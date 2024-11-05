# README

Hello Interlake interns! I'm not accustomed to using GitHub (I know...it's funny for a CS major) but please be gentle with me...and if I accidentally left in anything compromising, do turn a blind eye. This is mainly to show you some changes that had to be made for LegSim to run properly. A lot of the changes also just happened...I did not do them manually. That's the magic of web apps I guess.  

## MISSING CREDENTIALS?

When you try to the run the app...you will have no credentials. This is because the `credentials.yml.enc` file does not exist anymore. When you run `rails credentials:edit` for the first time, it will generate a `credentials.yml.enc` and a `master.key` file for you. This is pretty simple Ruby on Rails stuff...you can look it up if you're curious. But short and sweet, your credentials file will be encrypted with the key from `master.key` so you'll need to run `rails credentials:edit` to actually edit your credentials. And yes, you need these. To run `rails credentials:edit` for the first time you need to comment out the two places where credentials are used first. In some environments you may also need to run it and specify an editor such as `EDITOR 'code --wait' /bin/rails credentials:edit` in order to open the credentials file in an editor. Once you have the credentials file open you can copy most of `credentials.yml.example` and set usernames and passwords for the gmail and database credentials (usernames and passwords) to `root`.

## NEED SYSTEM ACCESS?

I am unclear if my system login (and all my test logins, and all the student logins from last year) will still exist. Regardless, what you need to do:  
* Append `/system/` to the web link to access the system menu
* Give me the link to your LegSim and ask me to try logging in and adding you as a system user OR
* If my login doesn't work, use `SystemUser.create(email:"user@example.com", password:"ENTER_PASSWORD", password_confirmation: "ENTER_PASSWORD")` in the Rails console (obviously, filling in all necessary fields)

Fun fact: LegSim doesn't actually check if any of the emails in email columns are valid emails so you can literally use whatever you want, it doesn't have to be a valid email for the login to work. Make sure you record your login so you don't have to go searching the DBs every time.  

## HAVING OTHER ISSUES?

It's been a while since I worked on making changes to this. I've probably forgotten to put some things here and this document probably isn't accurate either. But last year I was in your shoes, new to LegSim's code and to Ruby. I'm just doing my best.  
That being said, PLEASE do not hesistate to reach out if you have any questions!!! Bother me before you bother Sean (please) and if I'm smart, I haven't told you how to contact Sean in case the mistake is something silly I did, and not something he left in the code.  

My personal details are:
* junyizhan@outlook.com
* (425) 351-3142
* parodac on Discord

I love receiving messages, so please don't wait if you have anything to tell/ask me. I still hold a lot of love for Interlake and LegSim. I'm also happy to set up a chat anytime, whether it's here at UW, over Zoom/Discord/Teams, or the very rare weekends I end up back in Bellevue.   

Good luck, interns!  

Acknowledgements (for fun and rainbows, and also because I can't think of anything else to write)
* University of Washington - for permission to use the code <3
* Professor John D. Wilkerson - the legend who is the origin of all things LegSim 
* Sean Bakker Kellogg - for answering all my silly questions about the code that I still don't understand
* Sophia Li - for understanding more about Docker than I ever will
* Ryan Rahlfs - for being a great Gov teacher and teaching me how to use this silly little website
* Michael O'Byrne - for signing my timesheets and giving me credit, even when they were two months late.
* You guys - for keeping the dream (and Interlake's post-exams Gov lesson plans) alive!


