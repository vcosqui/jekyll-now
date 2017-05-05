---
layout: post
title: Multiple Java versions on OSX
---

As may of us (java developers) I have to support projects developed in the legacy 1.7 version 
of Java. It has been a pain for a long time for OSX users to keep two different Java versions.
Now thanks to [Brew](https://brew.sh/), [Cask](https://caskroom.github.io/) and 
[jEnv](http://www.jenv.be/) we have all the tools we had long time ago in Ubuntu 
with the awesome `update-alternatives` command.


For this we just have to install several Java versions and jEnv via Cask and Brew
```bash
~ brew cask install caskroom/versions/java7
~ brew cask install java
~ brew install jenv
```

Now we add the new JDK to jEnv and verify 
```bash
~ jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_25.jdk/Contents/Home
oracle64-1.8.0.25 added
1.8.0.25 added
1.8 added

~ jenv add /Library/Java/JavaVirtualMachines/jdk1.7.0_10.jdk/Contents/Home 
oracle64-1.7.0.10 added
1.7.0.10 added
1.7 added

~ jenv versions
* system (set by /usr/local/opt/jenv/version)
1.7
1.7.0.10
1.8
1.8.0.25
oracle64-1.7.0.10
oracle64-1.8.0.25
```

Now we can easily switch between java versions in the current shell
```bash
~ jenv shell 1.8 && java -version
java version "1.8.0_25"
Java(TM) SE Runtime Environment (build 1.8.0_25-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.25-b02, mixed mode)

~ jenv shell 1.7 && java -version
java version "1.7.0_10"
Java(TM) SE Runtime Environment (build 1.7.0_10-b18)
Java HotSpot(TM) 64-Bit Server VM (build 23.6-b04, mixed mode)
```

Or we can change it globally in the system
```bash
~ jenv global 1.8
```

Enjoy!
