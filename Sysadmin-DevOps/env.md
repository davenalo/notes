Environment variables for user

```
env #print all
```
some important: SHELL, EDITOR, LANG, PATH

```
export VARIABLE=value
echo $VARIABLE
printenv VARIABLE
```

you can add it to the .bashrc; this way the varaible load everytime you open a terminal.

environment variables for all the users of the system:
```
sudo vim /etc/environment

#set the variable, save the changes

sudo source /etc/environment
```

you can use the command unset, for unset an environmetn variable.

