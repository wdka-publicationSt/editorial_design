#The HDSA Bot Family

This article exemplifies some of the chat bots created during the [[Code, text and text-to-speech|Code, text and text-to-speech]] workshop with Constant Association for Art and Media.

##Beuysbot
The Beuysbot created by [[Selby Gildemacher|Selby]] is dedicated to Joseph Beuys famous quote: "Every human being is an artist" and is linked to a database that live counts human beings who die and who are born. Accodingly the bot reports "xy Menschen sind Künstler" or "xy Menschen waren Künstler"

![Beuys speaks](Beuys-speaks.jpg)

##Facebot
The mouth bot made by Eurico is an animation that reacts to text appearing in the chatroom.

![Mouth closed](mouth-closed.png)
![Mouth half open](mouthopen-1.png)
![Mouth open](mouthopen-2.png)

##Fembot
Fembot created by Anja addresses her chatmates as female. She does that in a subtle and sympathetic way by using a bot's name (nick) and following up with a compliment. To not be perceived as a spam bot Fembot only reacts of another bot writes 2 words with 4 or more characters. 

This is the basic structure of the script that creates Fembot (check github repository or the wiki article for full script):

    infinite loop that takes the last message 
    of the chat
    take out blank line
    transformation of the message
    split the message in a list of words, 
    break on spaces between words
    find the nickname in the message and strip 
    of the colon
    loop that checks each word in the list, words 
    with 4 characters are saved in separate list
    check length of new list, if more than 2  
    -> send message
        if len(words_of_4) ># 2:
            sentence # "interesting " + nick 
            + " is a very wise woman."
            print sentence

##Haikubot
The Haikubot created by Juriaan looked for Haiku in the chatroom.

##Spybot
Spybot created by James spied on private chats, showing that the IRC channel is not as safe as one might expect.

##Swapbot
The Manifestos Bot/s or Swapbot created by Michaela uses Metaheaven Manifesto and Hackers Manifesto by McKenzie Wark as inputs. Each bot acts as an 
independent agent replacing keywords such as 'hacker/s ' with 'designer/s', 'designing' # 'hacking' etc. 
The aim of which is to blend them together questioning the notion of processes, approaches and roles that are often reversed. 


Example: 

<span style #"letter-spacing:0.5em;">
'''W  e        t  e  n  d         t o   <u>h a c k</u>  s o       t h a t      f o r m      a n d       c o n t e n t m a y      o b e y      d i f f e r e n t      r e g i m e s .''' </span>
<br>

<span style #"letter-spacing:-0.08em;">'''To the <u>designer</u> there is always a surplus of possibility expressed in what is actual, the surplus of the virtual.'''</span>


Michaela's wiki:   
   
[Visit Michaela's wiki for more information](http://92.51.132.110/~mlakova/wiki/index.php/Bot_irc_python)

###Transcriptionbot
The Transcriptionbot used Webkit's Speech2Text API to take spoken word input from Google's Chrome web-browser and post it via https (required for continued microphone input) to a Python webserver. The Python server then sent that text into the IRC chatroom. 


**More background about all bot scripts here:**   

[github.com/hackersanddesigners/HDSA2015](https://github.com/hackersanddesigners/HDSA2015)

