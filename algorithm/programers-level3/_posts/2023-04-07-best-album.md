---
sidebar:
  title: "Algorithm"
  nav: sidebar-algorithm
  icon: "fas fa-calculator"
title: "[Swift] 베스트앨범"
toc: true
toc_sticky: true
toc_label: 목차
tag: "Programers level3"
depth:
  - title: "Algorithm"
    url: /algorithm/
    icon: "fas fa-calculator"
  - title: "Programers level3"
    url: /algorithm/programers-level3/
    icon: "far fa-folder-open"
---
## 문제 설명
스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다.

속한 노래가 많이 재생된 장르를 먼저 수록합니다.  
장르 내에서 많이 재생된 노래를 먼저 수록합니다.  
장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다.  
노래의 장르를 나타내는 문자열 배열 `genres`와 노래별 재생 횟수를 나타내는 정수 배열 `plays`가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요.  

## 제한사항
* `genres[i]`는 고유번호가 i인 노래의 장르입니다.
* `plays[i]`는 고유번호가 i인 노래가 재생된 횟수입니다.
* `genres`와 `plays`의 길이는 같으며, 이는 `1` 이상 `10,000` 이하입니다.
* 장르 종류는 `100`개 미만입니다.
* 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
* 모든 장르는 재생된 횟수가 다릅니다.

## 입출력 예

|genres|plays|return|
|------|---|---|
|["classic", "pop", "classic", "classic", "pop"]|[500, 600, 150, 800, 2500]|[4, 1, 3, 0]|



* [풀러가기](https://school.programmers.co.kr/learn/courses/30/lessons/42579)

## 문제 이해


## 코드
```swift
func solution(_ genres:[String], _ plays:[Int]) -> [Int] {
  var best: [String: [(index: Int, play: Int)]] = [:]
  var totals: [String: Int] = [:]
  for (index, (genre, play)) in zip(genres, plays).enumerated() {
    best[genre, default: []].append((index: index, play: play))
    totals[genre, default: 0] += play
  }
  
  let totalsSorted = totals.map { ($0.key, $0.value) }.sorted { $0.1 > $1.1 }
  
  var ret: [Int] = []
  for total in totalsSorted {
    let bestSorted = best[total.0]!.sorted(by: { $0.play > $1.play })
    
    var index = 0
    while index < 2 && index < bestSorted.count {
      ret.append(bestSorted[index].index)
      index += 1
    }
  }
  return ret
}
```

## 풀이
-

## 다른 분의 멋진 코드
```swift

```

## 잘 배웠습니다.
-
