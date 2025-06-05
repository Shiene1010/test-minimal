defaults:
#_posts
- scope:
	- path: ""
	- type: posts
- values:
	- layout: single
	- author_profile: true
	- read_time: true
	- comments: true
	- share: true
	- realted: true
- 
# Writing  Jekyll posts
	step1 start by placing pages into a _page
	step2 include ["_pages"] to _config.yml
	step3 assign peralink