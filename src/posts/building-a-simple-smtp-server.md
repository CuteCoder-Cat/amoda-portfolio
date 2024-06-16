---
title: "What does it mean to build a simple SMTP server?"
seoTitle: "Building a simple SMTP server"
datePublished: 2024-06-15
slug: building-a-simple-smtp-server
cover: https://dynamic-og-image-generator.vercel.app/api/generate?title=Building+a+simple+mail+server%3A+Prologue&author=Kelvin+Amoaba&websiteUrl=https%3A%2F%2Fkelvinamoaba.com&avatar=https%3A%2F%2Favatars.githubusercontent.com%2Fu%2F97001695%3Fv%3D4&theme=github
tags: smtp, server, email, protocol, simple
---

### What does it mean to write your own smtp server

Writing your own SMTP server basically means that you go by the SMTP RFCSs and make sure that your system responds appropriately to whatever commands that come in from other mail servers. Under the hood, smtp servers are doing the same things with slight modifications but the fundamentals all stick to the SMTP RFCs proposed.

So writing a simple mail server means that your server has to run on the appropriate port of SMTP, mostly `25` (these are all well-known ports and should not be changed without reason) and also accept and respond with the appropriate status codes for each and every request that comes to play. Example, if the sending mail server sends the command `helo`, you must know that the right thing to do is respond with the `250 OK` code which is mostly the standard response.. 

These are all fundamental concepts that are highlighted in the various RFCs proposed for the protocol. Once all these are taken into consideration, the initial exchanges can go through without any hassle. 

The only thing about this that becomes quite of a hassle is when it comes to **mail delivery**. There are lots of barricades on the web that prevent the sending of mails from any mail server due to the potential security risks. Although the sending might go through, it is the matter of deliverability that is of major concern. 

There are many ways to mitigate that problem, such as using relays to send your email. This simply means relying on other established services to forward your mail since they have all the fundamentals done right to ensure that all your mails are delivered to the receiving mail servers. These relays can be done through services like Mailgun.

Building a simple mail server that actually works is not only dependent on you going by the RFCs but also making sure that you follow the standard procedures, including setting up your domain name and the associated Zone files to include the `MX` records.

To actually understand the keywords and the various subtle workings of smtp by building your own, you can rely on some libraries to take out a chunk of the work needed to go about it. For example, you can use the `sockets` library in python to set up the necessary tcp sockets needed in order to listen in for connections and also respond appropriately to those requests. You don't need to build everything from the socket level, as that would be a significant hassle.

There are other important factors that need to be considered to actually build a really solid smtp server. Since this is mostly a basic overview, detailed insights into protecting your mail server and meeting other necessary criteria have not been covered.

In the next post, we will be looking at how to build a simple smtp server using python and the `sockets` library. Stay tuned for that, but then, to ensure we are on the same page, you can read up on the SMTP RFCs to get a better understanding of how the protocol works. 

### Resources
- [SMTP RFC](https://tools.ietf.org/html/rfc5321)
- [SMTP Commands](https://www.geeksforgeeks.org/smtp-commands/)
- [SMTP Status Codes](https://en.wikipedia.org/wiki/List_of_SMTP_server_return_codes)
- [SMTP Overview](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)
- [SMTP Relay](https://en.wikipedia.org/wiki/Email_relay)
- [Zone Files](https://en.wikipedia.org/wiki/Zone_file)
- [MX Records](https://en.wikipedia.org/wiki/MX_record)
- [Python Sockets](https://docs.python.org/3/library/socket.html)
- [Mailgun](https://www.mailgun.com/)