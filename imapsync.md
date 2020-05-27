**Goal**: Sync mails from server1 to server2
* sync as the user
```
imapsync \
     --host1 test1.lamiral.info --user1 test1 --password1 secret1 \
     --host2 test2.lamiral.info --user2 test2 --password2 secret2
```

* sync on behalf of the user as masteruser
```
imapsync \
     --host1 test1.lamiral.info --user1 test1*masterusername --password1 secret1 \
     --host2 test2.lamiral.info --user2 test2 --password2 secret2
```

* sync for one folder
```
imapsync \
     --folder Archive.2006.Sent \
     --host1 test1.lamiral.info --user1 test1 --password1 secret1 \
     --host2 test2.lamiral.info --user2 test2 --password2 secret2
```

* fix longlines in message
```
imapsync \
     --folder Archive.2006.Sent --pipemess "reformime -r7" \
     --host1 test1.lamiral.info --user1 test1 --password1 secret1 \
     --host2 test2.lamiral.info --user2 test2 --password2 secret2
```

# References
* [APPEND error - fix long lines](https://imapsync.lamiral.info/FAQ.d/FAQ.APPEND_errors.txt)
```
Err 1/11: - msg Archive.2006.Sent/810 {27848} could not append ( Subject:...], 
Date:["07-Aug-2006 14:45:24 -0400"], Size:[27848], Flags:[\Seen] ) 
to folder Archive/2006/Sent: socket closed while reading data from server (4x)
```
* [Set up master user for Dovecot](https://github.com/xinxiang/notes/blob/master/linux/dovecot_masteruser.md)
* [Set up Stunnel](https://github.com/xinxiang/notes/blob/master/stunnel.md)
