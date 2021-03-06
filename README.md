# PassGen
Generate Passwords Deterministically based on a Master Password

## Motiviation
This was started because I had some concerns regarding password managers.
First, there is a small but real chance that I could lose access to all my passwords (temporarily or permanently) if something terrible happened to the service.
Second, the most secure way to store password is not to store them in the first place!

So with this project I designed a way to generated passwords by combining a master password with a "key" (usually website name) via the HMAC-SHA256 cryptographic function.
I then added some convinience features, like storing the list of keys which is displayed as an auto-complete dropdown list, and storing a hash of the master key to do a fail-early check instead of generating an incorrect password and failing the auth attempt later.

You can still use this tool along with a regular password manager (for mobile sync), it would replace the manager's random password generation, and you would still get the benefit of always having access to your passwords regardless of the manager's availability.

## FAQ
- **Q: Isn't storing a hash of the master password a bad idea?**
- A: It's the old security vs convenience balance, however I do intend to add the ability to disable that convenience.
- **Q: Can I have more than one key list?**
- A: Yes! You can also pass in the key list name as an argument to the executable to launch the tool with that key list pre-selected and loaded. You can then create shortcuts or batch files pinned in start for each of your key lists, this would let allow you to launch the tool very quickly from Search (Win+S).
- **Q: How can I customize the password generation?**
- A: There is currently no UI for this, but you can edit the key file to enforce a max length of the password or to remove symbols from the password. I know, some services have unreasoable limitations on passwords, some are quite dangerous.
- **Q: How can I synchronize the key list?**
- A: This decision is left for the user, depending on how you want to sacrifice security for convenience, you can go from manual sync via encrpted flash drive to auto-sync with Google Drive / OneDrive / Dropbox. If I make it possible to disable storing of the master hash, then the key file would effectively contain no critical secrets.
- **Q: What's with the "text-based key file" comments in the code?**
- A: The initial version stored key lists and master hash in a text file, this made it difficult to implement different generation modes (some website have a rediculous max length for passwords), and the master hash was not good (single iteration, hard-coded salt, ouch). So I switched over to a JSON-based key file and wrote some migration code.
- **Q: Android Version?**
- A: I initally wanted to build an Android version for this tool, but I gave up and used a password manager for the few passwords that I use on my phone, feel free to build your own and ping me.
- **Q: Linux Version?**
- A: I do have a very rough python script that reads the keylist file and generates passwords, but it obviously lacks a lot of convenience features. I might add it to this repo or as a gist.
- **Q: This code is ugly and doesn't use MVVM!**
- A: This is a hobby-project initially made for personal use, very few hours were put into the first version of this.
- **Q: I don't see a value in this tool.**
- A: Just use a full-blown Password Manager, much better than nothing. Stop re-using passwords, and stop inventing simple password generation formulas in your head.

## Contributing
I can't guarantee I'll be very responsive to issues and pull requests. But I'd be interested in discussing improvements to this project and possibly accept pul requests.

## License
This project is licensed under the [MIT License](LICENSE)... honestly I'm not quite aware of the differences between this and other popular licenses, so that was pretty much a random decision.