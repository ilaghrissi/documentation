

### Generate ssh key

    ssh-keygen -t rsa

Example :

    PS C:\Users\imad\OneDrive\Bureau> ssh-keygen -t rsa
    Generating public/private rsa key pair.
    Enter file in which to save the key (C:\Users\imad/.ssh/id_rsa):
    C:\Users\imad/.ssh/id_rsa already exists.
    Overwrite (y/n)? y
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in C:\Users\imad/.ssh/id_rsa
    Your public key has been saved in C:\Users\imad/.ssh/id_rsa.pub
    The key fingerprint is:
    SHA256:JhgHrg45hqVbMhf66MT/fMrdfgdftqrNxr5obGnaqoeJbQzs imad@DESKTOP-PDAE2H1
    The key's randomart image is:
    +---[RSA 3072]----+
    |                 |
    |                 |
    |    . . .        |
    |   . = o         |
    |   .= + S        |
    |. .=.+           |
    |*+BE+            |
    |B&=B=...         |
    |^@*o=B+          |
    +----[SHA256]-----+

SSH key generate in C:\Users\imad/.ssh/id_rsa.pub, copy the content of this file and paste it on gitlab