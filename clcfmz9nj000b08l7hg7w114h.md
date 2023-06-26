---
title: "How to set up fish-shell in WSL 2"
seoTitle: "How to Setup Fish in WSL by Mark Edzel Potane"
seoDescription: "Learn how to set up Fish shell in WSL2: install, configure, and use Fish to enhance your command-line experience in Windows. #Fish #WSL2"
datePublished: Wed Feb 22 2023 12:37:40 GMT+0000 (Coordinated Universal Time)
cuid: clcfmz9nj000b08l7hg7w114h
slug: how-to-set-up-fish-shell-in-wsl-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1672631591915/0eea1f39-131c-458d-a8de-1e1632050b71.png
tags: linux, software-engineering, fishshell, wsl-2

---

### **Let's talk about why fish. Why not use zsh?**

* Smart and user-friendly
    
* powerful features such as syntax highlighting, autosuggestions, and tab completions that simply work out of the box.
    
* No need to learn works without configuration (beginner-friendly).
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672709850830/44ef185e-b2f5-487c-a7ab-921381cc49f3.png align="center")

First, we need to install fish using the command:

```bash
# This will install fish and its dependencies.
sudo apt install fish
```

Now we need to set fish-shell as our default shell.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682226142703/6410d720-2e2d-4476-87e6-25b4121cd88c.gif align="center")

copy this command at the end of the line.

```bash
# This will tell us the path of fish binary
# Copy it in the clipboard
which fish
```

```bash
# Use command sudo chsh -s <paste path of fish shell> <your username>
# Just like:
sudo chsh -s /usr/bin/fish username
```

*<mark>Note: Restart your terminal and see if it works.</mark>*

![](https://media.giphy.com/media/3o6fJ1BM7R2EBRDnxK/giphy.gif align="center")

**Now we have fish as our default shell.**

---

> I previously stated that configuration is optional. Nonetheless, I will show you how to configure it so that we have a less-boring shell.

### How to inherit the system-wide environment variables on startup, from ***bash***?

Using the package ***bass*** we can solve just that. First, we need to install a plugin manager in Fish called Fisher from [git.io/fisher](http://git.io/fisher).

```bash
# This will install fisher plugin manager for us.
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
```

After installing we can now:

```bash
# this will update fisher as well as the plugins installed.
fisher update
```

Next, we will install bass from [https://github.com/edc/bass](https://github.com/edc/bass). To do this we just use Fisher like this:

```bash
fisher install edc/bass
```

To use bass we can configure fish like so:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672712146403/6d61e6a4-e676-41f0-8094-84028089c12e.gif align="center")

🖊️ Copy the command in `.config/fish/config.fish`

```bash
# Inherit system-wide environment variables.
bass source /etc/profile
```

That completes the configuration.

*Other notable plugins we can use:*

```bash
# Autopair brackets & qoutes. 
fisher install jorgebucaran/autopair.fish
```

```bash
# Jump to folder easily.
fisher install jethrokuan/z
```

![](https://media.giphy.com/media/SVH9y2LQUVVCRcqD7o/giphy.gif align="center")

---

### How to style fish using the starship cross-shell prompt?

Finally, we have come to the last part of this tutorial.

> Have you noticed how attractive my shell is in comparison to yours? That's because I'm using a Starship preset. This will be quick, so follow me again.

To install it we use:

```bash
# This will install the latest package in your local bin directory. 
curl -sS https://starship.rs/install.sh | sh -s -- --bin-dir ~/.local/bin/
```

Next, we need to initialize it using our shell.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672713593742/ccf3a644-139a-4852-9b2f-b3f2509fe409.gif align="center")

```bash
# Add this to your fish config.
starship init fish | source
```

Setting up the preset from [https://starship.rs/presets/pastel-powerline.html](https://starship.rs/presets/pastel-powerline.html)

```bash
# Copy this command and we are good to go.
starship preset pastel-powerline > ~/.config/starship.toml
```

* Additional plugin for fisher
    

```bash
fisher install jorgebucaran/nvm.fish
```

👏 Excellent job!

***<mark>Note: Restart your terminal to make sure all changes take effect.</mark>***

![](https://media.giphy.com/media/DAtJCG1t3im1G/giphy.gif align="center")

Don't forget to follow 🌏 my socials and subscribe to my 💌 newsletter.