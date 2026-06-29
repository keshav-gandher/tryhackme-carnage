# TryHackMe Carnage

If you're looking for a writeup which has not spoilers but all the learning, this just might be the one. In this I am going to share my learning of *how* and *why* I did what I did without any spoilers of the answers so you can learn and userstand along with me. Let's get started.

##
### What was the date and time for the first HTTP connection to the malicious IP?

See for this one I thought there has to be a connection setup first so thought about using `tcp` filter but it doesn't tell you nothing as you don't even know what is the malicious ip. But you know there is a way and that is throught `File > Export Objects > HTTP`. This way we can see from which ip the from were we received the document which was mentioned in the `Scenario`.

Lets see

we can see in that there is a file donladed. Looking at packet we can see the destination ip. now we can search for ip in display filter with an http filter to see the first contact  with ip. 

Also remember to change the change the `View > Time Display Format`