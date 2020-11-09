# 5 - Unstaking from the testnet

_**Video Tutorial**_

<a href="https://www.youtube.com/watch?v=0dZQjNdJWEk"><img src="http://img.youtube.com/vi/0dZQjNdJWEk/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00] Roger Brogan: Hello everyone. This is Roger Brogan.  In this video, we're going to see how to unstake a pocket node. In prior videos we saw how to set up a pocket node, turn it into a validator node - all on the Testnet.    create the staking transaction and just a quick review. Let's take a look at our node - I have an SSH. connection running here. So if we look at the balance, we can see, we got a little less than 5,000 pocket left. That's accurate because the Testnet faucet gave us a 20 and we staked with about 15. So if we look at our node, we can say, this is our address. We've got our public key setup.

[00:00:48] This is the service URL to our node status too. And that is the tokens that we have staked. So status two means that we are staked [00:01:00] and we are not jailed. So we're running on the net. And if we take a look at, take a look at our status here as well, we can see some more information. Once again, we're on our Testnet.

[00:01:13] We can see that we have voting power. 15,001, right? So we are actually staked. We are sinked. We are not, catching up. We are on block six, two, two, zero. Okay. So we are successfully, staked to the test net. So if we want to, to unstake ourselves, which unstacking is going to - remove the stake to the node and then return it back to your wallet and take you off the network as a validator you might want to do this, if you're going to, you know, on stake and maybe restate some other claims somewhere else.

[00:01:51] So let's take a look at the unstake command. The unstake command is really pretty simple. We're just gonna issue [00:02:00] pocket , nodes unsteak and we're going to use the, public address of our node.

[00:02:10] Oh, a couple of arguments I forgot. Right. So we need to tell it on which net we're unstaking from. So we're unstaking from the Testnet and we have to give it a fee and micro pocket.  It's asking for your password , because it's going to be signing this transaction with your private key. So you need to unlock that and, success equal true is what we're after there. Okay. So, and there's the transaction for unstacking transaction. Now, if we look at, the node right now, we're not going to see any change immediately on the Testnet it takes, I believe an hour at current configuration to unstake. So we're going to have to wait a little bit and let me take a look at, let's just go ahead and query our note [00:03:00] again, too. And we can see that  we're still staked to our  (check spelling) rank B test net. So what we're going to do is just pause the video right here and wait for an hour and then come back and look at these commands and look at the balance and see if we are successfully unstaked from Testnet.

[00:03:18] Okay. So it's been a little over an hour, so let's go ahead and check our node and see how the unstacking status is going.

[00:03:26] Taking a look at queering, the node here, we can see our status is back to one. We are no longer staked. It also gives us a timestamp of when we were unstated. You might've noticed before that that was just this,  one, one, one date.  now this is the actual unstacking date. And if we want to take a look at our status, We can see that our voting power is now zero because we're no longer a validator. We are successfully off the net.

[00:03:54] That's all there is.