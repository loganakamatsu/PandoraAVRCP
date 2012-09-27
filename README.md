PandoraAVRCP
============

Pandora + AVRCP - Add AVRCP metadata support to Pandora's Android app.

This repo contains a smali patch (and instructions) to add AVRCP/A2DP metadata support to Pandora.

WARNING:
	Modifying Pandora's app probably violates their TOS, so this is for educational purposes only etc, etc.

Notes:
	Known to be working against Pandora version code 37; SHA1 sum = 2a01ff499c5da14dab51c30af9be7f24615dd09c. Might work with others too, who knows.


Procedure:

Get the Pandora apk file. 
			Pull it from your device or whatever is convenient for you.

Use apktool to decompile the apk. 
http://code.google.com/p/android-apktool/
or homebrew has a formula for os x users.
apktool breaks on this app's resources but we don't need to modify those, so use the -r flag thusly:

			apktool d -r pandora.apk
Apply the patch:
cd to the decompiled directory, then
	
			git apply 0001-add-A2DP-AVRCP-Meta-data.patch

Recompile the app

			apktool b

Sign the app

Lots of people have detailed this: http://developer.android.com/tools/publishing/app-signing.html

Install using adb, e-mail, random vulnerabilites
			
			adb install pandora.apk

More Notes:
	You'll have to unintall the original Pandora first since the signatures won't match. Likewise, you'll stop receiving Pandora updates from the Google Market.
	You'll need to have the AVRCP support in your rom. I'm not really sure if it's in AOSP yet but CM10 works. 
 
