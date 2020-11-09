# 1 - POKT Node Setup

_**Video Tutorial**_

<a href="https://https://www.youtube.com/watch?v=S7YBdl6dF3E"><img src="http://img.youtube.com/vi/S7YBdl6dF3E/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00] Roger Brogan: Hello everybody. This is Roger Brogan. And today we're going to see how to set up a pocket node for the pocket network. I'm assuming if you're at this video, you've already understood what the project is and why you'd be interested in setting up a node. If you haven't come on out to this page and check it out, it's a really fantastic project.

[00:00:25] So let's get into some prerequisites before we, we dive right in and these are right off the documentation page. The documentation is really good on this project.  I'm assuming that you're going to have a basic knowledge of Linux for this tutorial. This will also work on Mac OX. You need to know a little bit about web architecture.

[00:00:46] You're going to need to have a static IP address and a domain name and an SSL cert, which we will go over getting those in this tutorial here. And ideally if you know, a little bit about networks and process managers [00:01:00] and reverse proxies, those will be handy as well, but not entirely necessary because we are going to be doing this step-by-step.

[00:01:08] Now some hardware requirements we typically need a couple of CPU's or virtual CPU's four gigs of Ram. They recommend 50 gigs, but they also note that this is blockchain is going to grow 154 gigs a year. So maybe something a little bit larger would be in line.

[00:01:24] Okay. So, the first thing is where do we get the hardware and the hardware that's going to have a static IP address or domain name? Well, a very popular service to do this is Amazon web services. And that's what we're going to use in this tutorial. But if you want it to use Azure or digital ocean or Google, they all have a virtual private servers or VPSs for short, or sometimes they're just referred to as virtual machines or VMs for short.

[00:01:52] You could use any of those. And a lot of these commands are just basic Linux commands. So, if you have access to a Linux box somewhere else, you [00:02:00] could do the same thing. All right. So, if you don't have an AWS account, you can set one up, create a free account. I'm going to go ahead and sign into my console.

[00:02:10] I've already signed up.

[00:02:15] Okay.

[00:02:18] What I'm going to do too, is jump over here to the EC2 dashboard. And I'm going to go over to the instances and I'm going to go ahead. And, this is an old one I had laying around. I'm going to go ahead and delete this one.

[00:02:47] We're going to create a new instance and we're going to use an instance that is an Ubuntu server. Okay. We're going to use [00:03:00] Ubuntu server, 20.04, LTS or long-term support. We're going to do a 64-bit version of this. So, let's go ahead and select it.

[00:03:09] Now there is a small, free tier available, but this is a really small instance. It doesn't really meet the basic requirements. So, I'm going to jump up to one that has the, two virtual CPU's, which were mentioned in the requirements and four gigs of Ram. And this one actually has support for higher network.

[00:03:29] So this is what I'm gonna do. This is a t3a.medium instance. So, I'm going to choose this one and I'm going to configure the instance. Most of the stuff is going to be all of the defaults here. So nothing really surprising. I am going to bump up the drive space though. Eight gigs is just not going to cut it.

[00:03:49] So we're gonna, crank it up to 80 gigs here.

[00:03:57] Okay. And if we had any tags we wanted to add, we could [00:04:00] do that. The next is the security group set up and we are going to open a couple of additional ports here.  the reason why we're going to do that is, pocket node requires a of ports to be open. So specifically, one is the pocket RPC port itself, and that is going to be a custom TCP rule.

[00:04:26] And this is going to be port 8081 and we'll have that accessible for anywhere. And the description for this. This is the pocket RPC or remote procedure call. And we also want to open the Tendermint peer to peer protocol port. So we're going to add one more rule.

[00:04:48] This is for Tendermint peer to peer. That's going to be accessible [00:05:00] from anywhere now that the SSH terminal I'm going to actually just say that this is available from my IP. This is going to disallow anyone else, but me from using SSH or secure shell to get into administer the desktop. That's just a little bit of a nice security feature.

