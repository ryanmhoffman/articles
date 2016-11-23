# Pictionize Android Game  
The intent is to make an Android app that closely resembles the game Pictionary. The way it will be different from any other pictionary type game in the play store is that it will be cast to a tv screen with chromecast or roku.

It will give you a word on the phone that only the drawing play can see, once he starts it will go to the drawing screen which will be cast to the tv. The player will try to draw whatever the word was while the other players on his team try to guess. There will be a timer counting down in the top corner of the screen so that you only have 1 minute to guess. After the timer hits 0 it will stop you from drawing and you will have to click a button to say whether they got it right or wrong, then the word will be revealed on the screen.

The game-play will go back and forth between each team. It will keep score for you based on whether you say you got the answer right or wrong.  

## Main Menu  
I think I'm going to make it so that the "main" screen is displayed on the tv as well, so all players are involved from the start. It will have the splash screen, then a very simple screen on the phone that only lets you start a new game. Once you select start it will connect to the chromecast. That screen will let you pick team names, difficulty level, then start. When you start it will show the word to draw on the phone, and once the person drawing is ready they click a button to begin drawing. They have 1 minute to draw it (or as long as they want really) and players have to guess. Once they guess the drawer hits next and the word will be displayed on the tv screen. If they got it right select "right" and if you got it wrong select "wrong" and it will keep score for you. Then it will say "Team 2's turn pass the phone" and it will start all over again.

## Drawing Screen
TODO: Design the drawing screen, that includes on the phone and the display that is casted to the tv.  

## Extra Thoughts
The words will live in plain text files, 1 word per line. So I'll just need to read in one line at a time. I might add the option for user created words, but maybe not right away... Maybe add a share feature so you can share your drawing on social media and see if other people can guess what it is. That could be cool. The timer should be a progress bar along the bottom that moves along just like the bar that shows you how far you are through a song or video. I might make the bar just kinda for show, it won't actually stop you from drawing after a minute so the rules are enforced by the players, not the app.  
