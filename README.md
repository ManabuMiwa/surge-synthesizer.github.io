# surge-synthesizer.github.io

## Working with the website

For this site we are using a **Jekyll theme**. 

It is named **Swiss** and can be found [here.](https://github.com/broccolini/swiss)

You can download **Jekyll** from [here.](https://jekyllrb.com/)

In order to make changes to the site you will need to follow SOP for working with GitHub pages and Jekyll sites that use themes. You will have to over-ride styles with more specific CSS, you can add more pages as HTML or .md, there is front matter, etc. 

Jekylly has a specific folder structure it looks at to generate sites from. It uses .scss files, layouts, etc. There is a bunch of stuff about using Jekyll and GitHub pages online. Since this was all entirely new to me I won't attempt an in depth tutorial on all the moving pieces.

At a high level, what I did to make changes was create my own surge.scss file. Include that in the theme that we are using. Then made changes to the home.html file. If you would like to make changes to styling I would recommend adding it the surge.scss file only.

# Use GitHub as CMS

You can follow a couple of different paths to make updates to the website. The easiest and most direct way to do that is simply use GitHub as a CMS. This can get most of the simple things you want to change done. 

To make changes this way, all you need to is fork the project. Once you have done that you can create a branch on your fork make changes and then open a PR. [This](https://github.com/surge-synthesizer/surge/blob/master/doc/git-howto.md) git document for the OSS Surge-Synthesizer project outlines a suggested way of doing work and then creating PR's. 

Once you have created a branch in your fork you can then just click the edit button (upper right corner) which should be available on all text documents. Meaning, since the site is all html and css you can just edit stuff in place in the GitHub editor. 

## Using the command line and Jekyll, Bundler, and optionally Docker to get a more modern front end development experience. 

Being comfortable using a command line and understanding how to get everything installed with the correct file permissions level will be key. On a Mac, this meant I installed an updated version of Ruby in a different location that was in $PATH and had correct read/write permissions.

To accomplish this goal, I used rbenv and bundler to get Ruby installed, used bundler to install Jekyll. Once I had done that I made sure to use a command line to go to my GitHub fork directory on my hard drive. 

By the time you have Ruby installed on macOS successfully, you can run the commands below.Following this mac specific tutorial is pretty good for setting up ruby and being able to get gems installed without beating your head against a wall. Caveat emptor applies though. [Moncef Belyamani - Fastest and Easiest Way To Install Ruby on a Mac](https://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/?utm_source=stackoverflow&utm_campaign=51126403#step-2-install-chruby-and-the-latest-ruby-with-ruby-install)

```
$ gem install jekyll
$ gem install bundle
$ git clone https://github.com/surge-synthesizer/surge-synthesizer.github.io.git
$ cd surge-synthesizer.github.io
$ bundle install
$ bundle exec jekyll server
```

After you successfully get through the above, the live version of the site will be running at localhost. 

Since it is a live site, you can open a text editor and make changes to files. Upon saving the file and refreshing the browser, you will see the change appear.

## Docker
You can use Docker to help with all of this stuff. That requires for you to have a Docker account. It will also provide a live version of your site at localhost. Super useful if your changing files often.

If you have Docker installed, you should be able to run the project by switching to the root dir and running:

```
$ rm Gemfile.lock ; docker run --rm -it -v "$(pwd)":/usr/src/app -p 4000:4000 starefossen/github-pages ; git checkout Gemfile.lock
```

# Updating the Skin Library

We have a skin library now! Here's how to update it if you have a new skin

1. For ths skin, generate a preview PNG and a zip file
2. Place the PNG and Zip in the 'assets/skin-library/' directory. If it is a 19 skin put it in 19, if it is an XT skin, put it in XT
3. Edit the skin-library.md to copy one of the rows and modify the text and links
4. Push and merge! Done
