# CSS 레이아웃에서 2개의 Element를 양쪽으로 정렬하고 싶을 때

참고 했던 [사이트](https://m.blog.naver.com/PostView.nhn?blogId=psj9102&logNo=221204146576&proxyReferer=https:%2F%2Fwww.google.com%2F)

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