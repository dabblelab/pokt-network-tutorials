# 4 - Full node to validator node

_**Video Tutorial**_

<a href="https://https://www.youtube.com/watch?v=raV7qfhmK6g"><img src="http://img.youtube.com/vi/raV7qfhmK6g/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00] Roger Brogan: Hello everyone. This is Roger Brogan. And today we're going to see how to turn our regular pocket node into a validator node. And some prior videos, we demonstrated how to get a pocket node up and running and sinking. With the blockchain. I have a SSH into this node right here that is up and running. And I'm looking at the log output here to make sure that everything is looking fine.

[00:00:30] So this is nice and sinked with our Testnet. We're going to do this on Testnet first and then switch over to the main net after we know that everything is working. Okay. And, a good command to just check things out is to curl to the local host on two six, six, five, seven slash status.  we'll take a peek at a few things in the response .

[00:00:50] Number one, we can verify that we are on our network test net. So we are in fact, on the test net, we can also verify the address [00:01:00] that we have for the validator, which we'll see how to actually set that up  in the beginning here. And we can see that catching up as false. So that means we are actually sinked to block height six.

[00:01:11] Zero four, four at the time of this recording. So the very first thing that we want to do is to create an account. When you first start with this node, there's not going to be any accounts created. An account is essentially going to be cryptic graphic private and public key pair. And that's, you know, the public part of that is going to be used as your identity for the node, essentially like your, your wallet or your account.

[00:01:36] So we're going to go ahead and create one. It's asking you for a passphrase here. So there's one that's nice and long, but easy to remember.

[00:01:47] And Wala we've now generated an account so we can take a look at the accounts that we have available. You can have multiple ones. Okay.

[00:02:03] [00:02:00] For example, I just created another one there. So let's take a look at. The ones that we have available now. And we now have three, I had a prior one from a prior example. So we're going to continue with the last one that I created here. So we're going to be using this as our validator account . And, if you're going to be changing configuration on your node, I think it's a good idea to go over to the other command that I started this with, and I'm going to do a control C.

[00:02:32] And I'm going to stop the Damon there. And then I'm going to hop back over to my other command window here, and we're going to change the validator address here. So if we look at pocket accounts and we get validator, It's going to tell us what the current validator address is, which this is one. And I had been using in some, some prior testing that I've been doing. So for this one, we're going to pretend like we're [00:03:00] setting this up fresh.

[00:03:02] So what we're going to do is use a similar command, but we're going to set the validator

[00:03:13]and we're going to set the validator using this public address. I'm just use. The screen here to just go ahead and copy and paste that exact address. And you have to use your passphrase to unlock the private key portion of this. And assuming that is you type all that incorrectly, we can see that our validator is now set to this address.

[00:03:38] So we're going to use this address as we continue on here. Okay. Now, We're going to go back over to our other window. And we're going to do the pocket start command and allow this to get sinking back with the test net. The next thing that we need to do is we need to create a [00:04:00] chains dot Jason file.

[00:04:02] Now the change dot Jason file specifies the other chains that you're going to be able to support. And for this testing, I have set up a rink B node, which is an ethernet  Testnet and if we go over and take a look at the supported networks here, we can see that the networks, that pocket support on their Testnet, there's a nice long list here.

[00:04:25]And if we go down to the ethernet section, we can see that for ethernet test nets, they do in fact, support a rink B. And the chain ID, which is the last column here. Zero zero two, two. That's important. When we set up our chains, Jason. Okay. And you also need to have access to either an Ethereum node.

[00:04:47] I happened to be running an Ethereum rink B node that I have access to, but you could use a gateway like infura, but ideally it's something that you're running yourself. All right. So this guy is running [00:05:00] again. We can do. Nice quick check to make sure that we're  sinked back up. And that is correct. We could also validate that our validator addresses is different here.

[00:05:12] And so we're going to go ahead and generate our chains, Jason, and we can use this command right here.

[00:05:25] Get copied over here correctly. There we go. Now, the first thing is the network says, enter the idea that network identifier. And if we look at all of these, we've got a net ID and network and a chains ID since we're generating the chains dot Jason, it's the chains ID that we're interested in, which for Rigby was zero zero two, two.

[00:05:51] And then now as the URL, the network identifier, now I told you I had a. Node running and I do. And just to verify [00:06:00] that it's up and running and the correct address, I will pull over little utility. I use here called postman, and we're going to take a look at the setup here. And this is the actual address that it's going to use.

[00:06:12] This is this very long string dynamic, DNS DAP node, and 32 seven seven zero port. So I'm just going to go ahead and grab that out of here.

[00:06:29] Yeah, we'll copy that. And it's H T T P

