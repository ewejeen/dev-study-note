## JSP 파일 include 하기

`<%@include file=""%>` 지시어로 메인 JSP 파일에 서브 JSP 파일을 여러개 불러오니 파일이 너무 커져서 메모리가 오버되었다.

__Stack Trace__
> The code of method _jspx_meth_c_005fif_005f7(PageContext) is exceeding the 65535 bytes limit~~

- `<jsp:include page=""/>` 액션 태그 방식으로 include하니 문제가 해결되었다.
***
#### <%@include file=""%>과 <jsp:include page=""/>의 차이

**1.<%@include file=""%>**  
- **정적으로 JSP 파일을 불러오는 방법**
- 소스 자체를 통째로 불러오는 방식이다. 서브 JSP 파일에서 소스 글자만 떼어내서 메인 JSP에 넣었다고 보면 된다.

**2.<jsp:include page=""/>**
- **동적으로 JSP 파일을 불러오는 방법**
- 렌더링이 완료된 결과물만 불러오는 방식이다. 서브 JSP 내에서 자체적으로 이미 결과를 뽑아낸 뒤에 결과물만 메인 JSP에 보여주는 것이라고 보면 된다.
- 메인 JSP 파일에서 선언한 taglib들이 서브 JSP 파일까지 영향을 주지 않는다. 서브 JSP 각각에 taglib를 다시 선언해야 한다.
- 메인 JSP 파일에서 `<c:set>`으로 선언한 변수도 서브 JSP에서 받을 수 없다.
- 변수를 보내기 위해서는 다음과 같은 방식을 사용한다.
```JSP
<!-- subPage.jsp 화면에 변수 보내기 -->
<jsp:include page="subPage.jsp">
  <jsp:param var="변수명" value="값"/>
</jsp:include>
```
- 서브 JSP 파일에서 `${param.변수명}` 형식으로 불러올 수 있다.

> When you use `jsp:include`, it executed the target in a separate request, and then includes the output in the including JSP. It doesn't include the source of the included target, it includes the output. The means by which that target output is generated is lost.
