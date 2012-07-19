smart-time-ago
======================

Smart Time Ago is a little lib to update the relative timestamps in your document. (e.g "3 hours ago").
It's originally built for https://pragmatic.ly/. 
It's inspired by another jQuery plugin http://timeago.yarp.com/. But give more flexibility and more features.

Installation
------------

You can juse use it as a jQuery plugin. 
If so, you just need copy the lib/timeago.js or src/timeago.coffee to your javascripts lib then load it after jQuery loaded.

Or if you use node, you can install it from npm.
  
    $ npm install -g smart-time-ago
  
Useage
------------

By default smart-time-ago will keep watch on the time elements with a class of timeago and a ISO8601 timestamp in datatime attribute:

    <time class="timeago" datetime="2012-07-18T07:51:50Z">about 8 hours ago</time>
    
You can initialize the smart-time-ago in global like:

    $().timeago();
    
It will watch all your relative time elements by only one TimeAgo instance.

Or you can use it in a specify scope like.
   
    <div class="timeLables">
     <time class="timeago" datetime="2012-07-18T07:51:50Z">about 8 hours ago</time>
     <time class="timeago" datetime="2012-07-18T06:51:50Z">about 9 hours ago</time>
    </div>
    
    $('.timelables').timeago();
 
It will create one TimeAgo instance to update the time elements in the div with timeLables class.

However you can also create TimeAgo instance for every time element separately like:

    $('.timeago').timeago();
    

We highly recommend initialize the smart-time-ago in global or bigger scope, to get better performace. That is a big reason we create this lib.

Why Smart
-------------


smart-time-ago will check and update the relative time every 30000 millisecond (30 seconds) in document. Latter it will check the newest time in your scope then change the interval to a proper value. For example, If the newest time in your document is '2 hours ago'. The smart-time-ago won't check and update the relative time every 30 seconds, because it's unneccessary. It will automaticly make the interval longer to 15 minutes.

So if you need dynamic add the time element to your document without refreshing the page. You might need call the refresh function to refresh the smart-time-ago like:

    $().timeago('refresh');
    
    
Configuration
--------------

There are some default configuration in smart-time-ago

    $.fn.timeago.defaults = {
      selector: 'time.timeago',
      attr: 'datetime',
      dir: 'up',
      suffix: 'ago'
    };
    
The 'time.timeago' is the default selector for smart-time-ago to watch and update.

The 'datetime' is the default attribute to put the ISO8601 absolute time for smart-time-ago to parse.

The 'up' in dir means the elements in your scope is display by time desc. which means if the dir sets to 'up'. smart-time-ago will treat the first element's time as the newest time to adjust the time interval. Oppositely if it set to 'down', smart-time-ago will treat the last element's time as the newewst time.


The 'ago' in 'suffix' means the relative generated by smart-time-ago will look like '3 hours ago'.
If you want the text looks like '3 hours from now', you might need change the 'suffix' to 'from now'.

You can feel free to change the configuration for your needs.

Credits
-------

![pragmatic.ly](https://pragmatic.ly/assets/vlogo.png)

smart-time-ago is maintained and funded by [Pragmatic.ly](https://pragmatic.ly/ "Pragmatic.ly").

Thanks to all the contributors.

Copyright (c) 2012 Terry Tai, Pragmatic.ly (terry@pragmatic.ly, https://pragmatic.ly/)
