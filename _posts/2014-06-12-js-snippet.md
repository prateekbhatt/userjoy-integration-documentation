---
layout: page
title: "JS Snippet"
category: tracking
date: 2014-06-12 09:47:44
---

~~~javascript
window.userjoy = window.userjoy || [];

window.userjoy.methods = ['identify', 'company', 'track', 'page', 'track_link', 'track_form'];

window.userjoy.factory = function (method) {
  return function () {
    var args = Array.prototype.slice.call(arguments);
    args.unshift(method);
    window.userjoy.push(args);
    return window.userjoy;
  };
};

for (var i = 0; i < window.userjoy.methods.length; i++) {
  var key = window.userjoy.methods[i];
  window.userjoy[key] = window.userjoy.factory(key);
}

window.userjoy.load = function (key) {

  window._userjoy_id = key;

  if (document.getElementById('userjoy')) return;

  // Create an async script element based on your key.
  var script = document.createElement('script');
  script.type = 'text/javascript';
  script.id = 'userjoy';
  script.async = true;

  script.src = '//cdn.userjoy.co/js/userjoy.js';

  var first = document.getElementsByTagName('script')[0];
  first.parentNode.insertBefore(script, first);
};

window.userjoy.SNIPPET_VERSION = '1.0.0';
window.userjoy.load('YOUR_API_KEY');

userjoy.page();

~~~