[00:05:18] Tighten that SSH port up a bit. There. So, this is a review, our instance launch. It looks good to me. So we're going to go launch this instance and, you’re not going to have an existing key pair. This is a prior one. So, I'm going to go ahead and create a new one. And I'm going to call this pocket AWS keys, and I'm going to download this key pair.

[00:05:46] And this is going to be important to connect via SSH.

[00:05:50] In other words, this is a private and public key pair that will allow us to access the virtual private instance.

[00:05:56] And this is launching. So, let's go and take a look at [00:06:00] its status. Okay. It looks like it’s already booted up and running and we've got a public IP address. This is what we needed. One of the other requirements. So, this is the public IP address we're going to use.  and we're going to connect over to this and we're going to use an SSH client and is where it gives us a nice handy connection where we're going to take our SSH command. And we're going to tell it which key file to use. And we're going to give it this name here.

[00:06:36] I'm going to use a regular command prompt, and this is in my local directory. So, if we're going to use this command as is, we've got to make sure that we have that permission file in the right place. So, I'm going to copy it out of the downloads and I'm going to go put it over [00:07:00] here and users cyber let's go ahead and paste that.

[00:07:11] That way we can use this command exactly as it is. So, I'll just paste it in right there.   It's going to ask; do we want to really connect to this and then store the key for this? And it's, it's adding that to our known hosts and, voila. Now we are, secure shelled into our box . Okay.

[00:07:39] Now for the rest of the steps there's some very good documentation on this. But we also have a gentleman that, created a GitHub repo with some setup scripts that is gonna help us. And this is referenced off the material of the [00:08:00] documentation on the site here. So, we're going to use this GitHub repo.

[00:08:07] And we're going to go through the, the read me here, but we're not going to just blindly execute these scripts. They don't recommend that we are going to go through here and read these and I'll review the scripts as we execute them, because it just saves us a little typing. And this is looking at a fresh Ubuntu install with version 20.

[00:08:24] And we're going to go through here and create a new user to use the identity to run the pocket node. We're going to go through here and set up all of the dependencies. We're going to go out and get our SSL cert using something called let's encrypt.  This technique he goes through here is a one way to do it.

[00:08:43] I'm going to show you a way that I think is a little bit easier. So, we're going to vary our steps right there, and then we're going to continue to go in and configure our pocket configuration files. And then we're going to go ahead and create a pocket account and sync the node. And at that point we [00:09:00] should have a working node.

[00:09:01] We are going to run this on the Testnet at first and in later videos, we can see how to switch that over to the main net. So, let's jump right in it here. We can copy and paste these commands over. So, this is just going to go in and clone the repo. And then we're just going to CD into the directory, I just used a tab shortcut there.

[00:09:28] So we're now in the directory that has all of that. And we're going to do a ch mod command to change some of the permissions on the script. So that they're executable. Then we're going to go ahead and execute the make user command. Now I said, we weren't going to blindly execute scripts. So, let's take a look at what make users going to do.

[00:09:50] And just, as you might guess from the name, it's just going to create a new user and we're going to create one called node user. So, let's go ahead and make our new user [00:10:00] here. We're just going to call this node user.  If you get a permission denied, we're going to say sudo, make user no user.

[00:10:11] Pick a password, a nice strong password. Make sure you re-type that password and not really gonna fill out the rest of this stuff here. You can, if you wish. And we are right back at our prompt after creating our user.   You might also note here that the, the prompt has changed. We're no longer under our original user, which was Ubuntu we're now under the new user that we created.

[00:10:40] So. We need to go and clone the repo again because, that was cloned into the other user's directory. So, let's do that again.

[00:11:02] [00:11:00] And then we're going to CD into that directory, same tab completion, trick. And then we're going to run the dependency installer. So, let's go look at that script. See what it's going to do. This is going to do some pseudo app update and install the go language Nginx cert bot get. And another repo here to do some installs for the cert bot and, just dump out or starting a new shell to load up that.

[00:11:32] So that looks. Pretty safe, all the things we need to do. So, we'll go ahead and do that.

