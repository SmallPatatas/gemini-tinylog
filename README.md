# gemini-tinylog
Simple tinylog CGI script in Python, for use with the gmCapsule gemini protocol server.

It allows a capsule admin to add tinylog entries directly from their client.
Only a client using the authorized identity will be able to add entries. **This security measure should not be removed (unless you are also adding a method for sanitizing user input)**.


### Installation:

Place `tinylog.gmi` and the `tinylog` folder inside your capsule's `cgi-bin/[yourCapsule.example.com]/` folder.

Open `tinylog.gmi` in a text editor, and edit lines 12-14 with your tinylog page's title, your username, and your capsule's domain name. Save and close.

Open `[server root]/cgi-bin/[yourCapsule.example.com]/tinylog/tinylog_editor.gmi` in a text editor, and edit lines 9-10 with a client identity hash, and your capsule's domain name. *To find your identity hash in the Lagrange gemini client, click on the identities tab in the sidebar, then right-click on the identity you would like to use, and select 'copy fingerprint'. Now you can simply paste this 64-character value into the field on line 9 of `tinylog_editor.gmi`, replacing the example text (but keeping the quotation marks).* Save and close the file.

If you haven't already configured a path for cgi scripts in gmCapsule, then open up the configuration file `[server root]/gmcapsule/.gmcapsulerc` and add the following lines, replacing the path if necessary: 

```
[cgi]
bin_root = /home/user/gemini/cgi-bin
```
(For more on configuration, see gmCapsule's documentation at https://geminispace.org/gmcapsule/gmcapsule.html#cgi )

Restart your gmCapsule server and navigate to gemini://yourCapsule.example.com/tinylog.gmi in your client. If everything is set up correctly, you should now be able to add tinylog entries, which will be stored, one entry per line, in `tinylog.csv`.