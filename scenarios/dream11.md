1.	user
		- id
	match
		- id
		- club1 (RCB)
		- club2 (CSK)
	user-team
		- user_id
		- match_id
		- player_id
	player
		- id
		- points
		- skill (e.g., batsman, baller...)
		- club
	match-player
		- id
		- match_id
		- player_id
		- club
		- score
	contest
		- id
		- match_id
		- entry_fee
		- slots
	user-contest
		- id
		- contest_id
		- user_id
	score
		- user_id
		- score
		- match_id

2.	create team:
		- POST: /users/{user_id}/matches/{match_id}/team
	add player:
		- POST: /users/{user_id}/teams/{team_id}/players/{player_id}
	delete player:
		- DELETE: 
	get contests:
		- GET: /matches/{m_id}/contests/{c_id}
	enter contest:
		- POST: /contests/{c_id}/user_id
	fetch leaderboards:
		- GET: /contests/{c_id}/leaderboard
	update points:
		- PUT: /matches/{m_id}/score
		  payload: {player_id: score,...}
	rewards:
		- GET: /users/{u_id}/contests/{c_id}/rewards

3.	Sharding based on:
		- user_id
		- contest_id
		- tournament_id
		- match_id -> this should be the shard key

	- can data for 1 user fit into 1 machine?
	- is the most common/frequest api hitting one data node? (in our case it will be leaderboard api)
		- in a leaderboard:
			- /contest/{contest_id}/leaderboard
		- for each match, we have to show available slots for each contest
		- user < contests < matches < tournaments
		- contest: different group formed by users for a given match

4.	TTL (cache) is basically your inherent bottleneck on consistency.
		- cache eviction using TTL: load balancer (usually key is like, GET: /user/{user_id}/matches), application server, clients, CDNs
		- update cache based on new info: global cache (liek, Redis), some db also cache query related infos

5.	leaderboard update:
		- update on each ball
		- 22 players
		- contests size: 10, 1K, 100K
		- DAU (daily active users): 5M
		- push/pull score for 100K users based on precomputed score of 22 players
		- SLA (service level agreement, e.g., 99% request served within 300ms) is important. having large varinace in the turn around time makes SLA unreliable.
		- push:	precompute
		  pull:	lazy calculation
		- use hybrid calculation for our usecase i.e., for small contests (like, 10, 1K), each player scores will be pulled by client and they will compute the leaderboard related scores on their own devices. and for larger contests (like, 100K), precompute leaderboard scores for all participants and push it to them.

6.
