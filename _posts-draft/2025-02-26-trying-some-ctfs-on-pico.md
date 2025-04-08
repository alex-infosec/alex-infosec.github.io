
# Trying some CTFs on PicoCTF

## Verify (easy)
ssh'ed into their pico challenge

the description is 
*Checksum: fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7 To decrypt the file once you've verified the hash, run `./decrypt.sh files/<file>.`*

* Checksums let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file.

You can create a SHA checksum of a file with `sha256sum <file> ` or all files in a directory with `sha256sum <directory>/*.`

this was the code that won it for me 
```bash
ctf-player@pico-chall$ sha256sum decrypt.sh 
6eb5ce37a3581f5fb6f8f432186dbb49855670a39008dd4602bc4722c0f84c4e  decrypt.sh
ctf-player@pico-chall$ find files/ -type f -exec sha256sum {} + | grep 'fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7'
fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7  files/87590c24
ctf-player@pico-chall$ decrypt.sh files/87590c24
picoCTF{trust_but_verify_87590c24}
ctf-player@pico-chall$ Connection to rhea.picoctf.net closed by remote host.
Connection to rhea.picoctf.net closed.
alex-infosec-picoctf@webshell:~$ 
```

