# jquery-idleTimeout

idle Activity Timeout and logut redirect for jQuery

## Demo

Note:  This uses the jQuery UI dialog, and UI themes.  I am working on a non UI version – but it may be a while

I have an [active demo here](http://www.philpalmieri.com/js_sandbox/timedLogout/) – it is running on a 30 second timer for the logout, and if you open firebug you will see the keep alive firing every 10 seconds.

## How to use

### Run with defaults
  
  $(document).ready(function(){
    $(document).idleTimeout();
  });


### With Optional Overrides

  $(document).ready(function(){
    $(document).idleTimeout({
      inactivity: 30000,
      noconfirm: 10000,
      sessionAlive: 10000
    });
  });

## The plugin has a few configuration items so you can customize it for your own needs…

- *inactivity: 1200000* //20 Minute default (how long before showing the notice)
- *sessionAlive: 300000*, //5 minutes default how often to hit alive_url, we use for our ajax interfaces where the page doesn’t change very often. This helps to prevent the logout screen of your app appearing in ajax callbacks.  If you set this to false it won’t send off.
- *alive_url: ‘/path/to/your/imHere/url’*, //send alive ping to this url
- *redirect_url: ‘/js_sandbox/’*, //Where to go when log out
- *click_reset: true*, //Reset timeout on clicks (for ajax interface) – resets the sessionAlive timer, so we are not hitting up your app with alive_url if we just did an ajax call for another  reason.
- *logout_url: ‘/js_sandbox/timedLogout/index.html’* //logout before redirect (url so you can completely destroy the session before redirecting to login screen)