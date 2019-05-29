# Hello World
```objective-c
#import <Cocoa/Cocoa.h>

int main(int argc, const char * argv[]) {
    NSLog(@"Hello, world!");
    return 0;
}
```

# 类定义
```objective-c
@interface Foo : NSObject {
    int m_var2; // protected
    
  @public
    int var1; // public
}
@end
```

# 类实现
```objective-c
@implementation Foo {
    int m_var1; // private
}
@end
```

# 创建对象
```objective-c
Foo *f = [[Foo alloc] init];
```
```objective-c
Foo *f = [Foo new];
```

# 实例变量
```objective-c
obj->var = 1;
```

# +表示类方法(静态函数)
```objective-c
+ (void)func;
```

# -表示实例方法
```objective-c
- (void)func;
```

# 调用函数
```objective-c
[obj func]; // 实例方法
```
```objective-c
[Foo func]; // 类方法
```

# 函数参数
```objective-c
- (void)func:(int) p1 param2:(int) p2 param3:(int) p3;
```
```objective-c
[obj func:1 param2:2 param3:3];
```
