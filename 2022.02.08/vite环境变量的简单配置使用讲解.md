vite环境变量的简单配置使用讲解

在前端的日常开发中难免遇到需要打不同环境的包，比如后端提供三个不同的域名，分别用于前端本地测试，以及测试服上线、正式服上线，由于前端使用的是axios请求数据，能够配置不同的baseUrl，然后打包即可。但是有没有一种方式在打包时就自动帮我们修改了呢？由此引入vite环境变量来解决这个问题。



**背景：**

刚开始从事前端开发工作的时候，我看到项目根目录下有三个文件，分别是".env,development .env,test .env,production"，我就非常纳闷，这个是个啥，一脸懵逼，于是我开始了我的探究之路。

通过了解和尝试发现上述三个文件就是用于放置前端环境变量，在项目被运行时，无论是本地运行还是打包就会被加载，在vueCli和vite中我们可以通过在在`package.json`  中 `scripts`运行命令处加入`--mode development/production/test/其他环境变量后缀`指定加载对应的`.env`环境变量文件。

如果不指定，则本地运行默认加载`.env,development`,打包时默认加载`.env.production`。



**设置环境变量（举例）**

本地运行：

.env,development

```
NODE_ENV = 'development'
VITE_PUBLIC_PATH = ''

#VITE_API_BASE_URL  = 'https://development.com'
#本地测试环境如果定义了跨域  这里就根据跨域来 并加入到axios中
VITE_API_BASE_URL = '/api'
```

打包：

.env,test(测试包)

```
NODE_ENV = 'production'
VITE_API_BASE_URL  = 'https://test.com'
VITE_PUBLIC_PATH   = '/test/'
```

.env,production(正式包)

```
NODE_ENV = 'production'
VITE_API_BASE_URL  = 'https://production.com'
VITE_PUBLIC_PATH   = '/production/'
```



**开始使用：**

在通过vite构建的项目中，根据vite官方的意思，环境变量暴露在`import.meta.env`上，在项目中我们直接在这个上面取用我们的环境变量即可。

```typescript
const axiosBaseOptions: AxiosRequestConfig = {
  baseURL: import.meta.env.VITE_API_BASE_URL as string,//这里我们引用进来可以更据命令动态加载对应的环境变量从而动态更改baseUrl。
  timeout: 8000,
};
```

注意：vite项目中除了官方默认有的环境变量外，其他自定义的环境变量必须以`“vite_”`开头才能被识别，这个可以使用vite的`loadEnv`方法来修改，目前本人还未试过😅。



来自vite官方对该部分内容的扩展：

[环境变量和模式 {#env-variables-and-modes} | Vite中文网 (vitejs.cn)](https://vitejs.cn/guide/env-and-mode.html)
