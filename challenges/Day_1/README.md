# Day_1
I'm given access to a webapp thats supposed to be a "youtube downloader", but the downloader is a bit sus...

## Solution
1. Follow the initial guide to input the link `https://www.youtube.com/watch?v=dQw4w9WgXcQ` on the website and download the contents.
2. Im given a zip, in that zip there is a `song.mp3` (not even the song I told it to download, but a real banger nonetheless) and a `somg.mp3` that's really a windows shortcut.
3. Using [LnkParse3](https://github.com/Matmaus/LnkParse3) I parse this link and extract a malicious command (saved in [malicious_command.txt](malicious_command.txt))
4. This malicious command in turn downloads a file (`.ps1`) from github that gets run
5. From this investigation I can answer questions 1 and 2, and if I look around a bit on the github profile that hosts the malicious powershell-script I can answer questions 3 and 4.


## Questions
1. ***Looks like the song.mp3 file is not what we expected! Run "exiftool song.mp3" in your terminal to find out the author of the song. Who is the author?:***
    **Answer:** `Tyler Ramsbey`

2. ***The malicious PowerShell script sends stolen info to a C2 server. What is the URL of this C2 server?***
    **Answer: ** `http://papash3ll.thm/data`

3. ***Who is M.M? Maybe his Github profile page would provide clues?***
    **Answer: ** `Mayor Malware`

4. ***What is the number of commits on the GitHub repo where the issue was raised?***
    **Answer: ** `1`
