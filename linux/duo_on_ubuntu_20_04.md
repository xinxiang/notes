# Set up Duo MFA on Ubuntu

Enable MFA for selected users on Ubuntu 20.04.2 LTS with UTORMFA - https://uoft.me/mfa; powered by Duo.

## Install packages
```
sudo apt install libpam-duo
sudo apt install login-duo
```
## Adjust Configuration Files
### /etc/ssh/sshd_config
```
PubkeyAuthentication yes
PasswordAuthentication no
AuthenticationMethods publickey,keyboard-interactive

UsePAM yes
ChallengeResponseAuthentication yes
UseDNS no
```
*Note:*
* Commented out originals and put the 6 lines at the end of the file
* *UseDNS* was yes
* *ChallengeResponseAuthentication* was no
* *AuthenticationMethods* was added; comment it can disable MFA.

### /etc/security/pam_duo.conf
```
[duo]
host = ...
ikey =  ...
skey =  ...

gecos_username_pos = 2
gecos_delim = ,
groups = users,!visitor* 
```
*Note:*
* Request keys by filing a request at https://uoft.me/esc --> Get Help --> Information Security --> Multifactor Authentication
* *gecos* are used to mapping username with UTORid
* *groups* enable MFA for users in the users group, except those username starts with visitor

### /etc/passwd
Add *,UTORid* to the Comment field

```
username:x:uid:gid:Display Name,utorid:/home/username:/bin/bash
```

### /etc/pam.d/sshd
```
# Standard Un*x authentication.
#@include common-auth
...
auth  [success=1 default=ignore] /usr/lib/x86_64-linux-gnu/security/pam_duo.so
auth  requisite pam_deny.so
auth  required pam_permit.so
```
*Note:*
* Comment out *@include common-auth*; otherwise, password will also be asked before promoting for "Push" button.

## Enroll MFA

## Test MFA
* on server, after configuration files updated: service sshd restart
* on client
  * Test visitor1 -- should not requires MFA; authenticated with with public key
```
# ssh visitor1@myserver
visitor1@myserver:~$
```
  * Test before enrolling MFA
```
# ssh staff1@myserver
Please enroll at https://api-...duosecurity.com/portal?code=...&akey=...
staff1@myserver: Permission denied (keyboard-interactive)
```
*Note:* 
* MFA was configued to enforce, so no MFA, no access.
* Same message if no *geco* was set properly

  * Test after enrolling MFA
```
# ssh staff1@myserver
Duo two-factor login for staff1_UTORid

Enter a passcode or select one of the following options:

 1. Duo Push to XXX-XXX-1234

Passcode or option (1-1): 
```

## MFA and ansible
Server *myserver* is configured to use MFA for some users, and user *ansible* is excluded from using MFA. Run *ssh ansible@myserver* -- success; howerver failed. Disable MFA by commenting out the *AuthenticationMethods publickey,keyboard-interactive* line in sshd_config and ansible works.
```
# ansible -m ping all
myserver | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: ansible@mysever: Permission denied (keyboard-interactive).",
    "unreachable": true
}
```

## Reference
* https://duo.com/docs/duounix#pam-configuration
* https://duo.com/docs/duounix-faq
* https://blog.bitsrc.io/two-factor-authentication-for-ssh-ubuntu-660abb152db7
