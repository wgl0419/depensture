# depensture

## What is new?
在build.gradle中使用新的方式组织依赖库

1. 简洁
没有长串的 groupId,artifactId,versionId
```
apply from: "$dependenciesDir/Eventbus.gradle"
```

2. 集成混淆
在依赖脚本（如**Eventbus.gradle**）中已经配置好了混淆规则，避免 **app** module 中的 **proguard-rules.pro** 内容堆积过多。

3. 可与传统写法混用
使用`apply from` 引入常用库的同时，也可以在 `dependencies{}`中使用常规的 `compile`语法引入其它库。

## How to use?
1. 将项目copy到**rootProject**目录下

2. 在 **rootProject** 的 **build.gradle** 文件中加入：
```
ext{
  dependenciesDir = "$rootDir/depensture/dependencies"
}

```
3. 在子 module 工程的**build.gradle**中使用定义好的路径引入依赖

```
apply plugin: 'com.android.application'   #or 'com.android.library'
apply from: "$dependenciesDir/ButterKnife.gradle"
apply from: "$dependenciesDir/Dagger2.gradle"
apply from: "$dependenciesDir/Eventbus.gradle"
apply from: "$dependenciesDir/Glide.gradle"

android {
  
  ...
}
```
