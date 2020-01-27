---
layout: post
title: API 엔드포인트 아키텍쳐 패턴
subtitle: REST 방식과 GraphQL 
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [api,endpoint,restful,graphql]
---

# 들어가며

> API 엔드포인트를 구현하는 방식에도 여러가지 패턴들이 있는데, 그 중 가장 많이 알려진 것이 REST 방식(RESTful)이고, 다른 하나가 GraphQL로 최근에 백엔드 개발 쪽에서 많은 관심을 받고 있다. 

## RESTful HTTP API 

> API에서 전송하는 리소스를 URI로 표현하고 해당 리소스에 행하고자 하는 의도를 HTTP 메소드로 정의하는 방식
