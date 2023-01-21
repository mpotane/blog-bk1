# How to set up fish-shell in WSL 2

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

*<mark>Note: We cannot use the chsh (change shell command) because wsl is launch via bash.exe what we can do instead is start fish via bash. It's the only safe option just like how we do it in gentoo linux.</mark>*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672709711461/6b610f2b-09f8-4ef3-b10e-3d414355a624.gif align="center")

You can use any editor you want but in this example, we'll use nano.

[Nano cheatsheet -&gt;](https://www.nano-editor.org/dist/latest/cheatsheet.html)

copy this command at the end of the line.

```bash
# Use fish in place of bash.
# keep this line at the bottom of ~/.bashrc
[ -x /bin/fish ] && SHELL=/bin/fish exec fish
```

*<mark>Note: Restart your terminal and see if it works.</mark>*

![](https://media.giphy.com/media/3o6fJ1BM7R2EBRDnxK/giphy.gif align="center")

**Now we have fish as our default shell.**

---

> I previously stated that configuration is optional. Nonetheless, I will show you how to configure it so that we have a less-boring shell.

### How to inherit the system-wide environment variables on startup, from ***bash***?

Using the package ***bass*** we can solve just that. First, we need to install a plugin manager in fish called fisher from [git.io/fisher](http://git.io/fisher).

```bash
# This will install fisher plugin manager for us.
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
```

After installing we can now:

```bash
# this will update fisher as well as the plugins installed.
fisher update
```

Next, we will install bass from [https://github.com/edc/bass](https://github.com/edc/bass). To do this we just use fisher like this:

```bash
fisher install edc/bass
```

To use bass we can configure fish like so:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672712146403/6d61e6a4-e676-41f0-8094-84028089c12e.gif align="center")

🖊️ Copy the command in *<mark>.config/fish/config.fish</mark>*

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

👏 Excellent job!

***<mark>Note: Restart your terminal to make sure all changes take effect.</mark>***

![](https://media.giphy.com/media/DAtJCG1t3im1G/giphy.gif align="center")

Don't forget to follow 🌏 my socials and subscribe to my 💌 newsletter.