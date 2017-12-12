# He Kupu Matapōkere (A Random Word)
He Kupu Matapōkere: he raraunga o kupu matapōkere i te reo Māori, mō te 'fortune' taupānga.
Kua rato ngā kupu i **Te Kupu o te Rā** pae tukutuku (https://kupu.maori.nz).

He Kupu Matapōkere: a dataset of random words, with definitions and examples, in the Māori language to use with the "fortune" application.
The content is created by and sourced from the "Te Kupu o te Rā" website (https://kupu.maori.nz)

## License

This work is licensed under a [CC-BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/3.0/nz/) Creative Commons license. That means you can reuse, adapt, share this work as long as the use is non-commercial, that you attribute Te Kupu o te Rā and Kim Shepherd, and that you apply the same license to your own work.
More info at https://creativecommons.org/licenses/by-nc-sa/3.0/nz/

## Quick start
1. Got 'fortune'? If not, install it!
  * If you're a Linux/BSD/*nix user you probably already do, if not install it with your favourite package manager!
  * If you're a Mac (OSX) user you probably want you install it using a package manager like [homebrew](https://brew.sh) -- there's an easy three-step guide at [http://macappstore.org/fortune/](http://macappstore.org/fortune/)
  * If you're a Windows user, you might have a little more trouble... if you use a GNU environment like Cygwin you're probably OK, and there are compatible implementations of fortune out there other than the original BSD version, like [this python implementation](http://software.clapper.org/fortune/), which should run on any machine with [Python](Python) installed.
   (if you have Windows but you're not a power user and that all sounds scary or a lot of work, the best idea is to get that raw data repurposed (convince someone!) into a new form better for Windows and graphical user interfaces, perhaps a screensaver or something?)
2. Clone this repository or download the [dataset directly](https://github.com/kshepherd/he-kupu-matapokere/archive/master.zip)
3. Copy the **te-reo-kupu** and **te-reo-kupu.dat** files into the directory where your fortune databases (aka 'fortunes') are kept. This location will vary depending on your operating system, version of fortune, your own customisations during installation but hopefully you'll be able to find it somewhere like
  * /usr/share/games/fortunes (Linux installed by package)
  * /usr/local/share/games/fortunes (Installed with homebrew or compiled/installed manually on Linux 

That's it! Next time you run 'fortune' there's a chance it'll pick one from this new database.
You can force this database by giving the name along with the command like ```fortune te-reo-kupu```

If you're really keen as I am, you can delete all the other databases!

But really, wiring this ```fortune te-reo-kupu``` into your login scripts (eg **~/.bash_profile**) is the best way to get some kupu hou in your face, here's how my Mac terminals look now:
```Last login: Wed Dec 13 10:52:17 on ttys007
   Kupu o te wā! #16: "kōwhai"
   
     i te reo Māori:	kōwhai
     i te reo Ingarihi:	yellow
   
   Kōwhai means yellow or refers to the Kōwhai tree.
   He kōwhai te rā.
   The sun is yellow.
   - this is an example of a classifying sentence
   
   Retrieved from https://kupu.maori.nz/kupu/k%C5%8Dwhai (Te Kupu o te Rā)
   Kims-MBP:tereo kim$ 
```
## About this data
This data was collected, with permission, by scraping Te Kupu o te Rā website: https://kupu.maori.nz.
Te Kupu o te Rā is a tino pai te reo Māori resource, with grammar and sentence construction information as well as the Kupu o te Rā (word of the day) and Kupu o te Wiki (word of the week) with definitions and usage examples.
There are 714 kupu in the dataset right now, and as more are added to https://kupu.maori.nz they will be scraped and added to the list.

I've called it "Kupu o te wā" in the sense of "word of the moment" since you'll get a different one every time, unlike the other "of the day/week/month" services out there.

**te-reo-kupu** is the plaintext file with each entry separated by a '%' on its own line

**te-reo-kupu.dat** is the binary .dat file created with strfiles 

**kupu-pages.json** is the JSON file created while initially scraping the https://kupu.maori.nz website and might be useful for people who want to repurpose/reuse this data in different ways.
It's really simple, an array of page objects with seven properties:
* _title_, the title of the page (the kupu/word itself)
* _kupu_maori_, the word in New Zealand Māori
* _kupu_ingarihi_, the word in New Zealand English
* _desc_, the main page content, usually containing definitions, explanations, examples.
* _link_, the canonical link back to te Kupu o te Rā site.
* _url_, the underlying URL with ID number, etc.
* _tau_, the number extracted from the url to give to word some kind of numeric identifier

Here's an example of a single entry in the JSON file.
`{"title":"waho","kupu_maori":"waho","kupu_ingarihi":"outside","desc":"Kei waho te ngeru.\r\nThe cat is outside.\r\n- this is an example of a locative sentence\r\nKei waho te kurī i te whare.\r\nThe dog is outside the house.\r\n- this is an example of a locative sentence","link":"https://kupu.maori.nz/kupu/waho","url":"https://kupu.maori.nz/ShowKupu.aspx?kupu=1","tau":1}`

If you make changes to the plaintext file, you can recreate the .dat file using ```strfiles``` like this:
```strfiles -c % te-reo-kupu te-reo-kupu.dat```

If you don't want to do anything different with the data and just want the files to plug into 'fortune' then you don't need to worry about the JSON file!
 
## About 'fortune'

The database is designed to be used with 'fortune', a common application used in *nix systems to show random quotes, jokes, facts, and so on.
Fortune is often run at login so when you open a new terminal in your Mac, or login to your Linux PC, for example, you see a random 'fortune cookie' as part of the login message.

If you're interested in this database yu probably already know all about 'fortune' but just in case here's some extra reading:
* https://en.wikipedia.org/wiki/Fortune_(Unix)
* https://wiki.archlinux.org/index.php/Fortune
* https://linux.die.net/man/6/fortune (manpage)

## Contributing

If you spot any errors in the data (or in my te reo in this README!) or have any improvements or suggestions, please get in touch!
* Sign up for [Github](https://github.com) and create a new issue at https://github.com/kshepherd/he-kupu-matapokere/issues
* Drop me an email on kim@shepherd.nz or hit me up on Twitter: @kimshepherd

## Acknowledgements

https://kupu.maori.nz created all the original content used here and the site is tino pai!
Samson Ootoovak inspired this work by asking if there was a way to get a 'word of the day' at login. There is now!