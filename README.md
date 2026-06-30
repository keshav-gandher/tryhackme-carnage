# TryHackMe Carnage

If you're looking for a writeup which has not spoilers but all the learning, this just might be the one. In this I am going to share my learning of *how* and *why* I did what I did without any spoilers of the answers so you can learn and userstand along with me. Let's get started.

##
### What was the date and time for the first HTTP connection to the malicious IP?

See for this one I thought there has to be a connection setup first so I thought about using `tcp` filter but it was not helpful as you don't even know what the malicious IP is. But there is a way and that is through `File > Export Objects > HTTP`. This way we can see from which IP we received the document which was mentioned in the `Scenario`.

We see that there was a zip file downloaded from a specific `IP address`. Now we can set this IP address as destination address in the `display filter` and we can see the communication.

Also we set `View > Time Display Format` for the time format as per the answer format for the question.

**Key Takeaway:** Exporting HTTP objects is a quick way to identify downloaded files and trace them back to the server that hosted them.

##
### What is the name of the zip file that was downloaded?

Since we already identified the downloaded file while exporting HTTP objects in the previous step, we can use the same window to determine the name of the downloaded ZIP file.

**Key Takeaway** Exporting HTTP object is quick way to identify the downloaded files.

##
### What was the domain hosting the malicious zip file?

In the packet where the ZIP file is requested, inspect the HTTP details. The Host field contains the domain name of the web server the client is communicating with, making it the logical place to identify the hosting domain.

**Key Takeaway:** The HTTP Host field identifies the destination domain, making it valuable when tracing where a file was downloaded from.

##
### Without downloading the file, what is the name of the file in the zip file?

To identify the filename without downloading the archive we go to the packet where the ZIP file was requested and then right click and choose `Follow Stream > HTTP`. The Follow Stream option in Wireshark is used to reconstruct and stitch together scattered packets back into a single, continuous, and human-readable conversation. This reconstructs the HTTP conversation, allowing us to inspect the server's response and the transferred file data. From there, scroll through the reconstructed stream until the filename appears.

**Key Takeaway:** The Follow Stream feature reconstructs an application-layer conversation (such as HTTP), making it easier to inspect requests, responses, and transferred data.