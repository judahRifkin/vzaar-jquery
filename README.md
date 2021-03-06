vzaar.jQuery
============
<hr>
**vzaar.jQuery takes several popular applications of our JavaScript API and wraps them up in a handy plugin for your enjoyment and edification.**

Preparation
-----------

1. Download and extract the [zip file](https://github.com/vzaar/vzaar-jquery/archive/master.zip).
2. Upload it to your server
3. Link to the CSS in your header:

        <link href="css/vzaar.jQuery.min.css" media="screen" rel="stylesheet" type="text/css">
4. Link to the JavaScript files at the foot of your HTML

        <script src="js/jquery-1.9.1.min.js"></script>
        <script src="js/vzaar.jQuery-0.1.min.js"></script>
        <script src="js/flashtakt.client.min.js"></script>

    4a. Or go the CDN-hosted route

            <link href="//libs.vzaar.com/js/assets/vzaar.jQuery-0.1.css" media="screen" rel="stylesheet" type="text/css">

            <script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
            <script src="//libs.vzaar.com/js/vzaar.jQuery-0.1.min.js"></script>
            <script src="//libs.vzaar.com/js/flashtakt/client.min.js"></script>


5. Embed a vzaar video and tell us you need the JavaScript API

        <iframe
          allowFullScreen
          allowTransparency="true"
          class="video-player"
          frameborder="0"
          height="432"
          id="vzvd-918833"
          mozallowfullscreen
          name="vzvd-918833"
          src="http://view.vzaar.com/918833/player?apiOn=true"
          title="video player"
          type="text/html"
          webkitAllowFullScreen
          width="768">
        </iframe>

Usage
-----

###Chapterizer
This takes a list of timecodes in seconds and creates links to points in your video.

Basic usage:

    $(window).load(function() {
      $('#vzvd-918833').vzChapterizer({
    	chapters		   : [0, 28, 79],
    	titles			   : ["Intro", "Another chapter", "The end!"]
    	});
    });

All options:

    $('#vzvd-918833').vzChapterizer({
      chapters       : [0, 28, 79],
      titles         : ["Intro", "Another chapter", "The end!"],
      orientation    : "horizontal",  // horizontal or vertical list layout.
      position       : "bottom",      // positioning of the list -
                                      // top, left, bottom or right.
      appendTimes    : true,          // appends the timecode to each
                                      // chapter title in 00:00 format.
      chapterNumbers : true           // prepends the chapter titles
                                      // with the chapter number.
     });

###Bookmarkifier
This adds a bookmarking option to your video, that stores the saved timecode in a cookie.

Basic usage:

    $(window).load(function() {
      $('#vzvd-918833').vzBookmarkifier();
    });

All options:

    $('#vzvd-918833').vzBookmarkifier({
      persistent  : true,             // autosave on window close
      message     : "Are you sure?"   // custom message if persistent is on
    });

###Playcountattacher
Displays the video's playcount below the video. Please note: this only works with public videos.

Basic usage:

    $(window).load(function() {
      $('#vzvd-918833').vzPlaycountattacher();
    });

###Prerollinator
Plays another of your vzaar videos as preroll.

Basic usage:

    $(window).load(function() {
      $('#vzvd-918833').vzPrerollinator({
        pre     : "1096251"
      });
    });

All options:

    $('#vzvd-918833').vzPrerollinator({
      pre       : "1096251",                                    // vzaar video id
      prevars   : "disableControls=true&hideControls=true",     // flashvars for preroll
      mainvars  : "brandText=Hello!&brandLink=http://vzaar.com" // flashvars for main video
    });

###Postrollinator
Plays another of your vzaar videos as... you guessed it... postroll.

Basic usage:

    $(window).load(function() {
      $('#vzvd-918833').vzPostrollinator({
        post     : "1192459"
      });
    });

All options:

    $('#vzvd-918833').vzPostrollinator({
      post      : "1192459",                                   
      postvars  : "endText=Goodbye!&endLink=http://vzaar.com"  // flashvars for postroll
    });

###Chaining
The Prerollinator and Postrollinator can be chained together.
The Chapterizer, Bookmarkifier and Playcountattacher can also be chained.
Chaining the Pre/Postrollinator to the other methods will lead to misery.

Examples:

    $(window).load(function() {
      $('#vzvd-918833').vzPrerollinator({
        pre     : "1096251"
      }).vzPostrollinator({
        post    : "1192459"
      });
    });

    /* ---- */

    $('#vzvd-918833').vzChapterizer({
      chapters		: [0, 28, 79],
      titles		: ["Intro", "Another chapter", "The end!"]
    }).vzPlaycountattacher();

###Compatibility
####Flash
Chrome, Firefox, IE8+
####HTML5
Most things should work, but might not on iDevices, due to Steve Jobs :ghost:
