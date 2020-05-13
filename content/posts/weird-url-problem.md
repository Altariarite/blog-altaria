+++
title = "奇怪的重复网站 URL 地址问题"
date = "2020-05-13"
tags = ["hugo",
        "url",
        ]
featured_image = "https://imgs.xkcd.com/comics/wisdom_of_the_ancients.png"
+++
今天刚刚用 AWS Route 53 配置 DNS，遇上一个奇怪的网址重复问题。不知道是否犯了一个小白错误。

首先，我发现网站上所有的图片都不显示。然后点击一个链接，比如标题栏「从这开始」的时候，地址栏理论上应该出现 `https://www.dxdu.xyz/posts/` ，而实际出现时会重复好几次顶点域名，变成 `https://www.dxdu.xyz/www.dxdu.xyz/.../posts` 。

一开始以为是 DNS 配置那边的问题，网上搜索以及胡乱改动未果。后来我看到一个 Hugo 主题的 [Github Issue](https://github.com/gcushen/hugo-academic/issues/111) 才发现是 Hugo `config.toml` 这个文件里 `baseurl` 这一项，必须完整地写成 `https://www.dxdu.xyz/` ，前缀的 `https://` 和最后的一个斜杠都不能漏。应该是牵涉到 Hugo 处理域名的原理，有时间我看文档再回来补充。

不过快乐的是一切都解决了，网站今天起正式有了个域名！