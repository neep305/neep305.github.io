---
layout: post
title: Failed to download Chromium r722234
subtitle: npm install 중 Chromium 다운로드 에러 발생시 처리방법
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [nodejs, chromium, puppeteer]
---

## 에러메시지
```
RROR: Failed to download Chromium r722234! Set "PUPPETEER_SKIP_CHROMIUM_DOWNLOAD" env variable to skip download.
Error: self signed certificate in certificate chain
    at TLSSocket.onConnectSecure (_tls_wrap.js:1473:34)
    at TLSSocket.emit (events.js:311:20)
    at TLSSocket._finishInit (_tls_wrap.js:916:8)
    at TLSWrap.ssl.onhandshakedone (_tls_wrap.js:686:12)
  -- ASYNC --
    at BrowserFetcher.<anonymous> (C:\dev\oran-c\node_modules\puppeteer\lib\helper.js:111:15)
    at Object.<anonymous> (C:\dev\oran-c\node_modules\puppeteer\install.js:66:16)
    at Module._compile (internal/modules/cjs/loader.js:1158:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1178:10)
    at Module.load (internal/modules/cjs/loader.js:1002:32)
    at Function.Module._load (internal/modules/cjs/loader.js:901:14)
    at Function.executeUserEntryPoint [as runMain] (internal/modules/run_main.js:74:12)
    at internal/main/run_main_module.js:18:47 {
  code: 'SELF_SIGNED_CERT_IN_CHAIN'
}
```

## npm config 설정 변경 (Puppeteer 다운로드 스킵 처리)
```
$ npm config set puppeteer_skip_chromium_download true -g
```