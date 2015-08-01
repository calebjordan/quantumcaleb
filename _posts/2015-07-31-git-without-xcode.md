---
layout: post
title: Installing Git without XCode
category: OSX
tag: OSX
---
# XCode Command Line tools without XCode

XCode is big and takes up tons of space on my wimpy 128GB SSD. However, you need the developer tools to install things like git with homebrew. To install the tools without installing the XCode Application, run

```
xcode-select install
```

and click 'Install' on the window that pops up. After installing, run 

```
sudo xcode-select -switch /
```

to update the developer path. You can now run `brew install git`, and begin forking and pulling at your pleasure. 