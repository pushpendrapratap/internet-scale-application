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

3.	
