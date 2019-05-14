# Stanford-iOS7
###学习Stanford iOS7 公开课

斯坦福的iOS7公开课，在网易公开课上学习这门课，一共 18 集，希望我能在这里记录下我的学习步伐，记录学习心得。有ppt

Stanford CS193p
Developing Applications for iOS Fall 2013-14

### 第一课 课务、iOS概述  4.28

### 第二课  Xcode 5  卡牌游戏4.29
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