[00:06:35] go ahead and paste that in there. And if you want to add additional chains, all of these other chains are supported in the Testnet. You could add additional ones if you like, but we're just going to leave it with the one. Then it tells you a little bit output there. You can also take a look at what that generated for you, because this will actually live here in the pocket config directory 

[00:07:00] as the chains dot Jason file.

[00:07:02] And as we guessed correctly, or if we entered the data correctly, we've got the ID, correct. The URL. Correct. So that looks good. So we'll just exit out of there. And if we want to double check the command that I'm going to send over it, we have a simple  (change to Etherum) ether, net get balanced command. And this is a wallet that I have set up with some  (change to etherium) ether net in it.

[00:07:24] And if we send this over there, we're going to see that we do get the balance for that account. And just to prove that it's actually working, I'll change this to say an account that doesn't exist, that I know of. We'll send that over. We can see that we do in fact. Get a zero when I use my correct either not address, I get the balance that I have.

[00:07:47] Okay. So that's working correctly. That's good. And another thing that we can do to make sure that our note is configured correctly is to run the node in A [00:08:00] simulate relay node. Okay. And we'll, we'll go ahead and do that right now. And then we'll come back to funding the node here. What you need to do is shut it down with the control C here.

[00:08:11] And then when you run it, you add an additional flag here called simulate relay. And when you run it and simulate relay, it allows you to send a curl command that is going to essentially act like a relay, which means that if it got this command targeted at rink B, that it would forward that over to rank B and execute the command and get the results back.

[00:08:35] So in other words, what we should get, if we send it the same command is we should get the same result, but this time coming back from our node. So let's go ahead and do that. I've got the command that we want to use to execute that.

[00:08:58]And I'll go over this [00:09:00] command. It's it's kind of a long one here.

[00:09:05]okay. So I'll just go back to the beginning of this command. We'll go over each piece.

[00:09:12]Now first off, we're just going to curl a post request. And the data that we're going to send up in the post is Jason. So we have to send in the chain URL, which is the same URL that I used for the rink AB test node. And then we specify the payload, which has another data section here. Which is the Jason RPC version two.

[00:09:33] This is the command eith get balanced. The parameter is the actual,  either net wallet address that I used in the other one, chain ID one and method posts. And then the path is out to our local host, port eight Oh eight to slash V1 slash client slash SIM. And if we execute this. We should get the result back with the same balance here [00:10:00] that we did when we executed it directly against the node.

[00:10:05] And lo and behold, we get the same result as zero or the zero X one zero four three five one six and et cetera, et cetera. Okay. So what that means is that our pocket node can successfully access, uh, the other chain. So that means all of the networking and the ports and the configuration, all of that. And the network connectivity is set up correctly.

[00:10:31]Okay. So now we need to fund the validator node. If we become a validator node and we start doing work on the network and want to get compensated for that, we have to become a validator node. So the way that we have to do that is we have to stake some pockets. So we need to go get some pocket. And the way that we do that is via this Testnet faucet over here.

[00:10:53] Okay. So what I did is I just grabbed our public address and you've got to post the public address [00:11:00] in there and push the get Testnet pocket button here. And That was an old page, I guess there let's, that's a invalid  success. So let's invalid a result, not a success

[00:11:16]we want to see is something like this. Okay. So that's the actual transaction ID which I'm gonna copy for use later. We can take a look at this one.

[00:11:32]and so that granted   20,000 pocket from the Testnet over to our address. And then that means that we can go ahead and execute now the staking transaction to stake our note. Now let's look at some. Commands that we use to, to understand the status of our node. And we'll look at the differences between when it's staked and when it's not staked.

[00:12:00] [00:11:59] If we take a look at our actual node here, and I'm going to copy this address here so that we can reuse it. And some of our commands here, one of the ways we can take a look at this as we can just do pocket. Query the balance. And we can put in our address right now. It still says zero because these blocks happen every 15 minutes and it is not actually up with the fact that we do have a 20,000 pocket coming our way.

[00:12:37]We've got some other ways we can take a look at this as well. Let's take a look specifically at querying the node here. And we'll query the node.

[00:12:52] Okay. And it's telling us the validator is not found. Okay. So let's take a [00:13:00] look at the status here.

[00:13:06]We can see that we are catching up. This is our validator, but right now, We don't really, we're not a valid validator on the network. Okay. So in order to become a valid validator on the network, we need to actually create our staking transaction. Okay. Now, before we forget, we don't want to allow this to continue to run with simulate relay.

[00:13:28] So let's go ahead and, uh, do a control C and start this up again with just the command pocket starts so that we're not simulating a relay here. And then let's take a look at our status again here. Make sure that we're still caught up. Okay. Let's query our note again. It still doesn't consider us to be a valid validator on the network.

