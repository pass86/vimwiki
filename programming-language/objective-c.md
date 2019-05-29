# Hello World
```objc
#import <Cocoa/Cocoa.h>

int main(int argc, const char * argv[]) {
    NSLog(@"Hello, world!");
    return 0;
}
```

# 类定义
```objc
@interface Foo : NSObject {
    int m_var2; // protected

  @public
    int var1; // public
}
@end
```

# 类实现
```objc
@implementation Foo {
    int m_var1; // private
}
@end
```

# 创建对象
```objc
Foo *f = [[Foo alloc] init];
```
```objc
Foo *f = [Foo new];
```

# 实例变量
```objc
obj->var = 1;
```

# +表示类方法(静态函数)
```objc
+ (void)func;
```

# -表示实例方法
```objc
- (void)func;
```

# 调用函数
```objc
[obj func]; // 实例方法
```
```objc
[Foo func]; // 类方法
```

# 函数参数
```objc
- (void)func:(int) p1 param2:(int) p2 param3:(int) p3;
```
```objc
[obj func:1 param2:2 param3:3];
```
