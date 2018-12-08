+++
title = "How to build Blog"
author = ["Hyosang Kim"]
date = 2018-10-10T16:03:00+09:00
lastmod = 2018-10-19T16:39:10+09:00
tags = ["post"]
draft = false
summary = "ox-hugo, github, disqus 로 간단히 블로그 구축하기"
+++

<div class="ox-hugo-toc toc">
<div></div>

<div class="heading">Table of Contents</div>

- [Hugo](#hugo)
- [github.com](#github-dot-com)
- [netlify.com](#netlify-dot-com)
- [gabia.com (for domain)](#gabia-dot-com--for-domain)
- [disqus.com (for comment)](#disqus-dot-com--for-comment)

</div>
<!--endtoc-->


## Hugo {#hugo}

1.  hugo install, pandoc install
2.  org-capture setting
3.  외부 접속위해서 bind로 서버 start port 1313

    cd $BLOGHOME;<br>hugo server -D --bind=192.168.0.30 --baseUrl=url.com:portNum


## github.com {#github-dot-com}


## netlify.com {#netlify-dot-com}

host domain 생성


## gabia.com (for domain) {#gabia-dot-com--for-domain}

netlify 에 domain 4개 등록


## disqus.com (for comment) {#disqus-dot-com--for-comment}

ref this [link](https://portfolio.peter-baumgartner.net/2017/09/10/how-to-install-disqus-on-hugo/)
