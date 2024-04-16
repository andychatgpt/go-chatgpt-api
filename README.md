
### 关于har文件和arkoseToken
##### har文件其实是有两种的,一种是登录har,一种是ChatGPT4聊天时的har。这是两种har，很多项目并没有说明白。
- har携带了浏览器指纹，计算了一些软硬件信息、浏览器插件信息等。同一个浏览器指纹使用太过频繁就会失效。
- 下面提供了获取两种har文件的方式。你可以自己获取har文件并计算自己的arkoseToken。同时我们也提供api来让你调用获取两种arkoseToken,具体可以联系我们。
- 本项目中获取到了har文件后，都要放在harPool这个文件夹下

##### 聊天的har文件获取
- 这个主要是给聊天使用，现在ChatGPT 3.5也需要Arkose Token了。
- 获取过程参考[这里](https://github.com/gngpp/ninja/wiki/2-Arkose)

##### 登录接口har文件获取
- 无论是不是Plus账号，这个登录传递ArkoseToken是必须的。
- 获取方式参考上面的获取聊天的HAR文件，只不过是在输入完用户名密码后，要过滤的URL是```https://tcr9i.openai.com/fc/gt2/public_key/0A1D34FC-659D-4E23-B17B-694DCFCF6A6C```。


### 其它问题
##### 接口返回403的问题
- 在请求接口的时候，如果遇到状态码是403,基本上都是CloudFlare的盾给拦截住了
- 用浏览器打开的时候，CloudFlare盾一般是自动跳转5s盾或者有一个CheckBox的"Verify you are human"的点击盾。如果这个盾点击过不去一直循环，或者是更复杂的验证码形式，可以考虑换个IP了
- 5S盾破盾后，程序中再次请求时需要携带破盾的Cookies信息（cf_xxxx）

##### 可能有点效果的去掉CF 403盾的小设置
- 有部分返回403的IP可以简单的通过添加sec-ch-ua-arch和sec-ch-ua-bitness字段来去掉cf验证
- 设置苹果的Chrome浏览器的UA可能会引起某些接口的403问题,将它改成Windows或者苹果其它浏览器的UA可以去掉CF验证


