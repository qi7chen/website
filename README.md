# go-vanity-site

这个网站是用来在[Go Module](https://blog.golang.org/using-go-modules) 模式下实现自定义import路径 (Vanity import)


### 申请自有域名
 

首先，需要申请一个自有域名，如`devpkg.work`

则其它项目要引用simplemod的代码，需要这样import

```
import "devpkg.work/simplemod
```

创建一个module

```bash
go mod init devpkg.work/simplemod
git push
```



### 配置静态web服务

动态web服务始终要购买云服务，借助[Github Page](https://pages.github.com/) 静态网站托管，
再配合[netlify](https://www.netlify.com/)提供的[重定向](https://docs.netlify.com/routing/redirects/)功能，可以做一个白嫖版本的go import域名跳转

步骤如下：

1. 创建一个github repo
2. 创建一个netlify app，并绑定此github repo
3. 把自有域名绑定到netlify app上
4. 在github repo上提交go import的html，并编写`_redirects`里的跳转规则


#### 使用此module

初始化一个exmple，并调用simplemod的代码

``` bash
mkdir example && cd example && go mod init example
go get -u -v devpkg.work/simplemod
```

#### 参考

* [vanity import paths in Go](https://sagikazarmark.hu/blog/vanity-import-paths-in-go/)
* [package name](https://blog.golang.org/package-names)
* [goland-standard-project-layout](https://github.com/golang-standards/project-layout)
