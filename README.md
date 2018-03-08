# deep-copy-and-compare-Object

记录一下比较两个对象相等以及深拷贝的方法

# 一 深拷贝

## 利用JQuery， zepto、 Lodash、underScore、Prototype等三方库提供的API

      jQuery.extend([deep], target, object1, [objectN])，
      
      把多个对象合并得到新的target，deep是可选的，默认false，设置为true时深拷贝，即递归合并

## 浅拷贝可以直接使用ES6的Object.assign() 方法
深克隆，不可使用Object.assign() 方法，因为它只会复制对象的引用而不是新建一个对象

## 封装ES6的Object.assign() 方法

          const deepClone=(obj)=>{
             var proto=Object.getPrototypeOf(obj);
             return Object.assign({},Object.create(proto),obj);
          }
          
通过Object.getPrototypeOf函数得到obj被克隆函数的原型上的属性，然后通过Object.assign实现深度克隆。

## 利用JSON，但只能复制可枚举类型的

       let target = JSON.parse(JSON.stringify(source))


# 二 比较对象相等

      JSON.stringify(ObjectA) == JSON.stringify(ObjectB)