[00:11:45] It's asking us for the password, because it's going to elevate permissions here.

[00:13:14] [00:13:00] [00:12:00] Yes. Continue. Yes. Continue.

[00:14:03] [00:14:00] Okay, so now we're on to step three, creating an SSL cert. And these steps I'm sure will work, but you have to deploy a DNS text record.  if you're familiar with doing that, that's, that's an easy way to do it. But I like to use the Nginx, cert bot. So, I'm going to install that that's a pseudo app get installed Python three cert bot Nginx.

[00:14:27] So let's go ahead and install that.

[00:14:33] And while that is installing. We do need to get a domain name pointed at our instance.  if we go back and look over here, we have a public DNS record domain name, but this, Amazon, AWS, they own this domain name and they do not have an agreement with let's encrypt to issue certificates for that particular domain.

[00:14:58] So, what we are going [00:15:00] to do is use a different DNS provider. You could use any of your favorites. One that I use is just called free DNS, because it is a free DNS out at, uh, you know, free DNS dot, afraid.org.  you can sign up for free if you want. I'm just using a free account.  the trick I'm going to use here is just do a sub domain.

[00:15:21] I'm going to go ahead and add a new sub domain.  there's lots of different ones to choose from, but I like the us.to Just because it's really short. The name that you choose for your domain is not as important as the fact that it's available and you can get a cert for it.

[00:15:39] Now here's the IP address. From our instance, nine, seven double-check that's correct. We're just making up a name. I'm calling this PO T a P O C K. AWS for pocket. AWS. I'm going to go ahead and click save, got to put in the capture there, [00:16:00] which that's pretty nasty looking one. Not sure if I'll get it right on the correct.

[00:16:04] Do I'm here, LA, that was not correct. Let me try a different image. Okay. I think that is
[00:16:23] okay. Seem to like that. So now we have a domain name that is going to refer to our public IP address. And that's important now because we're going to use that with our little wizard here.

[00:16:39] So the one that I like to use is just going to be this command. We're just going to do sudo cert bot in Nginx.

[00:16:51] I think it's just Nginx got an extra Y in there.  this is the email address where they'll send us some stuff. So, [00:17:00] mine in there. We need to agree to their terms of service. And if we want to share address with the electronic frontier foundation, so let's enter our domain and the domain has to be the one that we just set up. So, P O C K AWS dot U S dot T O.

[00:17:29] And what this is doing is making a request out to let's encrypt and it's setting up a temporary HTTP server that is waiting for that to come back with a challenge now. What did we forget to do well? Yep. That's pretty good idea. Likely a firewall problem. We do have to have it responding on port 80.

[00:17:54] So I did forget one of those ports, but not to worry. We can go back over here [00:18:00] and go over to our networking tab
[00:18:06] and go to our interface here.

[00:18:15] go into our security group or have our port rules
[00:18:25] and let's edit the inbound rules because we did forget our regular old HTTP. So let's go ahead. And allow that from anywhere. Let's go ahead and save the rules.

[00:18:44] Can hop over here. Give this a shot again here.

[00:18:52] Sure. We get this right. Or it will fail also.

[00:19:05] [00:19:00] And that's what we want to see it set up the certificates and it's changed our configuration. We're not gonna have it modify Nginx to redirect all the traffic, because we're going to be changing that proxy file a little bit later. So, we'll just choose one.  the advantage of using this to also sets up a little, Cron job that this will run and automatically renew your certificate.

[00:19:30] So this is a pretty nice feature. All right. I thought that was a little simpler than going out and setting up the DNS record. Not that this is much more complicated, but a little bit faster too. Okay. So now we're going to get on to the install script. So, let's take a look at this one. This is the one that has.

[00:19:50] I think some of the most clever stuff in it here, this one is a little bit bigger. It's a little more space here and we're going in [00:20:00] and taking the domain. So, we're going to use the same domain that we used in the prior one. We can choose a test net or main net. Like I said, we're going to be setting up the, a test net, but this works for both.

