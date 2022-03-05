
ssh pair keys are storage in ~/.ssh, if I have not this directory/folder I can generate a new key.

```
/etc/ssh/sshd_config




```

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Genera una key ssh del tipo ed25519 con un COMENTARIO (-C) que es el email, pero podría ser cualquier cosa, y podría estar vacío

you can press enter to storage the key in the default directory, and you can also choose if you want an additional passphrase or not; you can leave the field empty pressing enter.

The next step is to run the ssh-agent in the "background"

```
eval "$(ssh-agent -s)"
```
But, WHYYYY?

```


ssh-agent outputs the environment variables you need to have to connect to it:

shadur@proteus:~$ ssh-agent
SSH_AUTH_SOCK=/tmp/ssh-492P67qzMeGA/agent.7948; export SSH_AUTH_SOCK;
SSH_AGENT_PID=7949; export SSH_AGENT_PID;
echo Agent pid 7949;
shadur@proteus:~$ 

By calling eval you immediately load those variables into your environment.

As to why ssh-agent can't do that itself... Note the word choice. Not "won't", "can't". In Unix, a process can only modify its own environment variables, and pass them on to children. It can not modify its parent process' environment because the system won't allow it. This is pretty basic security design.

You could get around the eval by using ssh-agent utility where utility is your login shell, your window manager or whatever other thing needs to have the SSH environment variables set. This is also mentioned in the manual.
```

[link](https://unix.stackexchange.com/questions/351725/why-eval-the-output-of-ssh-agent)

---

now we can add the key to the agent

```
ssh-add ~/.ssh/id_ed25519
```

-------------




```
ssh 192.168.56.101 - or - ssh testuser@10.0.0.55

or

ssh test.server.com - or - ssh username@hostname_or_ip
```
choosing a port
```
ssh test.server.com -p 3322
```
use SCP for copy files into a host
```
scp sample3 test@10.0.10.5:/home/test/Desktop

#use -P (uppercase?) for choose a port
```

```

```














