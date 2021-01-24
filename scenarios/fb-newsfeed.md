- requirement gathering:
	1. text/multimedia (photo/vids) -> both
	2. likes/comments visibility (# of likes)
	3. auto refresh feed
	4. feed ranking
	5. # of posts in feed
	6. > 1 month old, doesn't need to be into the news feed
	7. locale? -> rendering
	8. auto refresh newsfeed

- distributed db models:
	1. user: profile
	2. user: timeline (all posts by me)
	3. news feed: give me post by my friends in last 1 month

- sharding:
	1. user info: all user data for a single user should reside on a single machine (ideally)
	2. router: based on user_id, consistent hashing
	3. storage as a form of caching (for fetching posts for user). Delete all data older than 30 days (run cron job, and recreate indexing).

- auto refresh newsfeed:
	1. delta sync (every 5s/10s/15s/etc.): timestamp diff.
	2. append new posts to existing newfeed (based on delta sync) 

