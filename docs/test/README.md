# 部分配置示例

> 这个是示例。

## 代码高亮copy


```kotlin
// kotlin 代码高亮，带 copy
@file:JvmName("BooleanExtensions")

package com.tongji.autoparts.extentions

/**
 * <pre>
 *     @desc: boolean extensions to call chained
 * </pre>
 * @author 奚岩
 * @date 2018/11/30 9:13 AM
 */
sealed class BooleanExt<out T>

object Otherwise : BooleanExt<Nothing>()
class TransferData<T>(val data: T) : BooleanExt<T>()

inline fun <T> Boolean.yes(block: () -> T): BooleanExt<T> = when {
    this -> TransferData(block.invoke())
    else -> Otherwise
}

inline fun <T> Boolean.no(block: () -> T): BooleanExt<T> = when {
    this -> Otherwise
    else -> TransferData(block.invoke())
}

inline fun <T> BooleanExt<T>.otherwise(block: () -> T): T = when (this) {
    is Otherwise -> block.invoke()
    is TransferData -> this.data
}
```


## 图片缩放

![](http://img.imtianx.cn/header.png)

## gittalk

参见 **index.html** 文件

## 其他 doc 配置


- jsDelivr CDN : https://www.jsdelivr.com/package/npm/docsify
- awesome-docsify: https://github.com/docsifyjs/awesome-docsify
- 一个不错的主题： [docsify-themeable](https://jhildenbiddle.github.io/docsify-themeable/#/)

---

更多可[参见文档](https://sushantrahate.github.io/docsify-darkly-theme/#/zh-cn/)

