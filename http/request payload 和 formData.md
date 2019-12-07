## 理解
> FormData和Payload是浏览器传输给接口的两种格式，这两种方式浏览器是通过Content-Type来进行区分的，如果是 application/x-www-form-urlencoded的话，则为formdata方式; 如果是application/json或multipart/form-data的话，则为 request payload

FormData:x-www-form-urlencoded
> key1=xxxx&key2=xxxxx

request payload:application/json或multipart/form-data
> {
	"key1": "11",
	"key2": 2
}

## 参考
- <https://www.cnblogs.com/btgyoyo/p/6141480.html>
- <https://www.cnblogs.com/tugenhua0707/p/8975615.html>



