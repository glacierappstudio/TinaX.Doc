# C#方法扩展 ： UnityEngine.GameObject

TinaX中对UnityEngine类进行了一些常用的扩展。


- 命名空间： `TinaX`



## DestroySelf 销毁自身


用法：

``` csharp
    GameObject.Find("cube").DestroySelf();

```


## DestroyNow 立即销毁自身

相当于`GameObject.DestroyImmediate();` 

用法：

``` csharp
    GameObject.Find("cube").DestroyNow();

```



## Show 显示

相当于`SetActive(true);` 

- 返回值：`GameObject` 返回对象自身


用法：

``` csharp
    var go = GameObject.Find("cube");
    go.SetActive(false);
    go.Show();

```


## Hide 隐藏

相当于`SetActive(false);` 

- 返回值：`GameObject` 返回对象自身


用法：

``` csharp
    var go = GameObject.Find("cube");
    go.Hide();
    go.Show();

```





## Name 改名

相当于`gameObject.name = "xxx";` 

- 返回值：`GameObject` 返回对象自身


用法：

``` csharp
    var go = GameObject.Find("cube").Name("box");
```






## DontDestroy 载入新场景时不要销毁

相当于`GameObject.DontDestroyOnLoad();` 

- 返回值：`GameObject` 返回对象自身


用法：

``` csharp
    var go = GameObject.Find("cube").DontDestroy();
```




## GetComponentOrAdd 获取组件，如果不存在则新建



- 返回值：`T`  获取或创建的Component对象


用法：

``` csharp
    var image = gameObject.GetComponentOrAdd<Image>();
```


## RemoveComponentIfExists 如果指定组件存在，则移除它



- 返回值：`GameObject`  返回对象自身


用法：

``` csharp
    gameObject.RemoveComponentIfExists<Image>();
```




## RemoveComponentsIfExists 如果指定组件存在，则移除它

> 与上一个命令的区别：如果GameObject上有多个相同的Component，前者只会移除一个，本命令会全部移除。

- 返回值：`GameObject`  返回对象自身


用法：

``` csharp
    gameObject.RemoveComponentsIfExists<Image>();
```



## SetLayerRecursive 设置Layer(递归)

> 将GameObject与其子GameObject全部设置为指定Layer。

- 返回值：`GameObject`  返回对象自身


用法：

``` csharp
    gameObject.SetLayerRecursive(5);
```




## FindOrCreateGo 获取子GameObject，如果不存在则新建



- 返回值：`GameObject`  寻找到或新建的指定名称的子GameObject


用法：

``` csharp
    var sub_Go = gameObject.FindOrCreateGo("sub");
```

非扩展用法

``` csharp
    var sub_Go = GameObjectHelper.FindOrCreateGo("sub");
```




## SetParent 指定父级GameObject



用法：

``` csharp
    gameObject.SetParent(GameObject.Find("Camera"));
```

------

### 链式编程

以上大部分返回自身的命令可以被用于链式编程，如下：

``` csharp
    var go = GameObject.Find("Cube")
        .FindOrCreateGo("sub_cube")
        .SetLayerRecursive(6)
        .DontDestroy()
        .Hide();

```


------


