# Desckit

![Desckit](https://raw.github.com/elis/desckit/master/public/images/logo.png)

Custom desktop wallpaper generator with NodeJS and PhantomJS

***
March 2013: [Desckit is hiring](https://github.com/elis/desckit/wiki/hiring)
***

## Changelog

### Version 0.0.51

* Removed old deskcs, and created a new one called `base-desck`, check it out if you're looking to create your own descks
* Fixed some problems with Desck object and rendering (see #9)

### Version 0.0.5

* Refactored a bunch of code, much cleaner now, and better running

* Added support for rendering multiple descks at the same time

* Changed output directory of rendered descks to `/desckit/public/cache/[DESCK_NAME]` where `[DESCK_NAME]` is the desck used to generate the output

* ImageMagick is now required to visit the front-end

* New front-end: ![Front-End](http://i.imgur.com/wvWSsXC.png)

## Preview / Example Output

Based on `base-desck` desck

![Example output](http://i.imgur.com/frXoMT6.jpg)

## Installation

 - Install [Node.js](http://nodejs.org/download/)
 - Install [PhantomJS](http://phantomjs.org/download.html)
 - Install [ImageMagick](http://www.imagemagick.org/script/binary-releases.php)

For Windows, please place the `phantomsjs.exe` on your `PATH`.

Clone and run the application on your local computer

```shell
$ git clone git://github.com/weisjohn/desckit.git
$ cd desckit
$ npm install
$ node .
```

Once ready, navigate your browser to `http://localhost:1280/descks/base-desck/display` to preview the `base-desck` desck and it's output.

To generate a desktop wallpaper append `render` to the url (like so: `http://localhost:1280/descks/base-desck/render` which will create a new file (or overwrite existing one) in `/desckit/public/cache/base-desck/` directory.

### Windows Configuration
asd
To display your wallpaper in Windows 7/8 use the built in wallpaper rotation tool.

 1. Right click anywhere on your descktop
 2. Select `Personalize` (the lower-most item)
 3. Select `Desktop Background` in the bottom area of the window
 4. Click on `Browse...` next to `Picture location:` dropdown
 5. Locate and select the `/desckit/public/cache/[DESCK_NAME]` directory where `[DESCK_NAME]` is the style you want to use
 6. Select the update interval (I use 1 minute), make sure `Shuffle` is not marked
 7. Click `Save changes`

If you configured the application correctly you will now see the generated wallpaper showing on your desktop.

### Mac OS X Configuration

To display your wallpaper in Mac OSX use the built in wallpaper rotation tool.

 1. Open `System Preferences`
 2. Select `Desktop & Screen Save` (in the top-left area)
 3. Click the `+` button to choose a folder
 4. Locate and select the `/desckit/public/cache/[DESCK_NAME]` directory where `[DESCK_NAME]` is the style you want to use
 5. Select the `Change picture:` interval make sure `Random order` is not selected

If you configured the application correctly you will now see the generated wallpaper showing on your desktop.


## Custom Scripts

The application supports custom scripts to be created.

See `/public/descks/base-desck/` to get started with creating your own descks. The best way to get started with Desckit is by hacking away at that desck.

### A Desck (AKA Script Files)

To create a desck you will need to create a new directory in `/desckit/public/descks` with your name of choise, and put a `desck.json` in it (a good starting point would be to copy `base-desck` desck).

There are currently 2 mandatory script files:

 - `script.ejs` - This is the HTML template for the layout of the desktop wallpaper.
 - `script.js` - This is the Server-side(!!) script to be run when the script is requested. This runs in your NodeJS instance so you can configure it to do whatever you want that is supported by NodeJS.

Optionally, you can include more files in scripts:

 - `script.styl`- This is the Stylus CSS source file that will generate a `script.css` file when needed.

Change those files to create your own customized descktop backgrounds.

## Command Line 

You can run desckit from the command line as well.  This will be the prefered option to run the project in the future.

```
$ npm install -g desckit
```

To render the `base-desck` script only one time (think cron)

```
$ desckit -S base-desck 
```

To re-render every two minutes, specify an interval of 120 seocnds:

```
$ desckit -S base-desck -I 120
```


# Examples

There is one provided example at the moment named `base-desck` that you can use to play around with the application.

## Possibilities

Since this is basically a web-page being rendered into a desktop background, there are a lot of things that can be done with it; just to give you some direction:

 - Use HD Youtube or Vimeo videos as backgrounds
 - Display a different style based on the time of day
 - Display news headlines
 - Display HackerNews threads
 - Show top pics from /r/pics/
 - Use parallax effects

Since this is being rendered on a WebKit based browser, basically anything that you can think of creating with HTML5 can be rendered onto your desktop.

## Developing 

To see the internals of desckit as it operates, set an environment variable for `DEBUG` equal to `desckit`, such as:

```shell
$ DEBUG=desckit* node-dev app.js 
  desckit Express server listening on port 1280 +0ms
```

We do this to help the command-line tool version output clean.

### General Information

At this point the application is in preview/alpha version designed to show the capabilities of this technique. Most of the configuration is hard-coded (like the screen-resolution), you are welcome to change it to fit your needs. Some of the modules used are outdated (like datejs), and in general this is a work in progress aimed at hackers rather than the end-user at this point.

## The Future

The goals for this project are:

 1. Createa community around the project
 2. Create a simple and easy to use way to generate custom wallpapers using a Wysiwyg style designer
 3. Create modular widgets that could be configured to the users needs and wants
 4. Create integration with sites like Github, CSSDeck, jsfiddle along with an internal way to store users styles/designs
 5. Create a gallery of designs with ranking so users who are not into creating their own custom design could select an existing design, add or remove certain modules, and use it without hacking any code
 6. Provide an easy API to allow use of the software on mobile phones and tablets

This is the very first step, unveiling the concept idea, and showing the very rudimentary capabilities, the next step will be decided by you, the user.

## Contact

Created by Eli Sklar

Email: eli.sklar@gmail.com

Twitter: @EliSklar

## Contributors

 - [Eli Sklar](http://github.com/elis)
 - [John Weis](http://github.com/weisjohn)
