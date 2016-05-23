
## 如何把自己的插件发布到bower平台

- 注册一个github账号，bower的机制其实是一个git克隆的过程，开发者需要把自己的插件发布到github上，再在bower上面注册，所有的操作只需几个命令就可以搞定。

## 步骤1

假设我们已经把项目发布到github平台上了，这个是我新发布到github平台上的项目  [https://github.com/bl-front-end/bl-bower](https://github.com/bl-front-end/bl-bower)

打开bash操作如下：

```sh
git tag 0.1.0
```

```sh
git push origin --tags
```
![img](http://ccppchen.github.io/images/QQ20160520-0.jpg)

打开github的项目，就找到我们刚才创建tag版本

![img](http://ccppchen.github.io/images/QQ20160520-1.jpg)

## 步骤2

在bower中注册一下你的项目，输入以下命令执行后，选择y


```sh
bower register my-package-name git-url
==
bower register bowerName https://github.com/bl-front-end/bl-bower
```
![img](http://ccppchen.github.io/images/QQ20160520-2.jpg)

## 步骤3

接下下在我们的grunt 或 gulp 项目中输入以下命令执行

```sh
bower install --save bowerName
```
![img](http://ccppchen.github.io/images/QQ20160520-3.jpg)

接下来看下bower.json

![img](http://ccppchen.github.io/images/QQ20160520-4.jpg)

看到了吗，这个就是我们新增加上的bower插件


**在这里我们要发bower插件上到bower平台上需要注意的一点是bower.json文件 把我项目中的bower.json 粘贴出来**

```JSON
{
	"name": "bl-bower",
	"version": "0.1.0",
	"main": "./app.js",
	"homepage": "https://github.com/bl-front-end/bl-bower.git",
	"keywords": [
	  "百联",
	  "前端bower"
	],
	"license": "MIT"
}
```

### 如何删除bower平台上的插件
```sh
bower login
# enter username and password  
bower unregister bowerName

```
![img](http://ccppchen.github.io/images/QQ20160520-5.jpg)

### 如何删除tag标签

```sh
git push origin :0.1.0
```

### 如何添加js的依赖

在`bower.json`中的dependencies中写依赖关系

```json
{
  name: 'bootstrap',
  description: 'The most popular front-end framework for developing responsive, mobile first projects on the web.',
  keywords: [
    'css',
    'js',
    'less',
    'mobile-first',
    'responsive',
    'front-end',
    'framework',
    'web'
  ],
  homepage: 'http://getbootstrap.com',
  license: 'MIT',
  moduleType: 'globals',
  main: [
    'less/bootstrap.less',
    'dist/js/bootstrap.js'
  ],
  ignore: [
    '/.*',
    '_config.yml',
    'CNAME',
    'composer.json',
    'CONTRIBUTING.md',
    'docs',
    'js/tests',
    'test-infra'
  ],
  dependencies: {
    jquery: '1.9.1 - 2'
  },
  version: '3.3.6'
}
```

