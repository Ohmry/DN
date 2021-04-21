# 기타문서
- [기타문서](#기타문서)
  - [HTML에서 SVG 아이콘 사용방법](#html에서-svg-아이콘-사용방법)
  - [CSS 레이아웃에서 2개의 Element를 양쪽으로 정렬하고 싶을 때](#css-레이아웃에서-2개의-element를-양쪽으로-정렬하고-싶을-때)
## HTML에서 SVG 아이콘 사용방법
1. [freeicons.io](https://freeicons.io)에 가서 사용하고 싶은 아이콘을 찾는다.
2. 원하는 아이콘을 SVG로 다운로드 받는다.
3. 다운로드 받은 파일의 소스를 HTML 안에 삽입한다.


- [Material 아이콘 SVG](https://freeicons.io/icon-list/material-icons-toggle)
- [리스트아이콘](https://freeicons.io/material-icons-editor/format-list-bulleted-icon-9991)
- [LinearScaleIcon](https://freeicons.io/material-icons-editor/linear-scale-icon-10012)
- [칸반](https://freeicons.io/material-icons-editor/table-chart-icon-10027)
- [검색](https://freeicons.io/material-icons-action/search-icon-16011)
- [대시보드](https://freeicons.io/material-icons-action/dashboard-icon-15901)
- [HELP](https://freeicons.io/material-icons-action/help-outline-icon-15941)
- [체크박스(공란)](https://freeicons.io/material-icons-toggle/check-box-outline-blank-icon-15586)
- [체크박스(체크)](https://freeicons.io/material-icons-toggle/check-box-icon-15585)

## CSS 레이아웃에서 2개의 Element를 양쪽으로 정렬하고 싶을 때

[참고 했던 사이트](https://m.blog.naver.com/PostView.nhn?blogId=psj9102&logNo=221204146576&proxyReferer=https:%2F%2Fwww.google.com%2F)

- 정렬하고자 하는 2개의 Element를 1개의 부모 Element로 감싼다.
- 부모 Element의 CSS 속성에 flex 속성을 추가한다.
- justify-contents 속성에 space-between 을 설정한다.
- 수직정렬은 align-items: center를 입력한다.
  
``` css
.parent-contianer {
  display: flex;
  justify-contents: space-between;  /** 하위 엘리멘트를 양쪽으로 정렬 */
  align-items: center;              /** 하위 엘리멘트를 수직정렬을 가운데로 설정 */
}
```