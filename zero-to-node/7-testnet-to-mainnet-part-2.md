# 7 - Testnet to the mainnet - Part 2

_**Video Tutorial**_

<a href="https://www.youtube.com/watch?v=s57wbed8d6M"><img src="http://img.youtube.com/vi/s57wbed8d6M/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00] Okay. We can see that we've got an issue with a note. At this point, we can see the error message here is that it can't connect to any seeds. The reason why it can't connect to any seeds is because there's one other file that we need to modify when we're switching over from the Testnet over to the main net.

[00:00:23] let me hop over and show that and modify it. Okay, so we need to go into the config.json, and the reason why it's not finding any seeds is because we still have the old Testnet seeds in this line , so what we need to do is go down and just get rid of the, the Testnet seeds and put in the main net seeds, and then it should find some seeds and then it should be able to start syncing with the network.

[00:00:52] So over node resources, make sure we go over to the main net dispatcher and seed list. And let's grab a [00:01:00] couple of these and we'll put them in there, put a comment there and I'll grab another one and throw it in there. And you could, you could add all of them if you want, but we'll just start with a couple and see how that goes.

[00:01:20] All right, let's go over here and I'll start it up again here.

[00:01:31] And this is what we want to see. We want to see it grabbing some peers, and if we can take a look at our status and see what's going on. Okay. We are now on the main net. We are still catching up we're at block four, one 18 block five 30 catching up. All right. So let's, give this a little bit to catch up.

[00:01:58] And, as soon as it [00:02:00] gets sinked, then we are fully switched over and synced up with the main net. The only thing we need to do to create a validator is to Import the wallet that has the pocket that we want to use for the staking transaction and execute the staking transaction. And that's it.  we did those things in prior videos setting up the test net.

[00:02:24] So feel free to refer to those. Thanks a lot.

