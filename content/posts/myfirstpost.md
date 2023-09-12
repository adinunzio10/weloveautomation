---
title: "My Journey to using Hugo + Docker"
date: 2023-09-10T20:26:50Z
draft: false
---
# First item I am going to post about, is how much I struggled setting up this hugo installation. **100% User Error**

For anyone who actually reads this, one thing you will come to learn about me is I rush through things. Work, games, hobbies, anything I do I rush (unintentionally). Think Barry Allen from the flash, without the super powers. 

So of course, that meant me rushing setting this up, with the expectation it will be like a lot of my other docker projects. Setup a docker compose file, make configs, docker compose up, case closed.  I couldn't find any guides that were like this, and the docker compose files provided at docker hub were very.. bare.  After hours of fiddling around and saying "I give up!" I found a way to get this to work in a (probably not the intended way) I believe a unique (and likely less efficient) way to configure and run my hugo setup. I wanted to run it in Docker and kept having issues with themes and hugo new command. here are some of the things that helped me move along with it.

- Picking a docker image that worked for what I wanted. I ended up with the main hugo docker images  [Docker Hugo](https://hub.docker.com/r/klakegg/hugo) and using the 0.101.0-ext-ubuntu image. Not sure why I chose ubuntu, I figured if I was using the shell it would be more familiar. Despite not using it. 
- ~~Understanding that the server in hugo is mainly for dev purposes so i can test my site before I move it over to Caddy~~ Though you can also use it in production, see later comments. 
- My big starting point was picking a theme, at first a lot of the themes i chose, i just could not get to work.. Reading the config of the themes I think I just confused myself. I ended up finding and using the blowfish theme, which had my favorite guide that made setup easier. You can find it here [Blowfish](https://blowfish.page/docs/getting-started/)
- One of the issues I was running into was using the hugo new content command, and realizing that it doesn't have params like 'posts'  you need to create a folder called content and in that a folder labeled  posts. From there I can do hugo new content/posts/myfirstpost.md to get me to here!  
- Now this is where I think I did things a bit.. uniquely and probably not efficient lol. I was using the docker run commands found at klakegg's docker hub for hugo. Which I then setup Alias's for within bashrc. For example I did `alias hugo='docker run --name hugo --rm -it -v $(pwd):/src -u $(id -u):$(id -g) klakegg/hugo:0.101.0-ext-ubuntu'` so that i could run hugo as if it was installed on my machine but actually manipulating the docker container. 
- Then another alias `alias hugo-server='docker run --name hugo --rm -it -v $(pwd):/src -u $(id -u):$(id -g) -p 1313:1313 klakegg/hugo:0.101.0-ext-ubuntu server'` which allows me to run the hugo server
- Duplicate alias but to run the docker **detached** `alias hugo-serverd='docker run --name hugo -d --rm -it -v $(pwd):/src -u $(id -u):$(id -g) -p 1313:1313 klakegg/hugo:0.101.0-ext-ubuntu server'`
- These last 2 I setup on a different port using draft mode, so I could internally view my drafted posts before flipping the switch. `alias hugo-serverdraft='docker run --name hugo-draft --rm -it -v $(pwd):/src -u $(id -u):$(id -g) -p 1314:1314 klakegg/hugo:0.101.0-ext-ubuntu server -D -p 1314'` `alias hugo-serverdraftd='docker run --name hugo-draft -d --rm -it -v $(pwd):/src -u $(id -u):$(id -g) -p 1314:1314 klakegg/hugo:0.101.0-ext-ubuntu server -D -p 1314'`
- Now because I liked the way this worked, instead of moving things over to my caddy web directory, I just setup a reverse proxy in caddy for hugos server on port 1313. Which allowed me to access the live version at my domain (this websitue)

That's it!  I don't expect others to do it this way but hey if anyone is brave enough to try something I did, go for it. Don't blame me when it doesn't work lol but I can always try to help! 

Next up I need to setup **tags** so when I publish my new posts that are currently drafted, they can be sorted accordingly. 
