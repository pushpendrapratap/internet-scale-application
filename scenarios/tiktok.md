1.	Features:
	- post video
	- apply filter
	- recent posts (news feed)
	- like or comment on the post
	- 

2.	scale estimation:
	- storage
		- 1B user/day
	- throughput
		- 20GB data/day
		- 7TB data/year

3.	DB table:
	----------------------
	user:
		- id
		- name
		- dob
		- gender
	like:
		- user_id
		- entity_type
		- entity_id
	comment:
		- post_id
		- user_id
		- text
	post:
		- id
		- user_id
		- timestamp
	user_follower:
		- user_id
		- follower_id

4.	Pagination using:
		- keyset
		- limit/offset

	To get feed from all the users I'm following:
		- select p.* of user_id from user_follower uf join post p on p.user_id = uf.user_id where uf.follower_id = 100 order by p.created_at desc limit 50 offset 0;

5.	caching (for newsfeed/sharding):
		- to show newsfeed, need followers and their post
		- precompute newsfeed for every user in the system (cons: hot key/celebrity problem, e.g., show kohli post to all his followers!!!)
		- solution: cache only 2 weeks of data on one machine i.e., 14 * 20 GB can be easily stored on one machine
		- 

6.
