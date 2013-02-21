---
layout: post
categories: [blog]
---

I'm have now migrated my entire site to [Jekyll](http://jekyllrb.com/) and [disqus](http://disqus.com/). It took less than half a day. So far I'm impressed.

**The source code of this website is available online at <https://github.com/kerspoon/kerspoon.com>.**

The layout is built with the [Unsemantic fluid grid system](http://unsemantic.com/) and the default layout uses parts from [HTML5 boilerplate](http://html5boilerplate.com/).

I had planned to create the site using a mix of either [EJS Templates](http://embeddedjs.com/) or [Handlebars](http://handlebarsjs.com/) using [Grunt](http://gruntjs.com/) as a build tool. I still feel this would work well but [Jekyll](http://jekyllrb.com/) worked so well out of the box but I stuck with it.

My htaccess file simply re-directs `www.kerspoon.com/*` to `kerspoon.com/*`. Thanks [no-www](http://no-www.org/).

