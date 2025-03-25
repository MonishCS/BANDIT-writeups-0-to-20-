*INTRODUCTION:

   -> Bandit is a beginner-friendly wargame by OverTheWire, designed to teach basic Linux commands, file manipulation, and cybersecurity concepts. It provides a series of challenges (levels) where players must find hidden passwords using terminal commands.

  Who is it for?

      1.Beginners in cybersecurity – No prior knowledge required.
      2.Aspiring ethical hackers & penetration testers – Learn basic hacking techniques.
      3.Developers & system administrators – Improve Linux command-line skills.
      4.Anyone interested in CTFs – Helps in Capture The Flag (CTF) competitions.
      
   -> It is a beginner-friendly Linux and security challenge.
   
   -> link to the game: https://overthewire.org/wargames/bandit/.

 *LEVEL 0:
 
   -> OBJECTIVE:

      The goal os this level requires you to log into the game using SSH with the provided hostname, port, username, and password. Once logged in, you need to navigate to 
      the Level 1 page for further instructions.
      
   -> USED COMMANDS:
        
      # ssh bandit0@bandit.labs.overthewire.org -p 2220

*LEVEL 0 TO 1 :

   -> OBJECTIVE:

      The goal os this level requires you to find the password for the next level in a file named readme located in the home directory. Use this password to log into bandit1 
      via SSH on port 2220 and continue the game.

   -> USED COMMANDS:

      # ssh bandit0@bandit.labs.overthewire.org -p 2220

      #ls
      #cat readme


   -> FLAG / PASSWORD FOR BANDIT 1 :
           
      ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

*LEVEL 1 TO 2:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a file named "-" located in the home directory. You will need to use special handling to read this 
      file due to its name.
      
   -> USED COMMANDS:

      # ssh bandit1@bandit.labs.overthewire.org -p 2220

      # ls
      # cat ~/-

      
   -> FLAG / PASSWORD FOR BANDIT 2 :

      263JGJPfgU6LtdEvgfWU1XP5yac29mFx

*LEVEL 2 TO 3:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a file named "spaces in this filename" located in the home directory. You will need to handle spaces 
      in the filename properly when accessing the file.
   
   -> USED COMMANDS:

      # ssh bandit2@bandit.labs.overthewire.org -p 2220

      # ls
      # cat "space in this filename"

      
   -> FLAG / PASSWORD FOR BANDIT 3 :

      MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

*LEVEL 3 TO 4:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a hidden file located 
      in the inhere directory. You may need to use commands that list hidden files to locate 
      it.
      
   -> USED COMMANDS:

      # ssh bandit3@bandit.labs.overthewire.org -p 2220

      # ls
      # cd inhere
      # ls -ahl
      # cat ...Hiding-From-You

      
   -> FLAG / PASSWORD FOR BANDIT 4 :

      2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

*LEVEL 4 TO 5:

   -> OBJECTIVE:

       The level requires you to find the password for the next level in the only human- 
       readable file located in the inhere directory. You may need to use a command that 
       identifies file types to filter out non-human-readable files.
       
   -> USED COMMANDS:

      # ssh bandit4@bandit.labs.overthewire.org -p 2220

      # ls
      # cd inhere/
      # ls -ahl
      # file ./-file0*
      # cat ./-file07

      
   -> FLAG / PASSWORD FOR BANDIT 5 : 
       
      4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

*LEVEL 5 TO 6:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a file located 
      somewhere under the inhere directory that meets the following criteria:

      Human-readable
      1033 bytes in size
      Not executable

      You may need to use the find command with size and permission filters to locate the 
      correct file.
   
   -> USED COMMANDS:

      # ssh bandit5@bandit/labs.overthewire.org -p 2220

      # ls
      # cd inhere/
      # ls
      # find / -type f -size 1033c ! -executable 
      # cat maybehere07/.file2
   
   -> FLAG / PASSWORD FOR BANDIT 6 :

      HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

*LEVEL 6 TO 7:

   -> OBJECTIVE:
      
      Find the password for the next level by locating a file on the server that meets the following criteria.
   
   -> USED COMMANDS:

      # ssh bandit6@bandit.labs.overthewire.org -p 2220

      # ls -ahl
      # find / -group bandit6 -user bandit7 -size33c
      # cat /var/lib/dpkg/info/bandit7.password
   
   -> FLAG / PASSWORD FOR BANDIT 7 :

      morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

*LEVEL 7 TO 8:
   
   -> OBJECTIVE:

      Extract the password for the next level from the file data.txt, specifically from the 
      line containing the word "millionth".
   
   -> USED COMMANDS:

      # ssh bandit7@bandit.labs.overthewire.org -p 2220

      # ls
      # cat data.txt | grep "millionth"
   
   -> FLAG / PASSWORD FOR BANDIT 8 :

      dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

*LEVEL 8 TO 9:

   -> OBJECTIVE:

      Find the unique password stored in data.txt, which appears only once in the file.
   
   -> USED COMMANDS:

      # ssh bandit8@bandit.labs.overthewire.org -p 2220

      # ls
      # cat data.txt | sort | uniq -u
   
   -> FLAG / PASSWORD FOR BANDIT 9 :

      4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

*LEVEL 9 TO 10:

   -> OBJECTIVE:

      Extract the password from data.txt, which is one of the few human-readable strings and 
      is preceded by several = characters.
   
   -> USED COMMANDS:

      # ssh bandit9@bandit.labs.overthewire.org -p 2220

      # ls
      # strings data.txt | grep "=="

   
   -> FLAG / PASSWORD FOR BANDIT 10 :

      FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
      
*LEVEL 10 TO 11:

   -> OBJECTIVE:

      Decode the Base64-encoded password stored in data.txt and retrieve the password for the 
      next level.
   
   -> USED COMMANDS:

      # ssh bandit10@bandit.labs.overthewire.org -p 2220

      # ls
      # cat data.txt
      # cat data.txt | base64 -d
      # cat data.txt | base64 -d | awk '{print $4}'
   
   -> FLAG / PASSWORD FOR BANDIT 11 :

      dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

*LEVEL 11 TO 12:

   -> OBJECTIVE:

      Decode the ROT13-encoded password stored in data.txt and retrieve the password for the 
      next level.
   
   -> USED COMMANDS:

      # ssh bandit11@bandit.labs.overthewire.org -p 2220

      # ls
      # cat data.txt
      // by using cybershef do ROT13
      
   
   -> FLAG / PASSWORD FOR BANDIT 12 :

      7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
*LEVEL 12 TO 13:

   -> OBJECTIVE:

      Recover the password from data.txt, which is a hexdump of a repeatedly compressed file. 
      The goal is to reverse the hexdump and decompress the data step by step.
   
   -> USED COMMANDS:
   -> FLAG / PASSWORD FOR BANDIT 13 :

   
