---
layout: post
title: 알고리즘 정리 - 1
subtitle: Overview
gh-repo: neep305/neep305.github.io
gh-badge: [star, fork, follow]
tags: [python,algorithm]
---

### Algorithm Characteristics

#### 알고리즘 복잡도(Algorithm complexity)

- 공간복잡도(Space complexity): 얼마나 많은 메모리를 필요로 하는가?
- 시간복잡도(Time complexity): 완료까지 얼마만큼의 시간이 걸리는가?

#### 입력과 출력(Inputs and outputs)

- 알고리즘이 무엇을 입력값으로 받고, 무엇을 결과값으로 주는가?

#### 분류(Classification)
- Serial/parallel, exact/approximate, deterministic/non-deterministic

### Coomon Algorithms
- Search algorithms (검색)
  - 구조에서 특정 데이터를 찾는 알고리즘. 예를 들어 string에 있는 substring

- Sorting algorithms (정렬)
  - 데이터를 정렬 순서에 따라 적용

- Computational algorithms
  - 주어진 데이터 셋을 다른 값으로 계산

- Collection algorithms
  - 특정 아이템수를 세거나, 필요없는 데이터 필터 처리 등

### 알고리즘 퍼포먼스 측정

#### 알고리즘 퍼포먼스에 대한 이해
- 알고리즘이 데이터셋 사이즈에 따른 응답 측정
- **Big-O notation**
  - input size 증가에 따라 퍼포먼스를 분류한다.
  - "O"는 오퍼레이션 오더를 가리킨다. 실행 한번에 대한 타임스케일과 같다.
  - 많은 알고리즘과 데이터 구조는 적어도 1 이상의 O를 갖는다.