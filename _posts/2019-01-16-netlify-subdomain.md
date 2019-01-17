---
layout: post
title: "Adding a new subdomain on Netlify"
---
I hosted 2 sites with a custom domain on Netlify, it's been such a great experience, 
but I wanted to add a subdomain and sometimes, it just doesn't work. So here it is, the list.

Simply :

1. Make a new branch, we can call it `baru`
2. Change a bit of the content on the `baru` branch
3. Go to domain settings on the Netlify dashboard
4. Add the branch name manually to the branch subdomains box
5. Click trigger deploy
6. Change a bit of the content on the local and then push it to the `baru` branch
7. Wait for about 5-30 mins

I won't go into details, but this works. I searched the web for steps but most of them didn't work for me.

If you do know that's there's a better way than this, open an issue on the <a href="https://github.com/acp/djoernal/issues/new">`djoernal`</a> repository to help improve the content.
