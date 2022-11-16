关于一个shell，是否交互，是否login shell的问题。这个解释得好清楚：

https://unix.stackexchange.com/questions/38175/difference-between-login-shell-and-non-login-shell/522708#522708



A login shell is the first process that executes under your user ID when you log in for an interactive session. The login process tells the shell to behave as a login shell with a convention: passing argument 0, which is normally the name of the shell executable, with a `-` character prepended (e.g. `-bash` whereas it would normally be `bash`. Login shells typically read a file that does things like setting environment variables: `/etc/profile` and `~/.profile` for the traditional Bourne shell, `~/.bash_profile` additionally for bash†, `/etc/zprofile` and `~/.zprofile` for zsh†, `/etc/csh.login` and `~/.login` for csh, etc.

When you log in on a text console, or through SSH, or with `su -`, you get an **interactive login** shell. When you log in in graphical mode (on an [X display manager](http://en.wikipedia.org/wiki/X_display_manager_(program_type))), you don't get a login shell, instead you get a session manager or a window manager.

It's rare to run a **non-interactive login** shell, but some X settings do that when you log in with a display manager, so as to arrange to read the profile files. Other settings (this depends on the distribution and on the display manager) read `/etc/profile` and `~/.profile` explicitly, or don't read them. Another way to get a non-interactive login shell is to log in remotely with a command passed through standard input which is not a terminal, e.g. `ssh example.com <my-script-which-is-stored-locally` (as opposed to `ssh example.com my-script-which-is-on-the-remote-machine`, which runs a non-interactive, non-login shell).

When you start a shell in a terminal in an existing session (screen, X terminal, Emacs terminal buffer, a shell inside another, etc.), you get an **interactive, non-login** shell. That shell might read a shell configuration file (`~/.bashrc` for bash invoked as `bash`, `/etc/zshrc` and `~/.zshrc` for zsh, `/etc/csh.cshrc` and `~/.cshrc` for csh, the file indicated by the `ENV` variable for POSIX/XSI-compliant shells such as dash, ksh, and bash when invoked as `sh`, `$ENV` if set and `~/.mkshrc` for mksh, etc.).

When a shell runs a script or a command passed on its command line, it's a **non-interactive, non-login** shell. Such shells run all the time: it's very common that when a program calls another program, it really runs a tiny script in a shell to invoke that other program. Some shells read a startup file in this case (bash runs the file indicated by the `BASH_ENV` variable, zsh runs `/etc/zshenv` and `~/.zshenv`), but this is risky: the shell can be invoked in all sorts of contexts, and there's hardly anything you can do that might not break something.

-----------------------

24



I'll elaborate on the great answer by Gilles, combined with Timothy's method for checking login shell type.

If you like to see things for yourself, try the snippets and scenarios bellow.

**Checking whether shell is (non-)interactive**

```bash
if tty -s; then echo 'This is interactive shell.'; else echo 'This is non-interactive shell.'; fi
```

**Checking whether shell is (non-)login**

If output of `echo $0` starts with `-`, it's login shell (`echo $0` output example: `-bash`). Otherwise it's non-login shell (`echo $0` output example: `bash`).

```bash
if echo $0 | grep -e ^\- 2>&1>/dev/null; then echo "This is login shell."; else echo "This is non-login shell."; fi;
```

Let's combine the two above together to get both pieces of information at once:

```bash
THIS_SHELL_INTERACTIVE_TYPE='non-interactive'; 
THIS_SHELL_LOGIN_TYPE='non-login'; 
if tty -s; then THIS_SHELL_INTERACTIVE_TYPE='interactive'; fi; 
if echo $0 | grep -e ^\- 2>&1>/dev/null; then THIS_SHELL_LOGIN_TYPE='login'; fi;
echo "$THIS_SHELL_INTERACTIVE_TYPE/$THIS_SHELL_LOGIN_TYPE"
```

# Scenarios:

## Typical SSH session without special options

```bash
ssh ubuntu@34.247.105.87
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-1083-aws x86_64)

ubuntu@ip-172-31-0-70:~$ THIS_SHELL_INTERACTIVE_TYPE='non-interactive';
ubuntu@ip-172-31-0-70:~$ THIS_SHELL_LOGIN_TYPE='non-login';
ubuntu@ip-172-31-0-70:~$ if tty -s; then THIS_SHELL_INTERACTIVE_TYPE='interactive'; fi;
ubuntu@ip-172-31-0-70:~$ if echo $0 | grep -e ^\- 2>&1>/dev/null; then THIS_SHELL_LOGIN_TYPE='login'; fi;
ubuntu@ip-172-31-0-70:~$ echo "$THIS_SHELL_INTERACTIVE_TYPE/$THIS_SHELL_LOGIN_TYPE"

interactive/login
```

### Running script or executing explicitly via new shell

```bash
ubuntu@ip-172-31-0-70:~$  bash -c 'THIS_SHELL_INTERACTIVE_TYPE='non-interactive'; THIS_SHELL_LOGIN_TYPE='non-login'; if tty -s; then THIS_SHELL_INTERACTIVE_TYPE='interactive'; fi; if echo $0 | grep -e ^\- 2>&1>/dev/null; then THIS_SHELL_LOGIN_TYPE='login'; fi; 
echo "$THIS_SHELL_INTERACTIVE_TYPE/$THIS_SHELL_LOGIN_TYPE"'

interactive/non-login
```

### Running local script remotely

```bash
ssh ubuntu@34.247.105.87 < checkmy.sh
Pseudo-terminal will not be allocated because stdin is not a terminal.
Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-1083-aws x86_64)

non-interactive/login
```

### Running a command over ssh remotely

```bash
ssh ubuntu@34.247.105.87 'THIS_SHELL_INTERACTIVE_TYPE='non-interactive'; THIS_SHELL_LOGIN_TYPE='non-login'; if tty -s; then THIS_SHELL_INTERACTIVE_TYPE='interactive'; fi; if echo $0 | grep -e ^\- 2>&1>/dev/null; then THIS_SHELL_LOGIN_TYPE='login'; fi; echo "$THIS_SHELL_INTERACTIVE_TYPE/$THIS_SHELL_LOGIN_TYPE"'

non-interactive/non-login
```

### Running a command over ssh remotely with `-t` switch

You can explicitly request interactive shell when you want to run command remotely via ssh by using `-t` switch.

```bash
ssh ubuntu@34.247.105.87 -t 'THIS_SHELL_INTERACTIVE_TYPE='non-interactive'; THIS_SHELL_LOGIN_TYPE='non-login'; if tty -s; then THIS_SHELL_INTERACTIVE_TYPE='interactive'; fi; if echo $0 | grep -e ^\- 2>&1>/dev/null; then THIS_SHELL_LOGIN_TYPE='login'; fi; echo "$THIS_SHELL_INTERACTIVE_TYPE/$THIS_SHELL_LOGIN_TYPE"'

interactive/non-login
```

Note: On topic why running command remotely is not `login shell` more info [here](https://superuser.com/a/1224962/766900).