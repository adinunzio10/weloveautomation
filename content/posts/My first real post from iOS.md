---
title: "My first real post from iOS"
date: 2023-09-11
draft: false
---
# Posting from iOS
*Once again, is this the way it was supposed to be done? Who knows, but it's the way I figured out I wanted to do it (for now)*

To start, I needed a good markdown app for iPhone. As much as I love iPhone and iOS, I understand the limitations of the system.

For example, apps like obsidian, which are popular mark down / note taking apps, did not let me choose a folder to save my files. You can find more about this online but the way they are setup, they need the files to be in their own folder.

I looked into some other apps, which cost money, but offered a wide variety of cool features. I am still new to this so am not sure what features I really need in a markdown app, so I opted for a free alternative. I was (and still kind of am) considering silverbulletmd as it is a great FOSS Self Hosted markdown app. I haven't played around too much I will need to see about linking a subset of created pages to my hugo posts directory. 

For now I found [Pretext](https://apps.apple.com/us/app/pretext/id1347707000) which is a free app with no bells and whistles. It lets me choose a directory to save files in. So I mapped my server's content directory to my iPhone via internal IP. Then I just need to create a new markdown file in Pretext, make sure to fill in the Hugo headers (or as they call it, front matter) for title, time and draft.  As soon as I save the file it shows up on Hugo instantly. Awesome! Works pretty easily.

My next question is will **iOS Shortcuts** let me create posts and auto make the Hugo header. That would be cool. 

First idea is to check if Pretext supports iOS Shortcuts. Nope. Pretext doesn't support shortcuts.

# I figured it out!

I figured out how to do it!! Steps following:
1. I am still using the [Pretext](https://apps.apple.com/us/app/pretext/id1347707000) app for my markdown editing. 
2. Next I am using iOS shortcuts. Simple setup of prompting for blog title and appending that to a new file saved into a network share for where my content files save. 
3. So I just click the shortcut. Put in my title and it opens the file In Pretext. Just close and it's instantly available on my dev Hugo server. 

You can download my shortcut here to take a look [New Blog Post](https://www.icloud.com/shortcuts/e40c2597d6fa40008096c85f8e120c35)

I think hugo offers a front-end editing system that I may look into, but I think I should be okay for now using NVIM on my desktop and Pretext (or later maybe silverbullet) on my iPhone/iPad/MacBook Air

More to come! I still haven't looked into tags/cateogires yet.
