---
title: "Bookmarklets for checking the page you're on"
---
# Bookmarklets for checking the page you're on

Drag to your bookmarks bar.

- <a href="javascript:(function(){var m={};document.querySelectorAll('meta[property],meta[name]').forEach(function(e){m[(e.getAttribute('property')||e.getAttribute('name')).toLowerCase()]=e.content});alert('og:title: '+(m['og:title']||'MISSING')+'\nog:image: '+(m['og:image']||'MISSING')+'\ntwitter:card: '+(m['twitter:card']||'MISSING')+'\n\nNote: this reads the DOM after JavaScript ran; crawlers may see less.')})()">Share-card tags</a> — shows og:title, og:image and twitter:card for the current page.
- <a href="javascript:(function(){var l=[].map.call(document.querySelectorAll('link[rel*=icon],link[rel=manifest]'),function(e){return e.rel+' '+(e.sizes||'')+' '+e.href});alert(l.join('\n')||'No icon links declared')})()">Icon links</a> — lists declared favicons/apple-touch-icon/manifest.

Both run only in your browser and send nothing anywhere.
