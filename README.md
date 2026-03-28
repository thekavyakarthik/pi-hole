# Pi-Hole: A Network-Wide Ad Blocker

## Basics

1. A Raspberry Pi is a tiny computer that we will be converting into an Ad blocker
2. Like a CPU needs a desktop, mouse and keyboard to be useful, a raspberry Pi also needs them. If you have access to a monitor or an LCD display, use that to access and modify your raspberry pi. If not, temporarily acquire a monitor/desktop so that we can mirror the Raspberry Pi’s screen onto a personal laptop. The software that we are using to mirror the display is realVNC Viewer.
3. We are building a Network-wide Ad blocker, meaning your device is identified through your wifi Network. Recollect how we identified devices on the internet, that’s what will drive this assignment.

### Thought Experiment
***How does data travel across the internet? How do packages, routers, domain name servers, http requests, the different layers of the internet (like TCP/IP layers), and all the devices across the world share data? How is data tracked or blocked?***

## Pi-Hole
Here's the wikipedia definition:
> Pi-hole is a Linux[^1] network-level advertisement and Internet tracker blocking application which acts as a DNS[^2] sinkhole and optionally a DHCP server[^3], intended for use on a private network."

[^1]: Linux is a type of operating system (like windows and macOS). Raspberry Pi uses a Linux operating system. Linux is highly customizable and open-sourced with a strong resource bank making it perfect for experimentation without Apple or Microsofts rules on its own operating systems.
[^2]: Domain Name Server. It translates URLs which are human-readable into IP addresses for computers to process.
[^3]: Dynamic Host Configuration Protocol, used for auto-assigning IP addresses in a network

## Making a Raspberry Pi your personal Ad Blocker
A brief overview on the assignment: [click here](https://dev.to/eric_dequ/pi-hole-block-ads-and-trackers-on-your-network-4b51)

Open the terminal on your raspberry pi and type in the following command to start installing pi-hole:
`$ curl -sSL https://install.pi-hole.net | bash`

Follow pi-hole's intallation dialogues. Here are a few useful tips:
* We'll worry about static IP address later; click **Continue** and proceed
* When selecting an interface use `wlan0`
* When asked to chose a DNS provider, choose **OpenDNS**
* Include **StevenBlack’s Unified Hosts List** (This is just a comprehensive list of Ads to block that's pre-made for you)
* Enable query logging
* When prompted for a privacy level, chose the one that’s closer to “trackable”
<!--end of list-->
Once set-up is complete you'll be given an ip address, a website link and a password. Save all three. You cannot access your Ad Blocker if your lose them.

You have now installed the pi-hole software on your Raspberry Pi! This is equivalent to downloading VS Code on your windows. It's just another application taking up space if you don't put it to use. So now you have to put the pi-hole to use.

The goal of this Ad Blocker is to well block Ads on your personal devices. But your personal devices are phones, tablets, laptops - not Raspberry Pi's. 

Solution: You need to point your personal devices' DNS to your Raspberry Pi's IP address. This way the websites[^4] you access will send their IP address to the raspberry pi where the pi-hole will then block addresses that are Ads and send thru addresses that are not to your router, which will do the standard retrieving data in the internet.

[^4]: Not just websites, all things that use internet (or in basic terms, all things that use wifi)