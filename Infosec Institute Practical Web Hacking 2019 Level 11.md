# Infosec Institute Practical Web Hacking CTF- Level 11 solution #

*Hello everyone!*

I’m **Ch4r0n** and this is my solution for Level 11 of Practical Web Hacking CTF related to website pentesting organised by the Infosec Institute team. 
So, let’s get started.

Here's the [Problem URL](http://ctf.infosecinstitute.com/ctf2/exercises/ex11.php)
And when you open it up you see this webpage.

![Image of site](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/111.png)

It says that we have been **blacklisted** and that knowing what websites typically use to identify their users - try to get rid of that ban.
It was a bit confusing at first and so I decided to take the hint. The hint said that we needed to look at the **cookies**, **IP addresses** and **user-agents** to remove the ban.
So I started with the cookies first.

We would be using the [EditThisCookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=en) extention in Chrome for this purpose. Fire up the extention by clicking at the cookie shaped icon on the top right and see which cookies are set up by the site.

![Image of editthiscookie](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/112.png)

We see that there are two cookies set up, one is the **PHPSESSID** and the other is **welcome**. Now in the **value** parameter of the **welcome** cookie we find that it has been set up as "no". So what would happen if we change the value to "yes"?
Click on the value parameter and delete the preset value and type "yes". Now save the value by clicking on the red tick at the bottom of the pop-up window.
Reload the page and *Voila!* You did it. Wait for getting redirected to the next level.

![Image of congratulations](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/113.png)

*Hope you enjoyed this write-up. Suggestions and criticism are welcome.*
