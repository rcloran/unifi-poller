# Unifi

Collect your Unifi Controller Data and send it to an InfluxDB instance.
Grafana dashboards included.

## Installation

[See the Wiki!](https://github.com/davidnewhall/unifi-poller/wiki/Installation)

# Backstory

Okay, so here's the deal. I found a simple piece of code on github that
sorta did what I needed; we all know that story. I wanted more data, so
I added more data collection. I believe I've completely rewritten every
piece of original code, except the copyright/license file and that's fine
by me. I probably wouldn't have made it this far if
[Garrett](https://github.com/dewski/unifi) hadn't written the original
code I started with. Many props my man.

The original code pulled only the client data. This app now pulls data
for clients, access points, security gateways and switches. I currently
own two UAP-AC-PROs, one USG-3 and one US-24-250W. If your devices differ
this app may miss some data. I'm willing to help and make it better.
Open an [Issue](https://github.com/davidnewhall/unifi-poller/issues) and
we'll figure out how to get things working for you.

# What's this data good for?

I've been trying to get my UAP data into Grafana. Sure, google search that.
You'll find [this](https://community.ubnt.com/t5/UniFi-Wireless/Grafana-dashboard-for-UniFi-APs-now-available/td-p/1833532).
And that's all you'll find. What if you don't want to deal with SNMP?
Well, here you go. I've replicated 90% of what you see on those SNMP-powered
dashboards with this Go app running on the same mac as my Unifi controller.
All without enabling SNMP nor trying to understand those OIDs. Mad props
to [waterside](https://community.ubnt.com/t5/user/viewprofilepage/user-id/303058)
for making this dashboard; it gave me a fantastic start to making my own.

# What now...

- I probably suck at InfluxDB.

I don't know what should be a tag and what should be a field. I think
I did my best, but there's certainly room for improvements in both
the data input and the Grafana graphs (output).


- The USW and USG code needs love.

Up to this point, my focus has been on UAP. I have only included dashboards
that focus on UAP. I am still working on the other two, but it may be a while
before I get around to publishing them. Help is appreciated.


- Are there other devices that need to be included?

I have: switch, router, access point. Three total, and the type structs are
likely missing data for variants of these devices. e.g. Some UAPs have more
radios, I probably didn't properly account for that. Some gateways have more
ports, some switches have 10Gb, etc. These are things I do not have data on
to write code for. If you have these devices, and want them graphed, open an
Issue and lets discuss.


- Better Installation instructions.

If you're a nerd you can probably figure it out. I'd still like some pretty
pictures and maybe even a Twitch VOD.


- Sanity Checking

Did I actually graph the right data in the right way? Some validation would
be nice.


- Radios, Frequencies, Interfaces, vAPs

My access points only seem to have two radios, one interface and vAP per radio.
I'm not sure if the graphs, as-is, provide enough insight into APs with other
configurations. Help me figure that out?

# What's it look like?

Here's a picture of the Client dashboard.

![image](images/unifi-clients-dashboard.png?raw=true)

Here's a picture of the UAP dashboard. This only shows one device, but you can
select multiple to put specific stats side-by-side.

![image](images/unifi-uap-dashboard.png?raw=true)

# Woah, there's a library in here.

Sure is. If you want to write your own code around unifi data, you can import
the `unidev` library and easily poll your controller. If you have interest in
how to use the library, or need more features, open an Issue. I'm not committed
to documenting it unless it seems useful.


## Copyright & License
- Copyright © 2016 Garrett Bjerkhoel.
- Copyright © 2018 David Newhall II.
- See [MIT-LICENSE](MIT-LICENSE) for license information.
