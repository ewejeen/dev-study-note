## GET과 POST 방식

**1.GET**  
- `@Query`와 `@QueryMap` 어노테이션을 사용할 수 있다.
- `@Query`
  - 단일 parameter를 전송할 경우에 사용한다.
  - name이라는 값을 보내주려면 `@Query("name") String name;`처럼 사용하면 된다.
  - 결과적으로 `url.com?name=OOO`처럼 값이 전달된다.
- `@QueryMap`
  - 여러 개의 parameter를 전송할 경우에 사용한다.
  - name, phone이라는 값들을 보내주려면, 이 값들을 map에 넣어서 보내줘야 한다.
  - 임의의 map 이름을 `@QueryMap("map") Map<String, Object> map;`과 같이 지정하고, 구현 코드에서 `map.put(name); map.put(phone)`과 같은 코드로 map에 값을 넣어준 후에 retrofit 코드를 사용하면 된다.
  

**2.POST**
- `@FormUrlEncoded`를 사용해야 한다.
- `@Field`를 사용해서 parameter를 보내 준다.


**************
참고: https://flymogi.tistory.com/entry/Retrofit을-사용해보자-v202
