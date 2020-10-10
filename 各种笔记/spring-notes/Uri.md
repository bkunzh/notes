## http请求url中参数有汉字，报错`HttpClientErrorException: 400 Bad Request`
使用UriComponents.encode()方法进行编码，就可以了。

```java
    UriComponentsBuilder builder = UriComponentsBuilder.fromUriString(URL).path("/pm/workorder/list");
    RestUtils.makeQueryParams(builder, map);
    URI targetUrl = builder.build().encode().toUri(); // encode()
    HttpHeaders headers = headers();
    HttpEntity<?> formEntity = new HttpEntity<>(null, headers);
    ReturnObject result = restTemplate.exchange(targetUrl, HttpMethod.GET, formEntity, ReturnObject.class).getBody();
```
