# Infosec Institute Practical Web Hacking CTF- Level 12 solution #

*Hello everyone!*

I’m **Ch4r0n** and this is my solution for Level 12 of Practical Web Hacking CTF related to website pentesting organised by the Infosec Institute team. 
So, let’s get started.

Here's the [Problem URL](http://ctf.infosecinstitute.com/ctf2/exercises/ex12.php)

Okay, so when we open up the url we are greeted with a login page like this:

![Image of Problem URL](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/Level12_1.png)

I would've tried SQL first, but since it is mentioned that we should use **dictionary** attack, I tried that.
There are a lot of sites which offer awesome dictionary wordlists ( even Kali Linux has some, if you use that), 
but we will use the list mentioned in the hint:
http://www.openwall.com/passwords/wordlists/password-2011.lst

To brute force the login form, I used **Burpsuite**. You can configure it for your browser by following the instructions given [here.](https://support.portswigger.net/customer/portal/articles/1783066-configuring-firefox-to-work-with-burp)

Fire up Burpsuite and in the Proxy **Intercept** tab, ensure "Intercept is on".

![Image of Intruder tab](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/Level12_2.png)

In your browser enter username as **admin** (since it is already given in the problem page) and password as any arbitrary value in the login page and submit the request. 
The captured POST request can be viewed in the Proxy **Intercept** tab.
Right click on the request to bring up the context menu and click **Send to Intruder**.

![Image of context menu](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/122.png)

Go to the Intruder **Positions** tab.
Select the attack type as **Sniper**.
Clear the pre-set payload positions by using the **Clear** button on the right of the request editor.Add the "password" parameter value as position by selecting it and using the **Add** button. 

![Image of Positions tab](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/123.png)


Go to the **Payloads** tab. In the **Payload sets** settings, ensure "Payload set" is "1" and "Payload type" is set to "Simple list".
Upload the wordlist you downloaded using the **Load** option.

![Image of Payloads tab](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/125.png) ![Image of the start attack](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/124.jpg)

Click the **Start attack** button.
Wait for it to run and see the results in the **Results** tab.
If any of your attack is succcessful, you should see a difference in the **size of the response** sent by the site.
In this case, we find a different response size for the string "princess" and we can further verify by rendering the response by clicking on the **render** option. Thus the password is **princess**.

![Image of results](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/126.png)

Check if your password is correct by entering it in the form.
You should see something like this:

![Image of Solved](https://github.com/Th3Ch4r0n/CTF-writeups/blob/master/Level12_3.png)

*Hope you liked it. 
Feedback and suggestions are welcome.*
