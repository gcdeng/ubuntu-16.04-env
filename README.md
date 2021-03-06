# ubuntu-16.04-env

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get -y dist-upgrade
```

### git
```
sudo apt-get install git
git config --global user.name "gcdeng"
git config --global user.email ericdenggc@gmail.com
git config --global core.editor vim
```
- git has file permissions modes issue in case of share files between linux and windows via Samba  
solve it by following command:
```
git config core.filemode false
```  
ref: [How do I remove files saying “old mode 100755 new mode 100644” from unstaged changes in Git?](https://stackoverflow.com/questions/1257592/how-do-i-remove-files-saying-old-mode-100755-new-mode-100644-from-unstaged-cha)

### vim
```
sudo apt-get install vim
```

### oh-my-zsh
```
sudo apt-get install zsh -y
chsh -s $(which zsh)
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```
- Test that it worked with ```echo $SHELL```. Expected result: ```/bin/zsh``` or similar.
- change the theme by edit the ```~/.zshrc``` file and ```source ~/.zshrc```

### atom
```
sudo add-apt-repository ppa:webupd8team/atom
sudo apt update; sudo apt install atom
```
- To remove Atom text editor:
```
sudo apt remove --purge atom
```
- packages:
1. file icons
```
apm install file-icons
```
2. minimap
```
apm install minimap
```
3. linter-eslint
```
apm install linter-eslint
```
4. quokka
```
apm install atom-quokka
```
specify the path to the node executable in your global quokka config.json file, for example:
```
{
    "node": "/Users/username/.nvm/versions/node/v7.7.1/bin/node"
}
```  
On Mac/Linux:  
config.json in ~\.quokka  
On windows:  
config.json in C:\Users\XXX\.quokka  

5. indent-guide-improved
```
atom install indent-guide-improved
```

### nvm & node
- download
```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

- The script clones the nvm repository to ```~/.nvm```, and adds the source line to your profile  (```~/.zshrc```).  
``` 
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
```

- install nodejs lts version
```
nvm install --lts
```

### ESLint
```
npm install -g eslint
```

### MongoDB
- install:
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```
- Run MongoDB:  
The MongoDB instance stores its data files in <b>/var/lib/mongodb</b> and its log files in <b>/var/log/mongodb</b> by default, and runs using the mongodb user account. You can specify alternate log and data file directories in <b>/etc/mongod.conf</b>.  

- Start MongoDB:
```
sudo service mongod start
```
- Verify that MongoDB has started successfully:  
by checking the contents of the log file at <b>/var/log/mongodb/mongod.log</b> for a line reading
```
[initandlisten] waiting for connections on port 27017
```
- stop:
```
sudo service mongod stop
```
- restart:
```
sudo service mongod restart
```
- Begin using MongoDB:
```
mongo --host 127.0.0.1:27017
```

### 中文輸入法
[Ubuntu 16.0.4新增中文輸入法-新酷音輸入法](http://blog.xuite.net/yh96301/blog/342227672-Ubuntu+16.0.4%E6%96%B0%E5%A2%9E%E4%B8%AD%E6%96%87%E8%BC%B8%E5%85%A5%E6%B3%95-%E6%96%B0%E9%85%B7%E9%9F%B3%E8%BC%B8%E5%85%A5%E6%B3%95)

### Tmux
```
sudo apt-get install tmux
```
- reload:
This can be done either from within tmux, by pressing Ctrl+B and then : to bring up a command prompt, and typing:
```
:source-file ~/.tmux.conf
```
Or simply from a shell:
```
$ tmux source-file ~/.tmux.conf
```
- look sessions
```
$ tmux ls
```
- detach and attach session
```
$ ctrl+A d
$ tmux attach -t [session number]
```

### Samba
- Start
```
sudo service smbd start
```
- Stop
```
sudo service smbd stop
```
- Restart
```
sudo service smbd restart
```
- Status
```
service smbd status
```
