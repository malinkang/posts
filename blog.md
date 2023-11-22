
---
title: 纳瓦尔宝典读书笔记
date: 2023-05-16T01:04:00.000Z
featured_image: https://images.unsplash.com/photo-1471899236350-e3016bf1e69e?ixlib=rb-4.0.3&q=85&fm=jpg&crop=entropy&cs=srgb
draft: false
tags: []
categories: []
comment : true
---


## ShortCode

### Spotify

```html
<!--
Parameters:
    type - (Required) album / track / playlist / artist
    id - (Required) Target ID
    width - (Optional) width
    height - (Optional) height
-->

{{ if .IsNamedParams }}
<iframe src="https://open.spotify.com/embed/{{ .Get "type" }}/{{ .Get "id" }}"
    width="{{ default "100%" (.Get "width") }}"
    height="{{ default "380" (.Get "height") }}"
    frameborder="0"
    allowtransparency="true"
    allow="encrypted-media"></iframe>
{{ else }}
<iframe src="https://open.spotify.com/embed/{{ .Get 0 }}/{{ .Get 1 }}"
    width="{{ default "100%" (.Get 2) }}"
    height="{{ default "380" (.Get 3) }}"
    frameborder="0"
    allowtransparency="true"
    allow="encrypted-media"></iframe>
{{ end }}
```

### mermaid

https://gohugo.io/content-management/diagrams/

### douban

```html
{{ $dbUrl := .Get 0 }}
{{ $dbApiUrl := "https://neodb.social/api/catalog/fetch?url=" }}
{{ $dbFetch := getJSON $dbApiUrl $dbUrl }}

{{ if $dbFetch }}
    {{ $itemRating := 0 }}{{ with $dbFetch.rating }}{{ $itemRating = . }}{{ end }}
    <div class="db-card">
        <div class="db-card-subject">
            <div class="db-card-post"><img loading="lazy" decoding="async" referrerpolicy="no-referrer" src="{{ $dbFetch.cover_image_url }}"></div>
            <div class="db-card-content">
                <div class="db-card-title"><a href="{{ $dbUrl }}" class="cute" target="_blank" rel="noreferrer">{{ $dbFetch.title }}</a></div>
                <div class="rating"><span class="allstardark"><span class="allstarlight" style="width:{{ mul 10 $itemRating }}%"></span></span><span class="rating_nums">{{ $itemRating }}</span></div>
                <div class="db-card-abstract">{{ $dbFetch.brief }}</div>
            </div>
            <div class="db-card-cate">{{ $dbFetch.category }}</div>
        </div>
    </div>
{{else}}
    <p style="text-align: center;"><small>远程获取内容失败，请检查 API 有效性。</small></p>
{{end}}
```

## 参考