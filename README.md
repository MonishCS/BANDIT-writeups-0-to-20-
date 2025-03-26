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

   -> SOLUTION:

     connect to do server, and the password is in the file readme.

   -> FLAG / PASSWORD FOR BANDIT 1 :
           
      ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

*LEVEL 1 TO 2:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a file named "-" located in the home directory. You will need to use special handling to read this 
      file due to its name.
      
   -> SOLUTION:

     bandit1@bandit:~$ cat ./-
     263JGJPfgU6LtdEvgfWU1XP5yac29mFx

   -> FLAG / PASSWORD FOR BANDIT 2 :

      263JGJPfgU6LtdEvgfWU1XP5yac29mFx

*LEVEL 2 TO 3:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a file named "spaces in this filename" located in the home directory. You will need to handle spaces 
      in the filename properly when accessing the file.
   
   -> SOLUTION:

      bandit2@bandit:~$ cat "spaces in this filename"
      MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
      
   -> FLAG / PASSWORD FOR BANDIT 3 :

      MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

*LEVEL 3 TO 4:

   -> OBJECTIVE:

      The level requires you to find the password for the next level in a hidden file located 
      in the inhere directory. You may need to use commands that list hidden files to locate 
      it.
      
   -> SOLUTION:

     bandit3@bandit:~/inhere$ cat ...Hiding-From-You
     2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

   -> FLAG / PASSWORD FOR BANDIT 4 :

      2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

*LEVEL 4 TO 5:

   -> OBJECTIVE:

       The level requires you to find the password for the next level in the only human- 
       readable file located in the inhere directory. You may need to use a command that 
       identifies file types to filter out non-human-readable files.
       
   -> SOLUTION:

     bandit4@bandit:~/inhere$ cat ./-file07
     4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

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
   
   -> SOLUTION:

      bandit5@bandit:~/inhere$ cat $(find . -type f -size 1033c)
      HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
   
   -> FLAG / PASSWORD FOR BANDIT 6 :

      HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

*LEVEL 6 TO 7:

   -> OBJECTIVE:
      
      Find the password for the next level by locating a file on the server that meets the following criteria.
   
   -> SOLUTION:

      bandit6@bandit:~$ ls -l $(find / -type f -size 33c 2> /dev/null) | grep "bandit7 * bandit6"
      ls: cannot access '/home/bandit2/spaces': No such file or directory
      ls: cannot access 'in': No such file or directory
      ls: cannot access 'this': No such file or directory
      ls: cannot access 'filename': No such file or directory
      -rw-r----- 1 bandit7     bandit6     33 Sep 19 07:08 /var/lib/dpkg/info/bandit7.password
      bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
      morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
      
   -> FLAG / PASSWORD FOR BANDIT 7 :

      morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

*LEVEL 7 TO 8:
   
   -> OBJECTIVE:

      Extract the password for the next level from the file data.txt, specifically from the 
      line containing the word "millionth".
   
   -> SOLUTION:

     bandit7@bandit:~$ cat data.txt | grep millionth
     millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
   
   -> FLAG / PASSWORD FOR BANDIT 8 :

      dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

*LEVEL 8 TO 9:

   -> OBJECTIVE:

      Find the unique password stored in data.txt, which appears only once in the file.
   
   -> SOLUTION:

      bandit8@bandit:~$ sort data.txt | uniq -u
      4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
   
   -> FLAG / PASSWORD FOR BANDIT 9 :

      4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

*LEVEL 9 TO 10:

   -> OBJECTIVE:

      Extract the password from data.txt, which is one of the few human-readable strings and 
      is preceded by several = characters.
   
   ->SOLUTION: 
   
      bandit9@bandit:~$ strings data.txt | grep ===*
      }========== the
      3JprD========== passwordi
      ~fDV3========== is
      D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
   
   -> FLAG / PASSWORD FOR BANDIT 10 :

      FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
      
*LEVEL 10 TO 11:

   -> OBJECTIVE:

      Decode the Base64-encoded password stored in data.txt and retrieve the password for the 
      next level.
   
   -> SOLUTION:

     bandit10@bandit:~$ base64 -d data.txt
     The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
   
   -> FLAG / PASSWORD FOR BANDIT 11 :

      dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

