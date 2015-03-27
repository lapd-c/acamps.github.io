http://stackoverflow.com/questions/4565700/specify-private-ssh-key-to-use-when-executing-shell-command-with-or-without-ruby

config
#github for sp-albert-camps
Host github.com-sp
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa

#github for acamps
Host github.com-acamps
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_2

Host github.com-me
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_me
