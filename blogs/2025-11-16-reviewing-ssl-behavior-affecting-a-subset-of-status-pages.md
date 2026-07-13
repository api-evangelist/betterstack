---
title: "Reviewing SSL behavior affecting a subset of status pages"
url: "https://status.betterstack.com/incident/766659"
date: "2025-11-16"
feed_url: "https://status.betterstack.com/feed"
---
We’ve resolved an issue that caused some custom status pages to fail to load or return timeout errors. The problem was related to certificate handling workflow, which temporarily prevented certain pages from obtaining or refreshing their SSL certificates. All affected pages are now loading normally again.