[00:20:11] It's just got some decisions around that. Deciding which seeds to use. And if we're going to do version 5.0 or five one, we're going to stick with 5.0 For right now. And then it goes ahead and gets a pocket core from GitHub. Does an update, make sure that we have the lib essentials to go ahead and build this.

[00:20:32] And then it goes ahead and builds that we're actually building some more steps here and to the main go for pocket core. And then it's going to start either the main net or the Testnet, which creates the config Jason file, which is nice. then it goes down here and grabs the correct, Genesis file for whether we're in the main net or the test net.

[00:20:56] So that's also very handy. It's got a note to [00:21:00] add, create chains in there, I guess in a future version of this, I'm going to check to make sure we have the configuration file. Correct. And then we fix the configuration file with, some values that we need from our configuration, with our host name.

[00:21:13] Right. And then this sets our you limit, which is nice because if you don't have it set at least that high, you're going to have some, some issues with running out of files. Then we're going to go ahead and set up the Nginx configuration, making sure that it's running. This is populating that proxy config file, which is going to be basically something like this, except where we have the change.
[00:21:41] this.com is where let's encrypt actually put those certificates for you, the full chain and the private key, which is nice. And then it fixes that up right here by. Putting our domain into that placeholder that he had in there and then puts the [00:22:00] proxy config in the right place, stops and starts in genetics, and then says, we're done go to step five.

[00:22:07] So that's exactly what we want to do here.

[00:22:15] So we can do that.

[00:22:30] Let's make sure that we copy the files back into our directory here to make sure that. Has all the paths, correct. So, the domain name we used
[00:22:53] and we're going to do the test net. We're going to use five,
[00:23:03] [00:23:00] five, zero.

[00:24:42] [00:24:00] all right, we've got that going. Everything seems to be okay. Good. Quick little. Do a check here.
[00:24:58] config file is [00:25:00] okay. It seems to be happy. All right. So, the next one is create a pocket account. So, let's go ahead and do that. This is generating an account and what's a nice, long, but easy to remember passphrase.

[00:25:20] This is protect the private key. So we've got an account and really all we need to do there is a do pocket start and see if this thing is working here. So let's do pockets. Start to what we have.

[00:25:50] You'll occasionally see some red. It's not a big deal.

[00:25:59] Mostly [00:26:00] green. It's like everything is starting up.

[00:26:04] Yeah. And what I'm going to do is I'm going to do another command prompt here so that we can, you know, this has a lot of what's going on. It's now sinking with the blockchain, which is what we wanted it to do. And I'm going to hop back over here and get the command to connect over to our instance here.

[00:26:35] And we're going to be able to issue some commands here. Once we get connected again,
[00:26:43] to see how this thing is doing, and one is looking at the, uh, queering for the height.  So it helps if I log in as my node user.

[00:27:08] [00:27:00] Okay. So we can see that we've gotten all the way up to some block 28, 78, and we can see it as cranking away . So this is going to continue until it gets all the way to the current. Block. And so the pocket query height is a very handy command to take a look at what's going on. There's also another really handy command that I'll share with you guys.

[00:27:37] This is another curl command here, and this one is a, we'll just paste it in here. We're going to post some data here out to local hosts to 600, 605 seven, and look for the status. And that's going to give us the status of the node. That's from looking at it from [00:28:00] Tendermint. And we can verify a few things where on our test net, there it is catching up, right?

[00:28:08] It was on four, four, five, seven. This is our public address for our validator. That's our public key.

[00:28:37] And, it looks like we are synced here. So it looks like we're at index block five, three, seven, nine. We can take a look at this again; we can see it's answering the request and we can see now catching up as false. We are synced. We are in the block height and we have a pocket [00:29:00] node up and running on the Testnet.

[00:29:03] Now we still have a few things to do. If we want to turn this into a validator node, we can do that. We need to. Get some pocket and then we need to create a sticking transaction and then we need to link it to a chain. So we'll cover all of those topics in future videos. Thanks a lot, everyone.[00:29:31]