*LEVEL 11 TO 12:

   -> OBJECTIVE:

      Decode the ROT13-encoded password stored in data.txt and retrieve the password for the 
      next level.
   
   -> SOLUTION:

     bandit11@bandit:~$ cat data.txt | tr a-zA-Z n-za-mN-ZA-M
     The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
   
   -> FLAG / PASSWORD FOR BANDIT 12 :

      7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

*LEVEL 12 TO 13:

   -> OBJECTIVE:

      Recover the password from data.txt, which is a hexdump of a 
      repeatedly compressed file. 
      The goal is to reverse the hexdump and decompress the data step by 
      step.
   
   -> SOLUTION:

      bandit12@bandit:~$ cd $(mktemp -d)
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ cp ~/data.txt .
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data.txt
      data.txt: ASCII text
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ cat data.txt
      00000000: 1f8b 0808 dfcd eb66 0203 6461 7461 322e  .......f..data2.
      00000010: 6269 6e00 013e 02c1 fd42 5a68 3931 4159  bin..>...BZh91AY
      00000020: 2653 59ca 83b2 c100 0017 7fff dff3 f4a7  &SY.............
      00000030: fc9f fefe f2f3 cffe f5ff ffdd bf7e 5bfe  .............~[.
      00000040: faff dfbe 97aa 6fff f0de edf7 b001 3b56  ......o.......;V
      00000050: 0400 0034 d000 0000 0069 a1a1 a000 0343  ...4.....i.....C
      00000060: 4686 4341 a680 068d 1a69 a0d0 0068 d1a0  F.CA.....i...h..
      00000070: 1906 1193 0433 5193 d4c6 5103 4646 9a34  .....3Q...Q.FF.4
      00000080: 0000 d320 0680 0003 264d 0346 8683 d21a  ... ....&M.F....
      00000090: 0686 8064 3400 0189 a683 4fd5 0190 001e  ...d4.....O.....
      000000a0: 9034 d188 0343 0e9a 0c40 69a0 0626 4686  .4...C...@i..&F.
      000000b0: 8340 0310 d340 3469 a680 6800 0006 8d0d  .@...@4i..h.....
      000000c0: 0068 0608 0d1a 64d3 469a 1a68 c9a6 8030  .h....d.F..h...0
      000000d0: 9a68 6801 8101 3204 012a ca60 51e8 1cac  .hh...2..*.`Q...
      000000e0: 532f 0b84 d4d0 5db8 4e88 e127 2921 4c8e  S/....].N..')!L.
      000000f0: b8e6 084c e5db 0835 ff85 4ffc 115a 0d0c  ...L...5..O..Z..
      00000100: c33d 6714 0121 5762 5e0c dbf1 aef9 b6a7  .=g..!Wb^.......
      00000110: 23a6 1d7b 0e06 4214 01dd d539 af76 f0b4  #..{..B....9.v..
      00000120: a22f 744a b61f a393 3c06 4e98 376f dc23  ./tJ....<.N.7o.#
      00000130: 45b1 5f23 0d8f 640b 3534 de29 4195 a7c6  E._#..d.54.)A...
      00000140: de0c 744f d408 4a51 dad3 e208 189b 0823  ..tO..JQ.......#
      00000150: 9fcc 9c81 e58c 9461 9dae ce4a 4284 1706  .......a...JB...
      00000160: 61a3 7f7d 1336 8322 cd59 e2b5 9f51 8d99  a..}.6.".Y...Q..
      00000170: c300 2a9d dd30 68f4 f9f6 7db6 93ea ed9a  ..*..0h...}.....
      00000180: dd7c 891a 1221 0926 97ea 6e05 9522 91f1  .|...!.&..n.."..
      00000190: 7bd3 0ba4 4719 6f37 0c36 0f61 02ae dea9  {...G.o7.6.a....
      000001a0: b52f fc46 9792 3898 b953 36c4 c247 ceb1  ./.F..8..S6..G..
      000001b0: 8a53 379f 4831 52a3 41e9 fa26 9d6c 28f4  .S7.H1R.A..&.l(.
      000001c0: 24ea e394 651d cb5c a96c d505 d986 da22  $...e..\.l....."
      000001d0: 47f4 d58b 589d 567a 920b 858e a95c 63c1  G...X.Vz.....\c.
      000001e0: 2509 612c 5364 8e7d 2402 808e 9b60 02b4  %.a,Sd.}$....`..
      000001f0: 13c7 be0a 1ae3 1400 4796 4370 efc0 9b43  ........G.Cp...C
      00000200: a4cb 882a 4aae 4b81 abf7 1c14 67f7 8a34  ...*J.K.....g..4
      00000210: 0867 e5b6 1df6 b0e8 8023 6d1c 416a 28d0  .g.......#m.Aj(.
      00000220: c460 1604 bba3 2e52 297d 8788 4e30 e1f9  .`.....R)}..N0..
      00000230: 2646 8f5d 3062 2628 c94e 904b 6754 3891  &F.]0b&(.N.KgT8.
      00000240: 421f 4a9f 9feb 2ec9 83e2 c20f fc5d c914  B.J..........]..
      00000250: e142 432a 0ecb 0459 1b15 923e 0200 00    .BC*...Y...>...
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ xxd -r data.txt  > data.bin
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data.bin
      data.bin: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ mv data.bin data.bin.gz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ gunzip -d data.bin.gz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data.bin
      data.bin: bzip2 compressed data, block size = 900k
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ mv data.bin data.bin.bz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ bzip2 -d data.bin.bz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data.bin
      data.bin: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ mv data.bin data.bin.gz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ gunzip -d data.bin.gz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data.bin
      data.bin: POSIX tar archive (GNU)
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ mv data.bin data.bin.tar
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ tar -xf data.bin.tar
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ ls
      data5.bin  data.bin.tar  data.txt
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data5.bin
      data5.bin: POSIX tar archive (GNU)
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ tar -xf data5.bin
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ ls
      data5.bin  data6.bin  data.bin.tar  data.txt
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data6.bin
      data6.bin: bzip2 compressed data, block size = 900k
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ mv data6.bin data6.bin.bz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ bzip2 -d data6.bin.bz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data6.bin
      data6.bin: POSIX tar archive (GNU)
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ tar -xf data6.bin
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ ls
      data5.bin  data6.bin  data8.bin  data.bin.tar  data.txt
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data8.bin
      data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ mv data8.bin data8.bin.gz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ gunzip -d data8.bin.gz
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ file data8.bin
      data8.bin: ASCII text
      bandit12@bandit:/tmp/tmp.HpP2cGkNJ5$ cat data8.bin
      The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
      
   -> FLAG / PASSWORD FOR BANDIT 13 :

      FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

*LEVEL 13 TO 14:

   -> OBJECTIVE:

      You need to access the password stored in /etc/bandit_pass/bandit14, 
      which is only readable by user bandit14. However, instead of 
      receiving the password directly, you are provided with a private SSH 
      key to log into the next level. Useful commands include ssh, telnet, 
      nc, openssl, s_client, and nmap, and understanding SSH keys will be 
      helpful.
   
   -> SOLUTION:

      ssh -i sshkey.private bandit14@localhost -p 2220
      bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
      MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
   
   -> FLAG / PASSWORD FOR BANDIT 14 :

      MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

*LEVEL 14 TO 15:

   -> OBJECTIVE:

      The password for the next level can be retrieved by submitting the password of the current level to port, 30000 on localhost.
      
   -> SOLUTION:
   
     bandit14@bandit:~$ nc localhost 30000
     MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
     Correct!
     8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
   
   -> FLAG / PASSWORD FOR BANDIT 15 :

      8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
   

*LEVEL 15 TO 16:

   -> OBJECTIVE:

      To retrieve the password for the next level, submit the current level’s password to port 30001 on localhost using SSL/TLS encryption.
      If you encounter messages like "DONE", "RENEGOTIATING", or "KEYUPDATE", refer to the "CONNECTED COMMANDS" section in the manpage for troubleshooting. 
      You may need tools such as ssh, telnet, nc, ncat, socat, openssl s_client, nmap, netstat, or ss.
      For additional guidance, check resources like:
      Secure Socket Layer/Transport Layer Security on Wikipedia
      OpenSSL Cookbook – Testing with OpenSS
   
   -> SOLUTION:
   
     bandit15@bandit:~$ openssl s_client -port 30001 -quiet
     depth=0 CN = SnakeOil
     verify error:num=18:self-signed certificate
     verify return:1
     depth=0 CN = SnakeOil
     verify return:1
     8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
     Correct!
     kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
      
   -> FLAG / PASSWORD FOR BANDIT 16 :

      kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

*LEVEL 16 TO 17:

   -> OBJECTIVE:

      Scan ports 31000-32000 on localhost to find an active server, then identify which one uses SSL/TLS and provides the next level’s credentials. Use tools like nmap, 
      netstat, openssl s_client, and nc to complete the task.
   
   -> SOLUTION:

      bandit16@bandit:~$ nmap localhost -p 31000-32000
      Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-11-01 10:56 UTC
      Nmap scan report for localhost (127.0.0.1)
      Host is up (0.00011s latency).
      Not shown: 996 closed tcp ports (conn-refused)
      PORT      STATE SERVICE
      31046/tcp open  unknown
      31518/tcp open  unknown
      31691/tcp open  unknown
      31790/tcp open  unknown
      31960/tcp open  unknown

      Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
      bandit16@bandit:~$ openssl s_client -port 31790 -quiet
      depth=0 CN = SnakeOil
      verify error:num=18:self-signed certificate
      verify return:1
      depth=0 CN = SnakeOil
      verify return:1
      kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
      Correct!
      -----BEGIN RSA PRIVATE KEY-----
      MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
      imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
      Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
      DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
      JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
      x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
      KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
      J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
      d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
      YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
      vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
      +TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
      8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
      SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
      HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
      SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
      R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
      Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
      R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
      L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
      blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
      YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
      77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
      dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
      vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
      -----END RSA PRIVATE KEY-----


      bandit16@bandit:~$ cd $(mktemp -d)
      bandit16@bandit:/tmp/tmp.DuG8NNUTxO$ cat > private_key.pem
      -----BEGIN RSA PRIVATE KEY-----
      MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
      imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
      Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
      DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
      JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
      x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
      KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
      J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
      d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
      YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
      vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
      +TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
      8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
      SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
      HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
      SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
      R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
      Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
      R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
      L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
      blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
      YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
      77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
      dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
      vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
      -----END RSA PRIVATE KEY-----
      ^C
      bandit16@bandit:/tmp/tmp.DuG8NNUTxO$ chmod 600 private_key.pem
      bandit16@bandit:/tmp/tmp.DuG8NNUTxO$ ssh "bandit17@localhost" -p 2220 -i private_key.pem


      bandit17@bandit:~$ cat /etc/bandit_pass/bandit17
      EReVavePLFHtFlFsjn3hyzMlvSuSAcRD
   
   -> FLAG / PASSWORD FOR BANDIT 17 :

      EReVavePLFHtFlFsjn3hyzMlvSuSAcRD

*LEVEL 17 TO 18:

   -> OBJECTIVE:

      There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been 
      changed between passwords.old and passwords.new
   
   -> SOLUTION:

      bandit17@bandit:~$ diff passwords.new passwords.old
      42c42
      < x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO
      ---
      > ktfgBvpMzWKR5ENj26IbLGSblgUG9CzB
   
   -> FLAG / PASSWORD FOR BANDIT 18 :

      x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

*LEVEL 18 TO 19:

   -> OBJECTIVE:

      Avoid automatic logout by preventing .bashrc execution, then access the readme file in the home directory to retrieve the password. Use tools like ssh, ls, and cat to 
      complete the task.
   
   -> SOLUTION:

      moshe@myPC:~$ ssh bandit18@bandit.labs.overthewire.org -p 2220 cat ./readme
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

      bandit18@bandit.labs.overthewire.org's password:
      cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
   
   -> FLAG / PASSWORD FOR BANDIT 19 :

      cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

*LEVEL 19 TO 20:

   -> OBJECTIVE:

      Use the setuid binary in the home directory to escalate privileges and access the password stored in /etc/bandit_pass. Run the binary without arguments to get usage 
      instructions.
     
   -> SOLUTION: 

      bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
      0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
   
   -> FLAG / PASSWORD FOR BANDIT 20 :

      0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
