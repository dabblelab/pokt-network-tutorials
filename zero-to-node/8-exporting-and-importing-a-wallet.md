# 8 - Exporting and importing a wallet

_**Video Tutorial**_

<a href="https://www.youtube.com/watch?v=cTmakxNKTFk"><img src="http://img.youtube.com/vi/cTmakxNKTFk/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00]Hello everyone. This is Roger Rogan. And today we're going to talk a little bit about importing and exporting accounts out of a pocket node . So the reason you might want to do this, as you might want to move one of your accounts to different node, or you want to export out of one node and move it over to another note, or you, you want to manage some pocket that are in different wallets various reasons why you might want to do this.

[00:00:29] One of the ways that we can do this is to use the pocket accounts export command, which takes an optional path here. And what this does exports it as an armored private key. So it's encrypted. This is the recommended way to do that. You can actually export the raw address with the private address.

[00:00:47] That's not really recommended because of potential security issues. So we're going to create a new one to do an import and export . So if we look at a pocket [00:01:00] counts list, we've got three of them in here. So I'm going to go ahead and just create a new one. And this passphrase is important. This is what is used to protect your private key.

[00:01:12] So. Pick a nice long, strong one. That's easy to remember, but hard to guess from anyone that's trying to break in. All right. So let's operate or export on this one that begins with CB six. So we'll follow the same command here. We're just going to do, uh, our pocket counts export, and we'll pick the private key address .

[00:01:39] And you can do it out to a path if you want. But if you just take the default and you're going to need to enter your phrase to decrypt this.

[00:01:51] Now it's also gonna encrypt it with another password as well. So let's put the encrypt passphrase on here, how we're going to encrypt this. This is what you'll [00:02:00] use to decrypt it later when you're doing an import.

[00:02:08] And optional hint if you want. And there we go. So the export private key has been exported. You can see some information about it. This is the Jason format. And we could use this file. We could copy this file. This file is located right here at, since I didn't give an explicit name, it's going to be just pocket dash account and then the public portion of the key dot Jason.

[00:02:37]So what I'm going to do then is I'm going to remove that account because you can't import an account that already exist. So if we do,  could accounts delete.

[00:02:47]And, or your passphrase, then we can see that that account has been deleted. It's no longer in there. So now we can [00:03:00] practice the import. So we're going to do pocket accounts, import armored, because this is an armored one and we need to give it to the. Key file that we're going to import here. And so let's park at account.

[00:03:24] The one that we said with the CB. Okay. We'll go ahead and import that. And, or your passphrase to decrypt. Now it's going to be encrypted again, right? So we have another one of the encrypt pass here.

[00:03:48] And successfully imported. And if we take a look at our list  we could see that we do in fact, have our account back and ready to [00:04:00] use. That's it. Thank you very much.