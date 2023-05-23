---
title: "Photo"
date: 2020-01-28T12:26:30+08:00
draft: false
categories: [_Misc]
tags: []
card: true
weight: 0
---

<!--more-->

## 成长瞬间

### VSCode 折叠策略

VSCode 默认的折叠策略（Wrapping Strategy）为 `simple` ，如下：

<img alt="picture 9" src="imgs/8c2800b1d32340a32b4e84370b7d66921ad46df2a5b822d7c5515565c78b9222.png" />  

偶尔更换了下 Editor 的字体，以同一编辑器字体和网页字体，出现了自动换行不能正确截断的问题。如图所示，总有一部分会显示不完全。

<img alt="picture 10" src="imgs/3b8886a9753323ac86b7838c1863b9e49cb7080d84269e0850b1e0d0009f50bd.png" width="600" />  

经过测试，只需要把折叠策略，修改为 `advanced` 即可。

*=不得不说，VSCode 是真的好用哦，处理文本真的很方便。* 

### DNS 设置

| 公司                 | DNS            | 备注      |
|:-------------------|:---------------|-----------|
| 安印                 | 192.168.51.168 |           |
| 中国互联网络信息中心 | 1.2.4.8        | 210.2.4.8 |
| 百度                 | 180.76.76.76   |           |
| 阿里                 | 223.5.5.5      | 223.6.6.6 |
| 腾讯                 | 119.29.29.29   |           |

### 关于 Iframe 

好吧，老掉牙的技术了，当前许多浏览器已经限制了该功能，了解可能参考：
- https://www.cnblogs.com/bester-ace/articles/9292779.html
- https://www.cnblogs.com/hq233/p/9849939.html

### 奶头乐理论 [1]

> 刺激他们的欲望，降低他们的工资，借钱给他们花，让他们忙的停不下来，同时开放大量的娱乐项目，使他们又不至于崩溃。
>   
> 当娱乐大量占用人们的时间，让人们丧失思考的能力，这一社会麻醉剂将会带来“马太效应”，沉迷的人继续沉迷，清醒的人保持清醒，人与人的差距，甚至阶层间的差距也就拉大了。  
> 
> 从而消磨他们的斗志，抹平阶级跃迁的愿望。

### Git 解决每次拉取、提交代码时都需要输入用户名和密码

在家目录运行 `git config --global credential.helper store` ，然后在拉取时输入正确的用户名和密码，就可以成功记录下来。

### 解决 git bash 不能登录 mysql[4]

在使用 git bash 登录 mysql 时会卡死，怎么办呢？加上 winpty 就好了，如下：

```
winpty mysql -u root -p
```

### 厚墨书源

下面每一条链接都是一个书源，一个一个复制到厚墨里用网络导入，粘贴版是导入单个书源的，无法导入链接

```
- https://cdn.jsdelivr.net/gh/chuner821/deepink/repository.json
- https://cdn.jsdelivr.net/gh/chuner821/deepink/repository.json
```

### element-ui 单元格点击事件，行点击+单元格点击，获取某一行的 index

```html
<el-table :data="tableData" stripe  @cell-click="addSubAccount" :row-class-name="tableRowClassName">
     <el-table-column prop="installer" label="主子账号">
     </el-table-column>
 </el-table>
```

相应逻辑：

```js
//下面是利用给表格添加 className, 添加 index
tableRowClassName ({row, rowIndex}) {
	//把每一行的索引放进 row
	// console.log(row,rowIndex)
	row.index = rowIndex;  //拿到的索引赋值给 row 的 index, 在这个表格中能拿到 row 的里面都会包含 index
	return 'row-remarks'  //className（类名）
},
addSubAccount(row){ //获取焦点弹出关联多个子账号
	console.log(row.index)
},
//如果需要区分那一数列的才能触发需要判断下 prop 的值
addSubAccount(row,column){ //获取焦点弹出关联多个子账号
	console.log(row.index)  //获取下标
	console.log(column.property ) //获取判断条件
	if(column.property == 'prop 的值'){  //prop 的值是自己设置的，注意别重复设置同一个值

	}
},
//如果表格既有行点击，又有单元格点击，在行点击事件里判断 prop, 等不等于你行点击的 prop, 如果等于直接 return false  跳出
```