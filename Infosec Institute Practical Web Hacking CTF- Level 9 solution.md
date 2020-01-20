# Infosec Institute Practical Web Hacking CTF- Level 9 solution #

*Hello everyone!*

I’m **Ch4r0n** and this is my first Infosec Writeup blog. In this writeup I am going to solve a CTF related to website pentesting organised by the Infosec Institute team. So, let’s get started.

Here's the [Problem URL](http://ctf.infosecinstitute.com/ctf2/exercises/ex9.php).

![Image of Problem URL](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/1.png)

Okay so when you visit the URL you get this page, it says that we are logged in as **John Doe** but we need to be logged in as **Mary Jane** and also in the bottom left we see the problem is about **Broken authentication and Session Management**.
So we get an idea that we need to look for **cookies** and **tokens** because they are most commonly used for session management in websites.

Firstly, we need a tool for viewing and editing cookies. I would be using the [EditThisCookie](https://chrome.google.com/webstore/detail/editthiscookie/fngmhnnpilhplaeedifhccceomclgfbg?hl=en) extension in Chrome because its quite user-friendly.
Okay so after getting the extension added we open it up by clicking on the cookie shaped icon on the top right and we see these cookies in the webpage.

![Image of EditThisCookie](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/2.png)

There are only two cookies- **user** and **PHPSESSID**. I chose to examine the **user** cookie for obvious reasons 😉.

Okay now under the value parameter we find the string: **Sk9ITitET0U%3D**, that has %3D at the end, which when url-decoded using an [online url-decoder](https://www.urldecoder.org/) gives us **=** at the end of the decoded string. This hints that it may be a **Base64** encoded string. I am going to try to decode that by opening up an online [Base64 decoder](https://www.base64decode.org/). We put the string under the Type parameter and press the decode button.

![Image of decoded text](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/6.png)

As you see, the decoded text is **John+Doe**, that is first name + surname of the user. So to get the solution we first need to base64 encode the string **MARY+JANE** and set it as the cookie. We visit an online [Base64 encoder](https://www.base64encode.org/), enter the string and click on encode. We get the base64 encoded result: **TUFSWStKQU5F**.

![Image of encoded text](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/4.png)

Now we copy the string and fire up our EditThisCookie extension. Then under the value parameter of the **user** cookie we paste this string after removing the previous value and to save the changes we click on the red tick at the bottom of the extension pop-up. Now we reload the page aaaand **Boom**!

![Image of congratulations message](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/5.png)

You see the info on Mary Jane and the congratulations message. You would be automatically redirected to level 10.

*Hope you enjoyed this write-up. Suggestions and criticism are welcome.*
