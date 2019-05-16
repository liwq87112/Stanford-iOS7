# Stanford-iOS7
###学习Stanford iOS7 公开课

斯坦福的iOS7公开课，在网易公开课上学习这门课，一共 18 集，希望我能在这里记录下我的学习步伐，记录学习心得。有ppt

Stanford CS193p
Developing Applications for iOS Fall 2013-14

### 第一课 课务、iOS概述  4.28

### 第二课  Xcode 5  卡牌游戏 4.29
All properties start out with a value of 0  
(called nil for pointers to objects).  
So all we need to do is allocate and initialize the object if the pointer to it is nil 
This is called “lazy instantiation”. 
Now you can start to see the usefulness of a @property

所有属性的初始值都是0
(为指向对象的指针调用nil)。
所以我们需要做的就是分配和初始化对象如果指向它的指针是nil
这称为“延迟实例化”。
```
- (NSMutableArray *)cards
{
if (!_cards) _cards = [[NSMutableArray alloc] init];
return _cards;
}
```
### 第三课  Objective-C  卡牌游戏 5.14

```
@property (strong, nonatomic) IBOutletCollection(UIButton) NSArray *buttonArray;
```
1、Xib  Outlet Collection
2、arr[0] 与 arr.firstObject/arr.lastObject 区别
注意不要访问数组索引超出界限(崩溃)(arr[0])。lastObject / firstObject免疫。可以包含任何类的任何对象组合)没有语法说明它包含哪些对象。lastObject性能比firstObject性能好
```
 NSArray *arr = @[]
 NSLog(@"-%@",arr.firstObject);
 NSLog(@"--%@",arr[0]);
```
3 
```
static const int MM_ROW = 2;
#define MM_ROW 2
```
4
头文件.h (public共有api)与实现文件.m (private私有api)
@interface MyClass: MySuperclass…
@end(仅在头文件中)
@ interface MyClass ()……@end(仅在实现文件中)
@ implementation……@end(仅在实现文件中)

5
@property (nonatomic) <type> <property name>(在本课程中始终是非原子的)
它只是setter和getter方法。默认值由编译器自动生成。比单独实例变量更好(延迟实例化、一致性检查、UI更新等)。
@property(strong or weak)<type，它是指向对象>的指针<property name>
@property (getter=<getter name>)…
@ property(readonly)…& @property (readwrite)…
使用点符号调用setter和getter，例如self。卡=…或者if (rank > self.rank)…
@synthesize <name> = _<name>(仅当同时实现setter和getter时)

类型:MyClass *、BOOL (YES或NO)、int、NSUInteger等(id尚未完全解释)。
所有对象都位于堆中(也就是说，我们只有指向它们的指针)。
堆中的对象存储是自动管理的(由强声明和弱声明引导)。
延迟实例化(使用@property的getter来分配和初始化
@property以“随需应变”的方式指向)。顺便说一句，并不是所有东西都是惰性实例化的。:)
如果指针的值为nil(即0)，这意味着指针不指向任何东西。


声明和定义实例方法，例如- (int)match:(NSArray *)otherCards
声明和定义类方法，例如，+ (NSArray *)validSuits
调用实例方法，例如，[myArray addObject:anObject]
调用类方法，例如，unsigned int rank = [PlayingCard maxRank]
方法的名称及其参数被穿插，例如，[deck addCard:aCard atTop:YES]


### 第四课 框架和带属性字符串 5.15
