# Lua扩展 - Class

原生的Lua中并没有Class的功能。TinaX的Class实现主要参考云风的Class实现。

<!-- more -->

代码用法：

``` lua
--定义一个宠物类
local pet = class()

--ctor是类的构造函数
pet:ctor = function(name)
    self.name = name
end

function pet:GetGameObject()
    --假装这里有代码实现
end

function pet:say()
    print("my name is Van~");
end



--还可以再定义一个类
local cat = class(pet)

--构造函数是一定得有的
function cat:ctor(name)
    super:ctor(name)
end

--重载了父类的say方法
function cat:say()
    print("meow")
end



--使用类

--实例化
local myCat = cat.new("大喵")
myCat:say();

```