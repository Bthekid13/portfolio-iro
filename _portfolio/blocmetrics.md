---
layout: post
title: Blocmetrics
feature-img: "img/navy_blue.jpeg"
thumbnail-path: "img/blocmetrics.png"
short-description: Blocmetrics is an API that track events on a website.

---

Blocmetrics utilizes client-side Javascript snippets (you plug them in) to track page visits on your website. A Server-side API saves those events to a database––which you can access anytime. Page visits are illustrated by colorful charts, so analyzing your data is a stress free task!

Getting Started:

1. insert this Javascript into your application.js file:

```javascript
var blocmetrics = {};
  blocmetrics.report = function(eventName) {

    var event = {event: { name: eventName}};

    var request = new XMLHttpRequest();

    request.open("POST", "http://localhost:3001/api/events", true);

    request.setRequestHeader('Content-Type', 'application/json');

    request.send(JSON.stringify(event));
 };

```

2. Add this yield statement after the default yield at the bottom of your views/layouts/application.html.erb file:

```ruby
<%= yield :analytic %>
```

3. Finally, Add this line at the bottom each page that you want to track:

```javaScript
<% content_for :analytic do %>
  <script type="text/javascript"> $(document).ready(function(){ blocmetrics.report("Topic Show Visit"); }); </script>
<% end %>
```

Want to know more? Check out Blocmetrics's [github](https://github.com/Bthekid13/Blocmetrics) or take it for a [test drive.](https://wil-burke-Blocmetrics.herokuapp.com/)
