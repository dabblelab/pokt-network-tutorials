# 6 - Testnet to the mainnet - Part 1

_**Video Tutorial**_

<a href="https://www.youtube.com/watch?v=0Z9N-Vc3_rk"><img src="http://img.youtube.com/vi/0Z9N-Vc3_rk/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00]Roger Brogan:  hello everyone. This is Roger Brogan. And today we're going to make a video on how to switch over from a pocket note, running on the Testnet over to the main net. In some prior videos, we went through the entire process of setting up. The node, turning it into a validator, creating the sticking transaction and even unstacking the node.

[00:00:26] So today we're going to see what it takes to switch over to the main net. We've done all of our testing on the test net, and now we want this to go live on main net. So let's talk about how to do that. I've got some SSH  terminals open into the node. So I'm going to hop over to the first one here while I've executed.

[00:00:42] Pocket's start. And I'm going to shut that down. I'm also gonna go over here and issue a pocket reset command. And if  you're curious about what that actually does, if we go back over here to our node resources and go down to the CLI reference, [00:01:00] we can see that a pocket reset is going to go in here and get rid of pocket data.

[00:01:04] It's going to delete these other, files and folders and get us ready for the reset. Now the other thing that we are going to have to do though, is change the Genesis, JSON file, which is one of the things that's different between the nodes. So if we look at configuring the node and we'd go over to the link for the Genesis file, we can see that there are two different ones for main net and for test net. so if we want to take a look at this, so it's in the pocket folder here and then config Genesis Jason. We can see that the chain ID up the very top is going to tell us, which net that we're on. So I'm going to grab this command right here. And this is going to replace.

[00:01:50] Our JSON,  Genesis file. Okay. So let's just double check this and make sure that we are, the correct one. it looks [00:02:00] like, Oh, make sure you're in the correct directory first, right? Because what I did is I just copied the new one into, The main home directory .

[00:02:08] So let's go ahead and remove this. It's not in the right place and let's go into config directory here. Take a look. Yes, this is the Genesis  JSON. So let's go ahead and execute that command again, and then we can see that we are now in fact  operating on the main net.

[00:02:34] so that's what we want to do. Go ahead and exit out of that. Go back to our home directory. And then over here, let's go ahead and start.

[00:02:51]So let's take a look at the configuration . And we have a couple of different accounts and let's see what we're set up as a validator .

[00:02:58] Okay. So just [00:03:00] starting, it's going to give you a random address. Let's go ahead and set the validator.

[00:03:10] Set the validator address to the one that we're going to control . So let's use this first one.

[00:03:30] Yeah, get her validate validator. Now make sure that that's set. Now, if we had a, uh, account that we were using that already has pocket in it, other than one of  these other ones, then we could, use the commands to import that account so that we could use that one because over on the main net we're going to require real actual pocket tokens in order to create the staking transaction.

[00:03:55] So

[00:04:01] [00:04:00] looks like a, this guy's still working on it. Let's take a look at the status of our node here.

[00:04:19]So let's query art node. Okay. we're not actually set up as a validator on this chain yet. So let's take a look at the notes status here using a different command will curl to the local host. We are on our main name, that, and we are still catching up and we are. On block zero. So it looks like we've got some issues catching up  this is going to take some time. So we'll come back to this. Once 

[00:05:00] we've got this actually synced up with the main net.
