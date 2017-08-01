# depensture

## What is new?
在build.gradle中使用新的方式组织依赖库

1. 简洁
没有长串的 groupId,artifactId,versionId
```
apply from: "$root/Eventbus.gradle"
```

2. 集成混淆
在依赖脚本（如**Eventbus.gradle**）中已经配置好了混淆规则，避免 **app** module 中的 **proguard-rules.pro** 内容堆积过多。

3. 可与传统写法混用
使用`apply from` 引入常用库的同时，也可以在 `dependencies{}`中使用常规的 `compile`语法引入其它库。

## How to use?
将项目copy到**rootProject**目录下

```
apply plugin: 'com.android.application'/'com.android.library'
def root = "$rootDir/depensture/dependencies"
apply from: "$root/ButterKnife.gradle"
apply from: "$root/Dagger2.gradle"
apply from: "$root/Eventbus.gradle"
apply from: "$root/Glide.gradle"

android {
  
  ...
}
```
