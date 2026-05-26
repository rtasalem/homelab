# Streaming music on iOS

While the Navidrome server itself can be access via its own dedicated subdomain e.g. `navidrome.myhomelab.com` (same as all other applications in this homelab), this doesn't allow for as convenient a streaming experience as dedicated iOS apps like Spotify or Apple Music provide. One way to address this is through the [Subsonic API](https://www.subsonic.org/pages/index.jsp). The Subsonic API is compatible with Navidrome, allowing external apps to communicate with personal media servers. This means developers can build iOS applications that can connect directly to the Navidrome server.  

One app in particular that does this is [Amperfy](https://github.com/BLeeEZ/amperfy). Once the app is downloaded to your iPhone, enter the domain name of the server and credentials and that's all that's needed to stream music from the Navidrome server to your iPhone in a Spotify-esque manner.
