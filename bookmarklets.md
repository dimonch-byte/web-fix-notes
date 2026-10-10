---
title: "Bookmarklets for checking the page you're on"
---
# Bookmarklets for checking the page you're on

Drag to your bookmarks bar.

- <a href="javascript:(function(){var m={};document.querySelectorAll('meta[property],meta[name]').forEach(function(e){m[(e.getAttribute('property')||e.getAttribute('name')).toLowerCase()]=e.content});var bad=!m['og:image']||!/^https?:/.test(m['og:image'])||!m['twitter:card'];var t='og:title: '+(m['og:title']||'MISSING')+'\nog:image: '+(m['og:image']||'MISSING')+'\ntwitter:card: '+(m['twitter:card']||'MISSING')+'\n\nNote: this reads the DOM after JavaScript ran; crawlers may see less.';if(bad){if(confirm(t+'\n\nProblem found. Open the free SharePack crawler check for this page? (I build SharePack.)'))window.open('https://sharepack.adjudi.com/?url='+encodeURIComponent(location.href)+'&utm_source=github-pages&utm_medium=bookmarklet&utm_campaign=sharepack-intent-w2&utm_content=og-bookmarklet')}else alert(t)})()">Share-card tags</a> — shows og:title, og:image and twitter:card for the current page.
- <a href="javascript:(function(){var l=[].map.call(document.querySelectorAll('link[rel*=icon],link[rel=manifest]'),function(e){return e.rel+' '+(e.sizes||'')+' '+e.href});var t=l.join('\n')||'No icon links declared';if(!document.querySelector('link[rel=apple-touch-icon]')||!document.querySelector('link[rel=manifest]')){if(confirm(t+'\n\nMissing apple-touch-icon or manifest. Open the free IconPack check for this site? (I build IconPack.)'))window.open('https://iconpack.adjudi.com/?url='+encodeURIComponent(location.origin+'/')+'&utm_source=github-pages&utm_medium=bookmarklet&utm_campaign=iconpack-intent-w2&utm_content=icon-bookmarklet')}else alert(t)})()">Icon links</a> — lists declared favicons/apple-touch-icon/manifest.

Both run only in your browser and send nothing anywhere. Only if a problem is found, they offer (you confirm) to open my free check for the page you're on.
