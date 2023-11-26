---
title: Remote Command Execution in Go
---

During my summer internship at Google, my primary project was to add a remote troubleshooting utility to Google's [Transfer Appliances](https://cloud.google.com/transfer-appliance/), which are a storage device that allows customers to move data to and from Google Cloud.

As you can imagine, there's a lot of infrastructure that happens behind the scenes when an appliance is getting ready to be shipped out and when it comes back from a customer, inclusing things like flashing the latest operating system and allocating the correct destination for the data. Nowadays, a big portion of this process is automated.

But what if there's a problem? The current troubleshooting procedure involved having to use a slow serial connection to find the IP address of the machine that was having an issue, then login to it remotely over SSH, and manually run whatever troubleshooting commands you wanted to run.

This process is not ideal, so my project, along with an intern partner, was to design, implement, and integrate into existing tooling a utility that would allow a developer or technician to run common troubleshooting procedures or fetch diagnostic information with a single click from a web portal. 

## What I did

Our project began in the design phase. While we knew what our project needed to accomplish and had some rough guidance on potential paths we could take to get there, there will still questions we needed to answer. A big one was how would the appliances communicate with the web portal? Will we use a database? Will we need to log a command history? What about the web server itself?

Ultimately, we settled on a system using [Cloud Pub/Sub](https://cloud.google.com/pubsub/docs/overview), which is an asynchronous messaging service. Messages (which are encoded in [Protocol Buffers]) get posted to a channel that each appliance is reading for new commands, and it replies back with the results of the command. This solution was simple, scalabale, and met the needs of the product.

I worked mostly on the appliance-side code written in __Go__, which involved receiving messages from the channel, checking if there were any commands to be run, running those commands, and sending the result back. There were some definite challenges with this process - for instance, not every command could be run at all times - it's not hard to imagine a situation where an untimely reboot or drive wipe could cause issues, so the program also had to be able to verify whether or not any given command was safe to run given the machine's given state.

I performed some time trials of our final system to benchmark its performance compared to previous manual methods and found that on average, the new utility was about 7.2x faster than previous methods for the commands it supported, with a best case of 11x.

## What I learned

This internship was an opportunity for me to refine my ability of writing robust code and working in larger codebases.

I was introduced to lots of new technologies, including gaining significant experience in Go, and learning about various Google Cloud services, as well as Protocol Buffers - but on a deeper level than that, I was able to examine the way I approach writing code, and how I can tailor that for what my requirements are.

For instance, the nature of my education at Olin meant that I was often working in small teams on projects with tight deadlines where my primary goal was to bodge something together as quickly as possible in order to actually be able to iterate on an idea or prove a concept more than once or twice in the timeframe of a typical university project, after which that code is usually never touched again.

During my internship, I did find this to be useful in some situations - for instance, when we were experimenting with a few different strategies, I was able to very quickly prototype them out - but when I started writing a more final solution, this got me into some hot water when my original approach turned out to be very difficult to test in a clear and concise way, and I was forced to start from scratch and throw out the better part of a week's work.

Whereas my first internship was almost entirely about programming growth - getting better at writing good, clean lines of code - I felt this internship allowed me to step back a few steps and train my _software design and development_ skills - how to design good programs and systems to accomplish a goal.



