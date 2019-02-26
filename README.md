This is the DMR Gateway which allows for the connection of up to four different DMR networks to one MMDVM system. One of the networks is defined as being an XLX reflector, while the other three may be one each of DMR+, BrandMeister, or a local HBLink system.

This software works by use of powerful rewriting rules which allow for changes in the slot, talk group, the type, and even the destination, of the messages. Without a rewrite rule, even if it does no actual rewriting, traffic will not be passed through from that defined network to the MMDVM and back again.

For example, the default configuration moves the announcements from BrandMeister for linking and unlinking to the same talk group slot as the reflectors themselves, a far more reasonable configuration than the default BrandMeister one.

The rewrite rules don’t apply to the XLX reflector, where only the slot and the talk group used may be changed. The controls i.e. private calls, for altering the reflector are fixed. In the case of the XLX reflectors the gateway will issue voice prompts to indicate the current reflector. These are available in a number of languages.

The MMDVM .ini file should have the IP address and port number of the client in the [DMR Network] settings.

They build on 32-bit and 64-bit Linux as well as on Windows using Visual Studio 2017 on x86 and x64.

This software is licenced under the GPL v2 and is intended for amateur and educational use only. Use of this software for commercial purposes is strictly forbidden.

The information in the next post is based on the assumption that most owners of DMR radios want the option of connecting to BrandMeister in addition to XLX DMR. Accessing multiple DMR master servers requires using MMDVMHost with DMRGateway. The images I have seen do not change the radio programming for BrandMeister but remap the Talk Groups for XLX. Therefore for XLX DMR, using MMDVM.ini and DMRGateway.ini information in the next post, radios should be programmed with following channels

For XLX Network 1 in the current DMRGateway and for all XLXs in the upcoming DMRGateway, create manual dial or channel contacts designated as Private call contacts in the 6xxxx range on Slot 2. The RX group should include the Group TG 6 to hear announcements.

Disconnect 64000

Status 65000

Use 64001 to connect to TG 4001

Use 64002 to connect to TG 4002 ...

Use 64026 to connect to TG 4026

Talk set TG 6 Group Call (after connecting to a TG, switch to a channel with TG 6 to both send and receive)

****UPDATE*****

There is a new version of DMRGateway. As of today, this version is still in an experimental branch of the GitHub and may not be available in the popular images. The previous or current version allows selecting between 2 XLX masters. The new version allows selecting up to 999 XLX masters.

The radio programming discussed above (64000, 64001, 64002, .. and 65000, TG 6) are not changed, but new commands are needed to select a particular XLX master. They are private calls in the range 68001 to 68999, with 68313 being XLX313, for example. There is a host file, nominally called XLXHosts.txt that may be populated automatically by the particular image.

The section of DMRGateway.ini would be different, as indicated below:

[XLX Network]
Enabled=1

File=XLXHosts.txt

#Local=3351

Slot=2

TG=6

Base=64000

Startup=313

Relink=10

Debug=0



--------------------------------
