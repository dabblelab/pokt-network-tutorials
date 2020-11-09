# 3 - Setup an AWS Elastic IP

_**Video Tutorial**_

<a href="https://www.youtube.com/watch?v=ajEx7vtWhF0"><img src="http://img.youtube.com/vi/ajEx7vtWhF0/maxresdefault.jpg" alt="Tutorial Video" height="480" /></a>

_**Video Transcript**_

[00:00:00] Roger Brogan: Hello everyone. This is Roger Brogan. And in this video, we're going to talk a little bit about. Some of the public IP addresses and the way that they work in AWS. You might note that I have an instance here and I was using this instance in a prior video to set up a pocket network node.  I went ahead and I stopped this, but you might note when it stopped here that the public IP 4 address in the DNS is, is no longer available.

[00:00:32] And if I go ahead and I launched this. So go ahead and fire up this instance here. Actually, I want to launch this one. So let me go here and start the central instance . It's going to go ahead and be started

[00:00:46] and we can see it does, in fact, now have a public IP address. And it also has the DNS name and the way that we made this work before I had set up a, the  subdomain record here pointing over to [00:01:00] this IP address. So

[00:01:02] I'm going to go over here. This was set up as a pocket. It'd be us. And the address was this three, one 35 to one, six 97.

[00:01:12]And we can see that it is in fact different. Right? We've got the three, one 37, one 92 one four. Now, if I go ahead and shut this down again and restart it, I'll probably end up with another different. IP address. So what we really want to do here is I'm going to go ahead and stop this instance.  And we want to make sure that this IP address doesn't change, because if it does change, then our DNS record that was pointing to it is going to break.

[00:01:43] And,  everyone's going to think that our node is down. So we need to fix that. The way that we can fix that is by going over here and creating something called an elastic IP address. And we do that. This little note here says that basically, AWS is gonna allow us to have one [00:02:00] instance attached to an elastic IP address for no charge, but to make sure that we aren't just hogging IP addresses, there are some small charges if they're not actually  associated with an instance or that are stopped or unattached.

[00:02:13] So we're going to go ahead and allocate one of these. And,  we'll take that. That's, that's  fine. And then when we go back over to our instance, we can go over to networking here,

[00:02:33] go over to our network interface, and now we can go over here and we can  associate an address. Okay. And so we have one here. This is the public one that it gave us as our elastic IP. This is the three one, two 15 100. We're going to go ahead and associate that. And now this is going to stay our public IP address.

[00:03:00] [00:03:00] I'm going to copy that. I'm going to go over here and I'm going to update our record here.

[00:03:14]Okay. It seemed to like that. And we're going to go ahead

[00:03:22] and go back to our instance management here.

[00:03:39]and we're going to start up our entrance here. We can see the elastic IP and the public IP are the same.  This is good.

[00:03:46] Now in order to connect this one, we should be able to connect with our command here. It's the same one that I used before 

[00:04:00] it was going to use.

[00:04:07] And voila, we're now into our machine that we'd set up before.

[00:04:11] And that's how you set up a permanent IP for address.

