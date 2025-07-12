# Transfer Domains

These aren't instructions I personally need anymore. But one of the first steps I took before starting my homelab was transferring all of my domains to Cloudflare. This was for a couple reasons:
1. Price. Cloudflare doesn't upsell domains like other providers and instead sells them at-cost.
2. Management. I had my domains listed under a couple different providers and wanted to centralise things a bit by having them all under one provider.

## Unlocking the Domains

In order to transfer your domain from one provider to another, it needs to be unlocked. This involves logging into your current provider, selecting the domain, and somewhere there should be an option to toggle off the domain lock. While you're logged into your current provider it's also worth taking the time to turn off auto-renew since the domain is being transferred to Cloudflare anyway.

## Update DNS Nameserver

Once the domain has been unlocked, navigate to the Cloudflare dashboard, select `Add a domain` and enter the domain you wish to transfer. Cloudflare will then provide you with (typically) 2 DNS nameservers. You'll need to copy both of these and back over on your current provider, there will be an option somewhere in the domain settings to update the current DNS nameserver with the onces Cloudflare has provided for you. Confirm back on the Cloudflare dashboard that you wish to continue with the transfer. Now it's just a waiting game while the DNS nameservers propagate, but really this should only take a few minutes.

## Transfer the Domain

Now that Cloudflare is the DNS provider for your domain, you can now select `Domains` > `Transfer Domains` and Cloudflare will show a list of all the domains you have registered with them that you can transfer. Select the desired domain and you may be asked to provide an authorisation code. Again, you'll get this from your current provider (usually in the same area as where you turn off the domain lock). Copy this over to Cloudflare and the domain transfer will now be under way. Sometimes, and in my experience, an authorisation code may not be needed. Instead I was asked to update the IPS tag on the current provider to be `CLOUDFLARE` (you can find the section to update the IPS tag by selecting 'Transfer to Another Registrar` or something along those lines). And voila, your transfer is now underway. It will typically say that it takes a couple days for the domain to be transferred but you can speed this up by approving the transfer request on the now previous provider's portal.