[00:13:59]All right. [00:14:00] So how do we become a valid validator? Well, what we're going to do is we're going to need to stakes and pocket here. So command to do that, there's going to be pocket we've set up. Our state command is the address. That's doing the funding and the rest of this, I'm gonna copy the rest of this command, but we're going to go over all the different pieces of this here.

[00:14:32]Okay. I had an extra carriage return in there that it didn't like. So let me go ahead and just type this out normally here. All right. So what we have here is the pocket state command, the address that we're coming from, what we're staking, we're going to be staking 15 thousand and [00:15:00] then one, two, three, four, five, six zeros at the end of that, because the denomination here is micro pockets.

[00:15:07] So we need to tack on six zeros for that. This is the chain that we're going to be validating against. So this is matching up to our chains dot Jason. This is the rink B Testnet and this is my DNS  name, HTTPS. For my pocket node, no, to support eight Oh 81, the test net is the net that we're going to transact that we're going to send this transaction to for staking.

[00:15:37] And our fee is going to be a 10,000  micro pocket or I've got, uh, Oh, I have in there it's like, yeah, 10,000 micro pocket. Go ahead and execute this command. [00:16:00]

[00:16:16]And I am missing pocket nodes. It's a nodes command here. So pocket nodes stake.

[00:16:25] It's asking you for your pass phrase because it's going to need to sign this with the private key. And this is what it looks like when it is not successful. Signature verification failed. the blocks happen every  15 minutes in pocket. So let's see where we're at here.

[00:16:59][00:17:00] We're at block six Oh four or five. All right. So we're going to have to wait a little bit of time here and we can wait until block six Oh four six and give this transaction another try. Or we can just keep trying it. We don't know exactly when the next block is ready.

[00:17:22] Exactly. But it's roughly about every 15 minutes. So we're going to hang out and wait, and we're going to try the sticking transaction again.

[00:17:36] Okay, let's give this shot again here.

[00:17:48] And success. This is what we wanted to see. Let's take a look at the output here. obviously this was a action to stake. A validator [00:18:00] and success is true. So this is what we wanted. This is also the transaction hash, which we could keep that if we want, we could. Examine that transaction as well.

[00:18:12]All right. So what are some other things that we can do to make sure that our. Validators working correctly. Let's take a look at our query height. We are on the next block.

[00:18:26]Let's take a look at our actual node here.

[00:18:35] So it looks like we just got our validator transaction in. So it looks like we're going to have to be waiting until, um, the next block to get some status on that. But let's use our other command. For status, just the local host status.

[00:18:58] We're still sinked [00:19:00] still on the test net. This is the correct validator. So we're going to give it until the the next block right here. And we're going to make sure that everything is actually running as it should here. When we take a look at our notes status.

[00:19:27]We should be able to take a look at our balance here. Let's look at, the balance for address here.

[00:19:39] okay. And we can see that it is now registering the 20,000 pocket that we originally got from the faucet here. So it hasn't actually subtracted the 15,000 out plus the the fee. So that should get taken out on the next [00:20:00] block here.

[00:20:03] Meantime, we, since we saved that transaction address, let's see if we can get a little information on the transaction here,

[00:20:18] command to do that is pocket query. Look for account transaction T access, and we're going to need that transaction,

[00:20:38] which we can grab right from up here as well as where I'd saved it before let's use that.

[00:20:49]let's try our account and this one. Okay. So none of the transactions are, are coming up yet. We're going to have to wait till 

[00:21:00] block.  Six Oh, four, seven. And we'll come back after that block posts.

[00:21:06]Okay. Let's take a look at what this looks like now with the next block here. First, we'll take a look at our balance and we can see that the balance has been deducted. Okay. Okay.

[00:21:25]Nothing on those transactions, but let's look at, uh, the status of our node here. Okay. Still looks good.

[00:21:38] Now let's look at the. Queer node here. Okay. So this is what we were hoping to see and to verify that we're actually on the chain here. So we are, this is our, our address, which is correct. We are on chain zero, zero two, two rank to be Testnet. This is our public [00:22:00] key. Our service URL is correct. And the status number two here.

[00:22:05] Is important. This is the fact that we are in status staking, and we have our stake tokens right there. And there you have it. That is going through setting up our note from just a regular sync node to setting up the validation. We have actually gone through this process here. We've set up the chains.

[00:22:30] We've created the account. We have, um, funded the node, created the staking transaction, and now we are all set. All right. We can see that we are in fact staked. Okay.

[00:22:45]And that's gonna wrap it up for this video. Thanks a lot.

