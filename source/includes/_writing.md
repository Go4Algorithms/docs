# Publishing Documentation to Slate

This guide is intended for any team member wishing to publish documentation to our documentation page [g4algorithms.github.io/docs](http://go4algorithms.github.io/docs). If you need any help please contact Sunny Golovine at aa05880@georgiasouthern.edu.

## Prerequisites
In order to publish to slate you will need the following:
* Linux or OSX (Cygwin or Bash for Windows may work but your mileage may vary)
* Ruby
* Git
* A local slate installation (Installation instructions can be found [here](https://github.com/Go4Algorithms/docs/wiki/Installing-Slate))
* A programming text editor (vim, Sublime Text, Atom, etc)

## Writing documentation

You want to start by cloning our fork of slate

```shell
git clone https://github.com/Go4Algorithms/docs.git
```
Once you clone it, navigate to /source/includes and create a markdown file. Make sure the file is in the format `_filename.md`. From here you can edit the file and save when you are done. After you are done, go up to the /source directory and edit the `index.html.md` file, here add the filename (without the underscore and `.md` extension) under `-includes:` (it's at the very top, you can't miss it).

Once you are done editing the file commit and push the code to the repository.
```shell
git add -A
git add -m "your message here"
git push
```
You will be prompted to enter you credentials, go ahead and enter them.

At this point your code is pushed to the repository however it is not *published* yet. Go back to /source and in the terminal execute `deploy.sh`
```shell
./deploy.sh
```
This script will publish the changes you have made. After that you should be able to go to [g4algorithms.github.io/docs](http://go4algorithms.github.io/docs) and see your changes.
