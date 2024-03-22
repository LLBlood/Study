# 一、数据结构

## 1. 树

![image-20231027102530953](images\tree.png)

- **子树：**树是一个有限集合，子树则是该集合的子集。就像套娃一样，一棵树下面还包含着其子树。比如，树T1 的子树为 树T2、T3、T4，树T2的子树为 T5、T6 。
- **结点(Node)：**一个结点包括一个数据元素和若干指向其子树分支。比如，在树T1 中，结点A 包括一个数据元素A 和 三个指向其子树的分支。上图中共有 17 个结点 。
- **根结点(Root)：**一颗树只有一个树根，这是常识。在数据结构中,“树根”即根节点。比如，结点A 是树 T1 的根结点; 结点C 是树T1 的子结点，是树 T3 的根结点。
- **度(Degree)：**一个结点拥有的子树数。比如，结点A 的度为 3，结点G 的度为 3，结点H 的度为 1。
- **叶子(Leaf)/ 终端结点：**度为 0 的结点被称为叶子结点，很形象吧。比如，对于树 T1来说，结点F、I、K、L、M、N、O、P、Q 均为叶子节点。
- **分支结点 / 非终端结点：**和叶子结点相对，即度不为 0 的结点。
- **双亲节点或父节点：**若一个节点含有子节点，则这个节点称为其子节点的父节点； 如上图：A是B的父节点。
- **孩子节点或子节点：**一个节点含有的子树的根节点称为该节点的子节点； 如上图：B是A的孩子节点。
- **兄弟节点：**具有相同父节点的节点互称为兄弟节点； 如上图：B、C是兄弟节点。
- **堂兄弟节点：**双亲在同一层的节点互为堂兄弟节点；如上图：E、G、H互为堂兄弟节点。
- **节点的祖先：**从根到该节点所经分支上的所有节点；如上图：A是所有节点的祖先。
- **子孙：**以某节点为根的子树中任一节点都称为该节点的子孙。如上图：所有节点都是A的子孙。
- **层次(Level)：**从根结点开始，根为第一层，根的孩子为第二层，依次往下。比如，结点K 在树 T1 中的层次为 4。
- **深度(Depth)/ 高度：**指树的最大层次。比如，树 T1 的高度为 4 。

## 2. 二叉树

![image-20231027103607175](images\binaryTree.png)

- 二叉树就是度不超过2的树，其每个结点最多有两个子结点
- 二叉树的结点分为左结点和右结点。

- 二叉树中，第 i 层最多有$2^{(i-1)}$个结点。
  
- 如果二叉树的深度为 K，那么此二叉树最多有$2^K -1$个结点

- 二叉树中，终端结点数（叶子结点数）为 n0，度为 2 的结点数为 n2，则 n0=n2+1。

- 具有n个节点的满二叉树深为$log_2(n+1)$。

  

### 2.1 满二叉树

![image-20231027110239225](images\fullBinary Tree.png)

- 如果二叉树中除了叶子结点，每个结点的度都为 2，则此二叉树称为满二叉树。

### 2.2 完全二叉树

![image-20231027110611110](images\completeBinaryTree.png)

- 如果二叉树中除去最后一层节点为满二叉树，且**最后一层的结点依次从左到右分布**，则此二叉树被称为完全二叉树。

### 2.3 二叉搜索树（BST）

![image-20231027110848317](images\binarySearchTree.png)

- 又称: 二叉排序树、二叉查找树
- 若任意节点的左子树不空，则左子树上所有节点的值均小于它的根节点的值；
- 若任意节点的右子树不空，则右子树上所有节点的值均大于它的根节点的值；
- 任意节点的左、右子树也分别为二叉搜索树;

### 2.4 平衡二叉树（AVL）

- **平衡二叉树是一种二叉排序树**，其中每个结点的左子树和右子树的高度差至多等于1。它是二叉排序树的一个进化体
- **平衡因子**：平衡二叉树是在二叉查找树的基础上进行构建，为了维持平衡二叉树的平衡，那么就需要一种机制来判断平衡二叉树是否是平衡的。这种机制就叫做平衡因子。平衡二叉树上某个结点的**左子树深度减去右子树深度的值**，就称**为此结点的平衡因子**。
- 平衡二叉树是一种二叉查找树
- 每个结点的左子树的高度减去右子树的高度的绝对值不超过1
- 空树和左右子树都是平衡二叉树
- 相比红黑树，平衡二叉树比较适用于没有删除的情况

#### 2.4.1 左旋

![image-20231027114914433](images\leftRotate.png)

- 指将根节点的右侧往左拉，原先的右子节点变成新的父节点，并把多余的左子节点出让，给已经降级的根节点当右子节点

#### 2.4.2 右旋

![image-20231027115153298](images\rightRotate.png)

- 指将根节点的左侧往右拉，原先的左子节点变成新的父节点，并把多余的右子节点出让，给已经降级的根节点当左子节点

#### 2.4.3 LL RR LR RL型

![image-20231027115352705](images\rotate.png)

![image-20231027115644304](images\rotateResult.png)

- 左旋和右旋都是以旋转节点为准
- 把key的值为中等的变为树的根，最小的放在左孩子，最大的放右孩子
- 树的旋转，如LL型被称为右旋，RR型称为左旋，LR型是先左旋，再右旋，RL型先右旋再左旋。

### 2.5 红黑树

![image-20231027130912377](images\redBlackTree.png)

- **红黑树**，是一种**二叉搜索树**，但在**每个结点上增加一个存储位表示结点的颜色**，**可以是Red或Black**。 通过**任何一条从根到叶子的路径上各个结点着色方式的限制，红黑树确保没有一条路径会比其他路径长出俩倍**，因而是**接近平衡**的。
- 结点不是红色就是黑色。
- 根节点是黑色的。
- 每个红色结点的两个子结点都是黑色。（从每个叶子到根的所有路径上不能有两个连续的红色结点）。
- 从任一结点到其每个叶子的所有路径都包含相同数目的黑色结点。
- 每个叶子结点都是黑色的(叶结点即指树尾端NIL指针或NULL结点)。
- 红黑树和AVL树都是高效的平衡二叉树，增删改查的时间复杂度都是$O(log_2n)$，红黑树不追求绝对平衡，只需保证最长路径不超过最短路径的2倍，相对而言，降低了插入和旋转的次数，所以在经常进行增删的结构中**性能比AVL树更优，而且红黑树实现比较简单，所以实际运用中红黑树更多**。

## 3. B树（B-树）

![image-20231027131330872](images\3BTree.png)

- B树和AVL树(平衡二叉树) 的差别就是 B树 属于多叉树，又名平衡多路查找树，即一个结点的查找路径不止左、右两个，而是有多个。数据库索引技术里大量使用者B树和B+树的数据结构。一个结点存储多个值(索引)。
- B树的阶数：M阶表示 一个B树的结最多有多少个查找路径(即这个结点有多少个子节点)。M=M路，M=2是二叉树，M=3则是三叉树。
- 每个结点的值(索引) 都是按递增次序排列存放的，并遵循左小右大原则。
- 根结点的 子节点 个数为 [2，M]
- 除 根结点 以外 的 非叶子结点 的子节点个数 为[ Math.ceil(M/2)，M]。 Math.ceil() 为向上取整。
- 每个 非叶子结点 的值(索引) 个数 = 子节点个数 -1 。最小为 Math.ceil(M/2)-1   最大为 M-1 个。
-  B树的所有叶子结点都位于同一层。
- 在数据库查询中，以树存储数据。树有多少层，就意味着要读多少次磁盘IO。所以树的高度越矮，就意味着查询数据时，需要读IO的次数就越少。（众所周知，读IO是一件费事的操作）当数据量大的时候，用AVL树存的话，就算AVL是平衡树，但是也扛不住数据量大，数据量大，AVL树的树高肯定很高，那么读取数据的IO次数也会多。那么有没有办法能压缩AVL树的树高呢？这时候B树就出来了。B树的一个结点可以装多个值，读取时，是把整个结点读到内存，然后在内存中，对结点的值进行处理，在内存中处理速度肯定比磁盘快。所以只要树的高度低，IO少，就能够提升查询效率，这是B树的好处之一。
- B树的每一个结点都包含key(索引值) 和 value(对应数据)，因此方位离根结点近的元素会更快速。（相对于B+树）

## 4. B+树

![image-20231027131549584](images\B+Tree.png)

- B+树内部有两种结点，一种是索引结点，一种是叶子结点。
- B+树的索引结点并不会保存记录，只用于索引，所有的数据都保存在B+树的叶子结点中。而B树则是所有结点都会保存数据
- B+树的叶子结点都会被连成一条链表。叶子本身按索引值的大小从小到大进行排序。即这条链表是 从小到大的。多了条链表方便范围查找数据
- B树的所有索引值是不会重复的，而B+树 非叶子结点的索引值 最终一定会全部出现在 叶子结点中。

### B树好处：

- B树的每一个结点都包含key(索引值) 和 value(对应数据)，因此方位离根结点近的元素会更快速。（相对于B+树）


### B树的不足：

- 不利于范围查找(区间查找)，如果要找 0~100的索引值，那么B树需要多次从根结点开始逐个查找。


- 而B+树由于叶子结点都有链表，且链表是以从小到大的顺序排好序的，因此可以直接通过遍历链表实现范围查找

# 二、设计模式

- 根据目的来分；通过完成什么工作划分为创建型模式、结构型模式和行为型模式 3 种类型
  - 创建型模式：作用于对象的创建，将对象的创建与使用分离。其中囊括了单例、原型、工厂方法、抽象工厂、建造者5 种创建型模式。
  - 结构型模式：将类或对象按某种布局组成更大的结构，其中以代理、适配器、桥接、装饰、外观、享元、组合 7 种结构型模式为主。
  - 行为型模式：作用于类或对象之间相互协作共同完成单个对象无法单独完成的任务，以及怎样分配职责。主要包含了模板方法、解释器、策略、访问者、命令、中介者、迭代器、职责链、备忘录、状态、观察 11种行为型模式

- 根据作用范围来分；根据是用于类上还是用于对象上划分分为类模式和对象模式两种
  - 类模式：用于处理类与子类之间的关系，这些关系通过继承来建立，在编译时刻便确定下来了。工厂方法、（类）适配器、模板方法、解释器均属于该模式
  - 对象模式：用于处理对象之间的关系，这些关系可以通过组合或聚合来实现，在运行时刻是可以变化的，更具动态性。除了以上 4 种，其他的都是对象模式。

- UML图

  ![image-20240124110422591](images\UMLImage.png)

## 2.1 简单工厂模式

### 2.1.1 简述

- 创建型模式，类模式
- 到底要实例化谁,将来会不会增加实例化的对象,比如增加开根运算,这是很容易变化的地方,应该考虑用一个单独的类来做这个创造实例的过
  程,这就是工厂
- 用白话文来说，就是如果有多种运算模式，就将实例化过程交给一个具体的类，对该类的获取方法输入参数，返回一个具体的运算模式

### 2.1.2 UML图

![image-20240116140938035](images\SimpleFactory.png)

## 2.2 策略模式

### 2.2.1 简述

- 行为型模式，对象模式
- 它定义了算法家族,分别封装起来,让它们之间可以互相替换,此模式让算法的变化,不会影响到使用算法的客户。
- 策略模式和简单工厂非常相似，结构基本上一样，但是它们侧重点不一样
  - 策略模式：是一个行为模式，解决策略的切换和扩展，让策略独立于客户端
  - 简单工厂模式：是一种创建模式「创建对象」，接收指令创建出具体的对象，让对象的创建和具体的使用客户无关
  - 工厂模式是创建型的设计模式,它接受指令,创建出符合要求的实例;它主要解决的是资源的统一分发,将对象的创建完全独立出来,让对象的创建和具体的使用客户无关。主要应用在多数据库选择,类库文件加载等。
  - 策略模式是为了解决的是策略的切换与扩展,更简洁的说是定义策略族,分别封装起来,让他们之间可以相互替换,策略模式让策略的变化独立于使用策略的客户。
- 用白话文来说，简单工厂就是为了获取一个对象，策略模式是自己创建对象，然后在某个地方具体使用，并且可以相互替换。

### 2.2.2 UML图

![image-20240116144739070](images\Strategy.png)

## 2.3 装饰模式

### 2.3.1 简述

- 结构型模式，对象模式
- 装饰模式是为已有功能动态地添加更多功能的一种方式，把每个要装饰的功能放在单独的类中,并让这个类包装它所要装饰的对象,因此,当需要执行特殊行为时,客户代码就可以在运行时根据需要有选择地、按顺序地使用装饰功能包装对象了,把类中的装饰功能从类中搬移去除,这样可以简化原有的类，有效地把类的核心职责和装饰功能区分开了。而且可以去除相关类中重复的装饰逻辑。
- 用白话文来说，就是不修改原始类的基础上，通过将原始类传入到新类A，再将新类A传到新类B，不断扩展原始功能，增强原始功能， 并且可以选择性的选取增强功能

### 2.3.2 UML图

![image-20240116160110652](images\Decorator.png)

- 如果只有一个ConcreteComponent类而没有抽象的Component类,那么Decorator类可以是ConcreteComponent的一个子类。同样道理如果只有一个ConcreteDecorator类,那么就没有必要建立一个单独的Decorator类,而可以把Decorator 和ConcreteDecorator的责任合并成一个类。

## 2.4 代理模式

### 2.4.1 简述

- 结构型模式，对象模式
- 代理模式(Proxy),为其他对象提供一种代理以控制对这个对象的访问。
- 用白话文来说，就是不直接访问某个对象，而是访问这个对象的代理类，代理类里面有该对象，通过操作代理类来操作该对象

### 2.4.2 UML图

![image-20240116171549158](images\ProxyImg.png)

## 2.5 工厂方法模式

### 2.5.1 简述

- 创建型模式，对象模式
- 工厂方法模式(FactoryMethod),定义一个用于创建对象的接口,让子类决定实例化哪个类。工厂方法使一个类的实例化延迟到其子类。简单工厂有可能违背开放-封闭原则，为了解决该问题，才出现工厂方法模式
- 用白话文来说，就是原本用一个工厂违背了单一职责，所以用多个工厂来创建对应产品

### 2.5.2 UML图

![image-20240117134935603](images\FactoryModel.png)

## 2.6 原型模式

### 2.6.1 简述

- 创建型模式，对象模式
- 原型模式(Prototype),用原型实例指定创建对象的种类,并 且通过拷贝这些原型创建新的对象。
- 浅拷贝，浅拷贝只复制对象本身和对象中基本数据类型的字段，对于引用类型的字段，浅拷贝只是复制引用，而不是复制引用的对象。这意味着，如果原对象中的引用类型字段被修改，那么拷贝后的对象中的相应字段也会被修改，因为它们引用的是同一个对象。Java中的Object.clone()方法可以实现浅拷贝，但是需要重写clone()方法以及Cloneable接口。
- 深拷贝，深拷贝则完全复制对象以及对象中所有引用类型的字段。这意味着，原对象和拷贝后的对象完全独立，对其中一个对象的修改不会影响到另一个对象。在Java中，实现深拷贝通常需要手动实现，例如通过序列化和反序列化的方式，或者使用第三方库如Apache Commons Lang的SerializationUtils.clone()方法。但是请注意，这种方式只适用于实现了Serializable接口的对象。另外，对于复杂的数据结构（如集合、数组等），可能需要自定义深拷贝的方法，逐个复制元素。
- 用白话文来说，就是复制一个新对象

### 2.6.2 UML图

![image-20240117140709537](images\Prototype.png)

## 2.7 模板方法模式

### 2.7.1 简述

- 行为型模式，类模式
- 模板方法模式,定义一个操作中的算法的骨架,而将一些步骤延迟到子类中。模板方法使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。
- 用白话文来说，就是某些大部分功能相同的类抽取公共模板，将变化的地方抽象化，由子类去实现

### 2.7.2 UML图

![image-20240117143546682](images\TemplateMethod.png)

## 2.8 外观模式

### 2.8.1 简述

- 结构型模式，对象模式
- 外观模式(Facade),为子系统中的一组接口提供一个一致的界面,此模式定义了一个高层接口,这个接口使得这一子系统更加容易使用。MVC经典就是外观模式
- 用白话文来说，就是将所有的操作封装到一个接口，将该接口提供给外界，统一调用

### 2.8.2 UML图

![image-20240117150041402](images\Facade.png)

## 2.9 建造者模式

### 2.9.1 简述

- 创建型模式，对象模式
- 建造者模式(Builder),将一个复杂对象的构建与它的表表示分离,使得同样的构建过程可以创建不同的表示。
- 用白话文来说，就是把一连串的操作，创建过程和获取过程分开调用

### 2.9.2 UML图

![image-20240117151944605](images\Builder.png)

## 2.10 观察者模式

### 2.10.1 简述

- 行为型模式，对象模式
- 观察者模式定义了一种一对多的依赖关系,让多个观察者对象 同时监听某一个主题对象。这个主题对象在状态发生变化时,会通知所有观察者对象,使它们能够自动更新自己。
- 用白话文来说，就是把观察者注册到通知者里面，然后通知者负责调用观察者的方法即可

### 2.10.2 UML图

![image-20240117154624579](images\Observer.png)

## 2.11 抽象工厂模式

### 2.11.1 简述

- 创建型模式，对象模式
- 特殊的工厂方法模式
- 抽象工厂模式(Abstract Factory),提供一个创建一系列相关或相互依赖对象的接口,而无需指定它们具体的类。
- 可以用简单工厂模式，去优化抽象工厂生成对象操作，但是违背了开放-封闭原则，而且修改的地方比较多。
- 可以用反射+抽象工厂模式，去优化简单工厂模式，但是前提是要求类名一致，可以用反射减少操作
- 用白话文来说，其实就是工厂方法模式，一样的

### 2.11.2 UML图

![image-20240118103705264](images\AbstractFactory.png)

## 2.12 状态模式

### 2.12.1 简述

- 行为型模式，对象模式
- 状态模式(State),当一个对象的内在状态改变时允许改变其其行为,这个对象看起来像是改变了其类。
- 状态模式主要解决的是当控制一个对象状态转换的条件表达式过于复杂时的情况。把状态的判断逻辑转移到表示不同状态的一系列类当中,可以把复杂的判断逻辑简化。当然,如果这个状态判断很简单,那就没必要用'状态模式'了。
- 用白话文来说，就是将多个if else通过代码分离的方式简化

### 2.12.2 UML图

![image-20240118135734157](images\State.png)

## 2.13 适配器模式

### 2.13.1 简述

- 结构型模式，类模式
- 适配器模式(Adapter),将一个类的接口转换成客户希望的另外一个接口。Adapter模式使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。
- 在软件开发中,也就是系统的数据和行为都正确,但接口不符时,我们应该考虑用适配器,目的是使控制范围之外的一个原有对象与某个接口匹配。适配器模式主要应用于希望复用一些现存的类,但是接口又与复用环境要求不一致的情况,比如在需要对早期代码复用一些功能等应用上很有实际价值。
- 用白话文来说，和代理很像,适配器模式旨在解决接口不兼容的问题，而代理模式则旨在控制对其它对象的访问,适配器模式旨在使两个不兼容的接口可以协同工作；而代理模式则旨在实现对目标对象的控制，在不改变目标对象的基础上增强其功能或保护其安全性。

### 2.13.2 UML图

![image-20240118154238665](images\Adapter.png)

## 2.14 备忘录模式

### 2.14.1 简述

- 行为型模式，对象模式
- 备忘录(Memento):在不破坏封装性的前提下,捕获一个对象的内部状态,并在该对象之外保存这个状态。这样以后就可将该对象恢复到原先保存的状态。
- 用白话文来说，就是把存储 对象，调用 对象，管理存储 对象三者分开

### 2.14.2 UML图

![image-20240118165923854](images\Memento.png)

## 2.15 组合模式

### 2.15.1 简述

- 结构型模式，对象模式
- 组合模式(Composite),将对象组合成树形结构以表示'部分-整体'的层次结构。组合模式使得用户对单个对象和组合对象的使用具有一致性。
- 用白话文来说，就是针对于树形结构的数据产生的特定模式

### 2.15.2 UML图

![image-20240118175028216](images\Composite.png)

## 2.16 迭代器模式

### 2.16.1 简述

- 行为型模式，对象模式
- 迭代器模式(Iterator),提供一种方法顺序访问一个聚合对象中各个元素,而又不暴露该对象的内部表示。
- 用白话文来说，就是想要遍历聚集对象，但是又不想暴露聚集对象内容，使用聚集对象创建一个迭代器对象，用迭代器来遍历对象

### 2.16.2 UML图

![image-20240119101402971](images\Iterator.png)

## 2.17 单例模式

### 2.17.1 简述

- 创建型模式， 对象模式
- 单例模式(Singleton),保证一个类仅有一个实例,并提供一个访问它的全局访问点。
- 用白话文来说，就是一个类对外界来说，仅有一个实例，并自身提供一个访问接口

### 2.17.2 UML图

![image-20240122133435286](images\Singleton.png)

## 2.18 桥接模式

### 2.18.1 简述

- 结构型模式，对象模式
- 桥接模式(Bridge),将抽象部分与它的实现部分分离,使它们都可以独立地变化。实现系统可能有多角度分类,每一种分类都有可能变化,那么就把这种多角度分离出来让它们独立变化,减少它们之间的耦合
- 用白话文来说，就是一个系统存在多种功能多种抽象，把这些多种抽象独立出来，用聚合/结合的方式放在一起，不使用继承操作
- 该模式与合成/聚合复用原则息息相关

### 2.18.2 UML图

![image-20240122141939525](images\Bridge.png)

## 2.19 命令模式

### 2.19.1 简述

- 行为型模式，对象模式
- 命令模式(Command),将一个请求封装为一个对象,从而使你可用不同的请求对客户进行参数化;对请求排队或记录请求日志,以及支持可撤销的操作.
- 用白话文来说，如果有多个命令执行，就将这些命令封装在一个对象里面，可以对命令进行控制，展示，撤销

### 2.19.2 UML图

![image-20240122144039920](images\Command.png)

## 2.20 职责链模式

### 2.20.1 简述

- 行为型模式，对象模式
- 职责链模式(Chain of Responsibility):使多个对象都有机会处理请求,从而避免请求的发送者和接收者之间的耦合关系。将这个对象连成一条链,并沿着这条链传递该请求,直到有一个对象处理它为止。
- 用白话文来说，就是一个请求有多个人处理，将多个人封装成对象，且能逐步调用

### 2.20.2 UML图

![image-20240122151032052](images\Responsibility.png)

## 2.21 中介者模式

### 2.21.1 简述

- 行为型模式，对象模式
- 中介者模式(Mediator),用一个中介对象来封装一系列的对象交互。中介者使各对象不需要显式地相互引用,从而使其耦合松散,而且可以独立地改变它们之间的交互。
- 用白话文来说，就是如果存在多个对象相互交互的情况，就使用一个中介者对象，将所有对象存到中介者对象中，代理其他对象完成交互

### 2.21.2 UML图

![image-20240122172241410](images\Mediator.png)

## 2.22 享元模式

### 2.22.1 简述

- 结构型模式，对象模式
- 享元模式(Flyweight),运用共享技术有效地支持大量细粒度的对象。
- 用白话文来说，就是把大量重复创建的对象，想办法变成通用只创建一次的对象，不能共享的部分由外界传入

### 2.22.2 UML图

![image-20240123094846296](images\Flyweight.png)

## 2.23 解释器模式

### 2.23.1简述

- 行为型模式，类模式
- 解释器模式(interpreter),给定一个语言,定义它的文法的一种表示,并定义一个解释器,这个解释器使用该表示来解释语言中的句子
- 用白话文来说，就是将某段文字通过解释器翻译成另外一段文字

### 2.23.2 UML图

![image-20240124095036839](images\interpreter.png)

## 2.24 访问者模式

### 2.24.1 简述

- 行为型模式，对象模式
- 访问者模式(Visitor),表示一个作用于某对象结构中的各元素的操作。它使你可以在不改变各元素的类的前提下定义作用于这些元素的新操作. 
- 用白话文来说，就是如果存在固定的数据结构，但是又有不同的操作方法，就可以使用访问者模式，将结构与操作分开，使得操作可以不断变化

### 2.24.2 UML图

![image-20240124110313955](images\Visitor.png)

# 三、Java

## 3.1 java基础

### 3.1.1 基础知识点

- Java中重写equals方法为什么要重写hashcode方法？

   ```
   等价的两个对象散列值⼀定相同，但是散列值相同的两个对象不⼀定等价，这是因为计算哈希值具有随机性，两个值不同的对象可能计算出相同的哈希值。
   HashMap存储值时，先调用hashCode，唯一则存储，不唯一则再调用equals，结果相同则不再存储，结果不同则散列到其他位置。因为hashCode效率更高（仅为一个int值），比较起来更快。
   所以重写equals可能导致对象等价，hashCode不同
   ```

- Comparator和Comparable的区别

   - ![image-20231205134454170](images\compare.png)
   - 如果实现类没有实现Comparable接口，又想对两个类进行比较（或者实现类实现了Comparable接口，但是对compareTo方法内的比较算法不满意），那么可以实现Comparator接口，自定义一个比较器，写比较算法
   - 实现Comparable接口的方式比实现Comparator接口的耦合性要强一些，如果要修改比较算法，则需要修改Comparable接口的实现类，而实现Comparator的类是在外部进行比较的，不需要对实现类有任何修改。从这个角度说，实现Comparable接口的方式其实有些不太好，尤其在我们将实现类的.class文件打成一个.jar文件提供给开发者使用的时候。实际上实现Comparator 接口的方式后面会写到就是一种典型的策略模式。

- 多态

   - 多态机制包括静态多态（编译时多态）和动态多态（运行时多态）
   - 静态多态比如说重载，动态多态一般指在运行时才能确定调用哪个方法
   - 多态实现方式：子类继承父类（extends）和类实现接口（implements）
   - 多态核心之处就在于对父类方法改写或对接口方法实现，以取得在运行时不同执行效果

- 反射

   - 用 Class.forName 静态方法。
   - 用类.class 方法
   - 用实例对象.getClass() 方法

- 类实例化顺序为： 父类静态代码块/静态域->子类静态代码块/静态域 - > 父类非静态代码块 -> 父类构造器 -> 子类非静态代码块 -> 子类

- 创建对象

   - 用 new 语句创建对象
   - 使用反射，使用 Class.newInstance()创建对象/调用类对象构造方法—— Constructor
   - 调用对象clone()方法
   - 运用反序列化手段，调用 java.io.ObjectInputStream 对象的 readObject()方法
   - 使用 Unsafe

- try-catch-finally-return 执行描述

   - 如果不发生异常，不会执行 catch

   - 不管有没有发生异常，finally 都会执行

   - 即使try 和 catch 中有 return 时，finally 仍然会执行

   - finally 在 return 后面表达式运算完后再执行。（此时并没有返回运算后值，而先要返回值保存起来，若 finally 中无return，则不管 finally 中代 码怎么样，返回值都不会改变，仍然之前保存值），该情况下函数返回值在 finally 执行前确定

      ```java
      public class TryTest {
          public static int getResult() {
              int result = 1;
              try {
                  System.out.println("run in try");
                  result++;
                  return result;
              } catch (Exception e) {
                  System.out.println("run in catch");
                  result++;
                  return result;
              } finally {
                  System.out.println("run in finally");
                  result++;
              }
          }
      
          public static void main(String[] args) {
              int result = getResult();
              System.out.println("result : " + result);
          }
      }
      // run in try
      // run in finally
      // result : 2
      ```

   - finally 部分就不要 return 了，要不然，就回不去 try 或者catch  return 了



### 3.1.2 JDK Proxy和CGLib

- JDK Proxy是实现目标对象的接口，而GGLib是继承目标对象

- JDK Proxy和CGLib都是在运行期生成字节码

- JJDK Proxy是通过反射调用目标对象的方法，而CGLib是采用FastClass机制来调用

- CGLib无法代理final修饰的方法

- JDK Proxy实现过程

  - 核心代码

    ```java
    public class ProxyFactory {
        private Object target;
    
        public ProxyFactory(Object target) {
            this.target = target;
        }
    
        public Object getProxy() {
            ClassLoader classLoader = this.getClass().getClassLoader();
            Class<?>[] interfaces = target.getClass().getInterfaces();
            InvocationHandler invocationHandler = new InvocationHandler() {
                @Override
                public Object invoke(Object proxy, Method method, Object[] args) {
                    Object result = null;
                    try {
                        System.out.println("[动态代理][日志] "+method.getName()+"，参数："+ Arrays.toString(args));
                        result = method.invoke(target, args);
                        System.out.println("[动态代理][日志] "+method.getName()+"，结 果："+ result);
                    } catch (Exception e) {
                        e.printStackTrace();
                        System.out.println("[动态代理][日志] "+method.getName()+"，异常："+e.getMessage());
                    } finally {
                        System.out.println("[动态代理][日志] "+method.getName()+"，方法执行完毕");
                    }
                    return result;
                }
            };
            /**
             * newProxyInstance()：创建一个代理实例
             * 其中有三个参数：
             * 1、classLoader：指定加载动态生成的代理类的类加载器（注：所有引入的第三方类库以及自己编写的java类 都是由 应用类加载器 负责加载的）
             【根类加载器（Bootstrap）> 扩展类加载器（Extension）> 系统类加载器（System）
             系统类加载器又称为应用类加载器】
             * 2、interfaces：获取目标对象实现的所有接口的class对象所组成的数组
             * 3、invocationHandler：设置代理对象实现目标对象的接口的方法的过程，即代理类中如何重写接口中的抽象方法
             */
            return Proxy.newProxyInstance(classLoader, interfaces, invocationHandler);
        }
    }
    ```

  - JDK Proxy原理

    ```
    Vm options
    -Dsun.misc.ProxyGenerator.saveGeneratedFiles=true
    
    生成对应的.class代理文件
    package com.sun.proxy;
    public final class $Proxy4 extends Proxy implements CalculatorI
    ```

    - 代理类继承了Proxy类，其主要目的是为了传递InvocationHandler
    - 代理类实现了被代理的接口CalculatorI，这也是为什么代理类可以直接强转成接口的原因。
    - 有一个公开的构造函数，参数为指定的InvocationHandler，并将参数传递到父类Proxy中。
    - 每一个实现的方法，都会调用InvocationHandler中的invoke方法，并将代理类本身、Method实例、入参三个参数进行传递。这也是为什么调用代理类中的方法时，总会分派到InvocationHandler中的invoke方法的原因

- CGLib 实现过程

  - 核心代码

    ```java
    public class SampleClass {
        public void test() {
            System.out.println("121212");
        }
    
        public static void main(String[] args) {
            Enhancer enhancer = new Enhancer();
            enhancer.setSuperclass(SampleClass.class);
            enhancer.setCallback(new MethodInterceptor() {
                @Override
                public Object intercept(Object o, Method method, Object[] objects, MethodProxy methodProxy) throws Throwable {
                    System.out.println("before run");
                    Object o1 = methodProxy.invokeSuper(o, objects);
                    System.out.println("after run");
                    return o1;
                }
            });
            SampleClass sampleClass = (SampleClass) enhancer.create();
            sampleClass.test();
        }
    }
    ```

  - CGLib 原理

    ```
    System.setProperty(DebuggingClassWriter.DEBUG_LOCATION_PROPERTY, System.getProperty("user.dir"));
    debug启动可查看对应class文件
    ```

    - Enhancer创建一个被代理对象的子类并且拦截所有的方法调用，Enhancer不能够拦截final方法，例如Object.getClass()方法，这是由于Java final方法语义决定的。基于同样的道理，Enhancer也不能对fianl类进行代理操作。这也是Hibernate为什么不能持久化final class的原因
    - 生成的动态代理类继承了父类 SampleClass，并且实现了接口 Factory
    - 动态代理类持有 MethodInterceptor
    - 动态代理类会重写父类 SampleClass的非 final、private 方法；也会构建自己的方法（cglib 方法），构建方式：CGLIB”+“$父类方法名$
    - cglib 方法的方法体：super.方法名，直接调用父类；重写方法：它会调用拦截器中的 intercept() 方法
    - methodProxy.invokeSuper() 方法会调用动态代理类中的 cglib 方法；methodProxy.invoke() 方法会调用动态代理类中的重写方法


### 3.1.3 深拷贝和浅拷贝

- 无论是深拷贝还是浅拷贝，都需要通过实现Cloneable接口，并实现clone()方法，以在clone()方法里面实现浅拷贝或者深拷贝的逻辑
- 浅拷贝，就是只复制某个对象的指针，而不复制对象本身，这种复制方式意味着两个引用指针指向被复制对象的同一块内存地址
- 深拷贝，会完全创建一个一模一样的新对象，新对象和老对象不共享内存，也就意味着对新对象的修改不会影响老对象的值

### 3.1.4 限制问题

- 静态成员属于类， 随着 类加载而加载到静态方法区内存，当类加载时，此时不一定有实例， 没有实例，就不可以访问非静态成员。类加载先于实例创静态环境中，不可以访问非静态变量
- 构造器不能被继承，因为每个类类名都不相同，而构造器名称与类名相 同， 所以谈不上继承。 又由于构造器不能被继承，所以相应就不能被重写了
- Java 不支持多继承，Java 提供了接口和内部类以达到实现多继承功能，弥补单继承缺陷
- final 修饰类叫最终类，该类不能被继承。final 修饰方法不能被重写。final 修饰变量叫常量，常量必须初始化，初始化之后值就不能被修改。
- round() ：返回四舍五入，负 .5 小数返回较大整数，如 -1.5 返回 -1
- ceil() ：返回小数所在两整数间较大值，如 -1.5 返回 -1
- floor() ：返回小数所在两整数间较小值，如 -1.5 返回 -2.0。

### 3.1.5 序列化和反序列化

- 序列化，就是把内存里面的对象转化为字节流，以便用来实现存储或者传输，序列化的前提是保证通信双方对于对象的可识别性，所以很多时候，我们会把对象先转化为 通用的解析格式，比如json、xml等。然后再把他们转化为数据流进行网络传输，从而实现跨平台和 跨语言的可识别性
- 反序列化，就是根据从文件或者网络上获取到的对象的字节流，根据字节流里面保存的对象描述信息和状态

### 3.1.6 面向对象原则

- 单一职责原则:一个类只做它该做事情，就一个类而言,应该仅有一个引起它变化的原因。
- 开放封闭原则：软件实体应当对扩展开放，对修改关闭
- 依赖倒转原则：面向接口编程
- 里氏代换原则：子类型必须能够替换掉它们的父类型
- 接口隔离原则：接口要小而专，绝不能大而全
- 合成聚合复用原则：优先使用聚合或合成关系复用代码
  - 合成(Composition,也有翻译成组合)和聚合(Aggregation)都是关联的特殊种类。
  - 聚合表示一种弱的'拥有'关系,体现的是A对象可以包含B对象,但B双对象不是A对象的一部分;
    - 大雁是群居动物,所以每只大雁都是属于一个雁群,一个雁群可以有多只大雁,所以大雁和雁群是聚合关系。

  - 合成则是一种强的'拥有'关系,体现了严格的部分和整体的关系,部分和整体的生命周期一样
    - 强的'拥有'关系,体现了严格的部分和整体的关系,部分和整体本的生命周期一样。比方说,大雁有两个翅膀,翅膀与大雁是部分和整体的关系,并且它们的生生命周期是相同的,于是大雁和翅膀就是合成关系

- 迪米特法则：迪米特法则又叫最少知识原则，一个对象应当对其他对象有尽可能少了解，如果两个类不必彼此直接通信,那么这两两个类就不
  应当发生直接的相互作用。如果其中一个类需要调用另一个类的某一个方法的话,可以通过第三者转发这个调用。

### 3.1.7 反射详解

- 在Java中，每个类都有一个与之关联的Class对象。这个Class对象实际上是一个元数据，它包含了关于该类的所有信息，例如类的名称、父类、实现的接口、声明的字段和方法等。

- 正常类加载过程

  - 当执行new Student()，会触发JVM加载Student.class文件
  - JVM从本地磁盘找到Student.class文件并加载到JVM内存中
  - .class文件加载入内存后，JVM会自动创建一个class对象(Class)，一个类只会产生一个class对象
  - 得到class对象(Class)后，反向获取Student对象的各种信息

- 获取class的Class实例

  - 知道具体类的情况下可以使用： 直接通过一个 class 的静态变量 class 获取
  - 通过 Class.forName()传入类的路径获取： 如果知道一个 class 的完整类名，可以通过静态方法 Class.forName() 获取
  - 通过对象实例instance.getClass()获取： 如果我们有一个实例变量，可以通过该实例变量提供的 getClass() 方法获取
  - 通过类加载器xxxClassLoader.loadClass()传入类路径获取

- 因为 Class 实例在JVM中是唯一的，获取的 Class 实例是同一个实例。可以用== 比较两个 Class 实例：

- 通常情况下，我们应该用 instanceof 判断数据类型，因为面向抽象编程的时候，我们不关心具体的子类型。只有在需要精确判断一个类型是不是某个 class 的时候，我们才使用 == 判断 class 实例

- newInstance()创建此 Class 对象所表示的类的一个新实例

- JVM在执行Java程序的时候，并不是一次性把所有用到的class全部加载到内存，而是第一次需要用到class时才加载，动态加载 class 的特性对于Java程序非常重要。利用JVM动态加载 class 的特性，我们才能在运行期根据条件加载不同的实现类。 JVM为每个加载的 class 及 interface 创建了对应的 Class 实例来保存 class 及 interface 的所有信息；  获取一个 class 对应的 Class 实例后，就可以获取该 class 的所有信息；  通过Class实例获取 class 信息的方法称为反射（Reflection）；  JVM总是动态加载 class ，可以在运行期根据条件来控制加载class。

- Field 成员变量：每个成员变量有类型和值。java.lang.reflect.Field 为我们提供了获取当前对象的成员变量的类型，和重新设值的方法。

  - Field getField(name)：根据字段名（成员变量）获取某个public的filed（包括父类）
  - Field getDeclaredField(name)：根据字段名（成员变量）获取当前类的某个field（不包括父类）
  - Field[] getFields()：获取所有public的field（包括父类）
  - Field[] getDeclaredFields()：获取当前类的所有field（不包括父类）
  - Field.setAccessible(true) 的意思是 ，一律允许访问
  - 如果JVM运行期存在 SecurityManager ，那么它会根据规则进行检查，有可能阻止 setAccessible(true) 
  - Field.get(Object) 获取指定实例的指定字段的值
  - Field.set(Object, Object) 实现的，其中第一个 Object 参数是指定的实例，第二个 Object 参数是待修改的值

- Method 信息

  - Method getMethod(name, Class...) ：获取某个 public 的 Method （包括父类）
  - Method getDeclaredMethod(name, Class...) ：获取当前类的某个 Method （不包括父类）
  - Method[] getMethods() ：获取所有 public 的 Method （包括父类）
  - Method[] getDeclaredMethods() ：获取当前类的所有 Method （不包括父类）
  - 如果获取到的Method表示一个静态方法，调用静态方法时，由于无需指定实例对象，所以invoke 方法传入的第一个参数永远为 null 
  - 调用非public方法，我们通过Method.setAccessible(true) 允许其调用：
  - 使用反射调用方法时，仍然遵循多态原则：即总是调用实际类型的覆写方法（如果存在）

- Constructor对象

  - 调用Class.newInstance()的局限是，它只能调用该类的public无参数构造方法。如果构造方法带有参数，或者不是public，就无法直接通过Class.newInstance()来调用。
  - getConstructor(Class…) ：获取某个 public 的 Constructor ；
  - getDeclaredConstructor(Class…) ：获取某个 Constructor ；
  - getConstructors() ：获取所有 public 的 Constructor ；
  - getDeclaredConstructors() ：获取所有 Constructor 。
  - 注意 Constructor 总是当前类定义的构造方法，和父类无关，因此不存在多态的问题
  - 调用非 public 的 Constructor 时，必须首先通过 setAccessible(true) 设置允许访问

- getSuperclass()获取父类的Class

- getInterfaces()获取interface,只返回当前类直接实现的接口类型，并不包括其父类实现的接口类型：

- 通过 Class 对象的 isAssignableFrom() 方法可以判断一个向上转型是否可以实现。

  ```java
  Integer.class.isAssignableFrom(Number.class); // false，因为Number不能赋值给Integer
  Number.class.isAssignableFrom(Integer.class); // true，因为Integer可以赋值给Number 
  ```

### 3.1.8 注解详解

- @Target 用来约束注解可以应用的地方（如方法、类或字段），其中ElementType是枚举类型

- @Retention用来约束注解的生命周期，分别有三个值，源码级别（source），类文件级别（class）或者运行时级别（runtime）

  - SOURCE：注解将被编译器丢弃（该类型的注解信息只会保留在源码里，源码经过编译后，注解信息会被丢弃，不会保留在编译好的class文件里）
  - CLASS：注解在class文件中可用，但会被VM丢弃（该类型的注解信息会保留在源码里和class文件里，在执行的时候，不会加载到虚拟机中），请注意，当注解未定义Retention值时，默认值是CLASS，如Java内置注解，@Override、@Deprecated、@SuppressWarnning等
  - RUNTIME：注解信息将在运行期(JVM)也保留，因此可以通过反射机制读取注解的信息（源码、class文件和执行的时候都有注解的信息），如SpringMvc中的@Controller、@Autowired、@RequestMapping等。
  - 这3个生命周期分别对应于：Java源文件(.java文件) ---> .class文件 ---> 内存中的字节码。
  - 一般如果需要在运行时去动态获取注解信息，那只能用 RUNTIME 注解，比如@Deprecated使用RUNTIME注解
  - 如果要在编译时进行一些预处理操作，比如生成一些辅助代码（如 ButterKnife），就用 CLASS注解；
  - 如果只是做一些检查性的操作，比如 @Override 和 @SuppressWarnings，使用SOURCE 注解。

- 注解本质是一个继承了Annotation 的特殊接口，所以注解也叫声明式接口

- 元注解是能够用于定义注解的注解

- 自定义注解

  - 新建注解文件, @interface定义注解

  - 添加参数、默认值

  - 用元注解配置注解

    ```java
    @Retention(RetentionPolicy.RUNTIME)
    @Target(ElementType.TYPE)
    public @interface MyReport {
        String name() default "";
        int value() default 0;
    }
    ```

- 自定义注解的读取

  - 通过反射获取自定义注解信息

## 3.2 Java容器（jdk1.8）

### 3.2.1 ArrayList

- ArrayList 是基于数组实现的，所以⽀持快速随机访问

  ```java
  transient Object[] elementData;
  ```

- 数组的默认⼤⼩为 10

  ```java
  private static final int DEFAULT_CAPACITY = 10;
  ```

- ⽤ grow() ⽅法进 ⾏扩容，新容量⼤约是旧容量的 1.5 倍左右，扩容操作需要调⽤ Arrays.copyOf() 把原数组整个复制到新数组中，这个操作代价很⾼，因此最好在 创建 ArrayList 对象时就指定⼤概的容量⼤⼩，减少扩容操作的次数

  ```java
  int newCapacity = oldCapacity + (oldCapacity >> 1);
  elementData = Arrays.copyOf(elementData, newCapacity);
  ```

- 删除元素，需要调⽤ System.arraycopy() 将 index+1 后⾯的元素都复制到 index 位置上

  ```java
  System.arraycopy(elementData, index+1, elementData, index, numMoved);
  ```

- modCount ⽤来记录 ArrayList 结构发⽣变化的次数。结构发⽣变化是指添加或者删除⾄少⼀个元素的所有操作，或者是调整内部数组的⼤⼩，仅仅只是设置元素的值不算结构发⽣变化

### 3.2.2 Vector

- 它的实现与 ArrayList 类似，但是使⽤了 synchronized 进⾏同步

  ```java
  public synchronized boolean add(E e) {
      modCount++;
      ensureCapacityHelper(elementCount + 1);
      elementData[elementCount++] = e;
      return true;
  }
  ```

- Vector 的构造函数可以传⼊ capacityIncrement 参数用来扩容，如果这个参数的值⼩于等于 0，扩容时每次都令 capacity 为原来的两倍。

  ```java
  int newCapacity = oldCapacity + ((capacityIncrement > 0) ? capacityIncrement : oldCapacity);
  ```

- 可以使⽤ Collections.synchronizedList(); 得到⼀个线程安全的 ArrayList

### 3.2.3 CopyOnWriteArrayList

- 写操作在⼀个复制的数组上进⾏，读操作还是在原始数组中进⾏，读写分离，互不影响。

  ```java
  public boolean add(E e) {
      final ReentrantLock lock = this.lock;
      lock.lock();
      try {
          Object[] elements = getArray();
          int len = elements.length;
          Object[] newElements = Arrays.copyOf(elements, len + 1);
          newElements[len] = e;
          setArray(newElements);
          return true;
      } finally {
      	lock.unlock();
      }
  }
  ```

- CopyOnWriteArrayList 在写操作的同时允许读操作，⼤⼤提⾼了读操作的性能，因此很适合读多写少的 应⽤场景

### 3.2.4 LinkedList

- ArrayList 基于动态数组实现，LinkedList 基于双向链表实现。ArrayList 和 LinkedList 的区别可以归结 为数组和链表的区别

### 3.2.5 HashMap

- jdk1.7 数组+链表 | jdk1.8 数组+链表+红黑树

- HashMap 是一种常用的哈希表实现，它将键（key）映射到值（value）上。它使用哈希函数将键映射到哈希表中的索引，以便快速查找键值对。HashMap 的实现基于数组和链表或红黑树，它通过散列函数来确定每个键值对在数组中的位置

  ```java
  //重新计算哈希值
  static final int hash(Object key) {
      int h;
      return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);//key如果是null 新hashcode是0 否则 计算新的hashcode
  }
  ```

- 将h无符号右移16为相当于将高区16位移动到了低区的16位，再与原hashcode做异或运算，可以将高低位二进制特征混合起来

- 在算出hash值之后,计算这个key落在哪一个桶上面,方法有2中,一种是&,一种是%,这两种方法都可行,但是效率不一样,新哈希值在后面将会参与hashmap中数组槽位的计算，计算公式：(n - 1) & hash，

- 异或运算能更好的保留各部分的特征，如果采用&运算计算出来的值会向0靠拢，采用|运算计算出来的值会向1靠拢

- 为了让哈希后的结果更加均匀，槽位数必须使用$2^n$

### 3.2.6 Hashtable

- Hashtable使用synchronized来同步
- HashMap可以插入键为null的Entry
- HashMap的迭代器是fail-fast迭代器
- HashMap不能保证随着时间的推移Map中的元素次序是不变的

### 3.2.7 ConcurrentHashMap

- JDK 1.8 使⽤了 CAS 操作来⽀持更⾼的并发度，在 CAS 操作失败时使⽤内置锁 synchronized。
- 并且 JDK 1.8 的实现也在链表过⻓时会转换为红⿊树

### 3.2.8 LinkedHashMap

- 继承自HashMap，因此具有和HashMap一样的快速查找特性

  ```java
  public class LinkedHashMap<K,V> extends HashMap<K,V> implements Map<K,V> {}
  ```

- 内部维护了⼀个双向链表，⽤来维护插⼊顺序或者 LRU 顺序

  ```java
  	/**
       * The head (eldest) of the doubly linked list.
       */
      transient LinkedHashMap.Entry<K,V> head;
  
      /**
       * The tail (youngest) of the doubly linked list.
       */
      transient LinkedHashMap.Entry<K,V> tail;
  
      /**
       * The iteration ordering method for this linked hash map: <tt>true</tt>
       * for access-order, <tt>false</tt> for insertion-order.
       */
      final boolean accessOrder;
  ```

- LRU是Least Recently Used的缩写，译为最近最少使用。它的理论基础为 “最近使用的数据会在未来一段时期内仍然被使用，已经很久没有使用的数据大概率在未来很长一段时间仍然不会被使用” 由于该思想非常契合业务场景 ，并且可以解决很多实际开发中的问题，所以我们经常通过LRU的思想来作缓存，一般也将其称为LRU缓存机制。

### 3.2.9 WeakHashMap

- WeakHashMap 的 Entry 继承⾃ WeakReference，被 WeakReference 关联的对象在下⼀次垃圾回收时 会被回收。 
- WeakHashMap 主要⽤来实现缓存，通过使⽤ WeakHashMap 来引⽤缓存对象，由 JVM 对这部分缓存 进⾏回收

## 3.3 java并发

### 3.3.1 使用线程

- 实现Runnable接口

  ```java
  public class MyRunnable implements Runnable 
  // 使⽤ Runnable 实例再创建⼀个 Thread 实例，然后调⽤ Thread 实例的 start() ⽅法来启动线程
  Thread thread = new Thread(new MyRunnable());
  thread.start();
  ```

- 实现Callable接口

  ```java
  public class MyCallable implements Callable<Integer>
  // 与 Runnable 相⽐，Callable 可以有返回值，返回值通过 FutureTask 进⾏封装
  FutureTask<Integer> futureTask = new FutureTask<>(new MyCallable());
  Thread thread = new Thread(futureTask);
  thread.start();
  Integer integer = futureTask.get();
  ```

- 继承Thread类

  ```java
  public class MyThread extends Thread
  // 同样也是需要实现 run() ⽅法，因为 Thread 类也实现了 Runable 接⼝
  MyThread myThread = new MyThread();
  myThread.start();
  ```

### 3.3.2 基础线程机制

- Executor

  - CachedThreadPool：⼀个任务创建⼀个线程

    ```java
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(new MyRunnable());
    ```

  - FixedThreadPool：所有任务只能使⽤固定⼤⼩的线程；

    ```java
    ExecutorService executorService1 = Executors.newFixedThreadPool(10);
    executorService1.execute(new MyRunnable());
    ```

  - SingleThreadExecutor：相当于⼤⼩为 1 的 FixedThreadPool。

    ```java
    ExecutorService executorService2 = Executors.newSingleThreadExecutor();
    executorService2.execute(new MyRunnable());
    ```

- Daemon

  - 守护线程是程序运⾏时在后台提供服务的线程，不属于程序中不可或缺的部分

  - 当所有⾮守护线程结束时，程序也就终⽌，同时会杀死所有守护线程。

  - main() 属于⾮守护线程。 在线程启动之前使⽤ setDaemon() ⽅法可以将⼀个线程设置为守护线程

    ```java
    public static void main(String[] args) {
            Thread thread = new Thread(new MyRunnable());
            thread.setDaemon(true);
        	// 随着main方法的终止，该守护线程会被杀死，无法继续执行
            thread.start();
    }
    ```

- sleep()

  - Thread.sleep(millisec) ⽅法会休眠当前正在执⾏的线程，millisec 单位为毫秒
  - sleep() 可能会抛出 InterruptedException，因为异常不能跨线程传播回 main() 中，因此必须在本地进⾏ 处理。线程中抛出的其它异常也同样需要在本地进⾏处理

- yield()

  - 对静态⽅法 Thread.yield() 的调⽤声明了当前线程已经完成了⽣命周期中最重要的部分，可以切换给其 它线程来执⾏。该⽅法只是对线程调度器的⼀个建议，⽽且也只是建议具有相同优先级的其它线程可以 运⾏。简称没啥用

### 3.3.3 中断

- InterruptedException

  - 通过调⽤⼀个线程的 interrupt() 来中断该线程，如果该线程处于阻塞、限期等待或者⽆限期等待状态， 那么就会抛出 InterruptedException，从⽽提前结束该线程。但是不能中断 I/O 阻塞和 synchronized 锁 阻塞

    ```java
    Thread thread = new Thread(() -> {
        try {
            System.out.println("======> run start");
            Thread.sleep(10000L);
            // 此处由于线程睡眠，调用interrupt发生InterruptedException异常，无法继续执行
            System.out.println("======> run end");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    });
    thread.start();
    thread.interrupt();
    System.out.println("====> main end");
    ```

- interrupted()

  - 如果⼀个线程的 run() ⽅法执⾏⼀个⽆限循环，并且没有执⾏ sleep() 等会抛出 InterruptedException 的 操作，那么调⽤线程的 interrupt() ⽅法就⽆法使线程提前结束。

  - 但是调⽤ interrupt() ⽅法会设置线程的中断标记，此时调⽤ interrupted() ⽅法会返回 true。因此可以在 循环体中使⽤ interrupted() ⽅法来判断线程是否处于中断状态，从⽽提前结束线程。

    ```java
    Thread thread = new Thread(() -> {
         while (true) {
             if (Thread.currentThread().isInterrupted()) {
                 break;
             }
             System.out.println("===> 执行中");
         }
    });
    thread.start();
    thread.interrupt();
    ```

- Executor 的中断操作

  - 调⽤ Executor 的 shutdown() ⽅法会等待线程都执⾏完毕之后再关闭，但是如果调⽤的是 shutdownNow() ⽅法，则相当于调⽤每个线程的 interrupt() ⽅法。

    ```java
    ExecutorService executorService = Executors.newCachedThreadPool();
    executorService.execute(() -> {
        while (true) {
            System.out.println("====>1111");
        }
    });
    executorService.execute(() -> {
        while (!Thread.currentThread().isInterrupted()) {
            System.out.println("====>2222");
        }
    });
    executorService.shutdown();
    // 只有====>2222会结束执行
    executorService.shutdownNow();
    ```

  - 如果只想中断 Executor 中的⼀个线程，可以通过使⽤ submit() ⽅法来提交⼀个线程，它会返回⼀个 Future 对象，通过调⽤该对象的 cancel(true) ⽅法就可以中断线程。实际上还是调用的interrupt()方法

    ```java
    ExecutorService executorService = Executors.newCachedThreadPool();
    Future<Object> submit1 = executorService.submit(() -> {
        while (true) {
            System.out.println("====>1111");
        }
    });
    Future<?> submit2 = executorService.submit(() -> {
        while (!Thread.currentThread().isInterrupted()) {
            System.out.println("====>2222");
        }
    });
    submit1.cancel(true);
    // 只有====>2222会结束执行
    submit2.cancel(true);
    ```

### 3.3.4 互斥同步

- synchronized

  - 是 JVM 实现的 synchronized

  - 同步⼀个代码块 

    ```java
    public void func() {
     synchronized (this) {
     // ...
     }
    }
    ```

    - 它只作⽤于同⼀个对象，如果调⽤两个对象上的同步代码块，就不会进⾏同步，this代表当前对象

  - 同步⼀个⽅法

    ```java
    public synchronized void func () {
     // ...
    }
    ```

    - 它和同步代码块⼀样，作⽤于同⼀个对象。类似于使用this同步代码块

  - 同步⼀个类

    ```java
    public void func() {
     synchronized (SynchronizedExample.class) {
     // ...
     }
    }
    ```

    - 作⽤于整个类，也就是说两个线程调⽤同⼀个类的不同对象上的这种同步语句，也会进⾏同步。

  - 同步⼀个静态⽅法

    ```java
    public synchronized static void fun() {
     // ...
    }
    ```

    - 作⽤于整个类

- ReentrantLock

  - JDK 实现的 ReentrantLock;

  - ReentrantLock 是 java.util.concurrent（J.U.C）包中的锁;

  - ```java
    public class LockExample {
         private Lock lock = new ReentrantLock();
         public void func() {
            lock.lock();
            try {
                for (int i = 0; i < 10; i++) {
                    System.out.print(i + " ");
                }
            } finally {
                lock.unlock(); // 确保释放锁，从⽽避免发⽣死锁。
            }
         }
    }
    
    ```

- 比较

  - 锁的实现。synchronized 是 JVM 实现的，⽽ ReentrantLock 是 JDK 实现的。
  - 性能。新版本 Java 对 synchronized 进⾏了很多优化，例如⾃旋锁等，synchronized 与 ReentrantLock ⼤致相同。
  
  - 等待可中断。当持有锁的线程⻓期不释放锁的时候，正在等待的线程可以选择放弃等待，改为处理其他事情。 ReentrantLock 可中断，⽽ synchronized 不⾏。
  - 公平锁。公平锁是指多个线程在等待同⼀个锁时，必须按照申请锁的时间顺序来依次获得锁。 synchronized 中的锁是⾮公平的，ReentrantLock 默认情况下也是⾮公平的，但是也可以是公平的。**可以通过带布尔值的构造函数要求使用公平锁**。
  - 锁绑定多个条件。⼀个 ReentrantLock 可以同时绑定多个 Condition 对象。
  - 除⾮需要使⽤ ReentrantLock 的⾼级功能，否则优先使⽤ synchronized。这是因为 synchronized 是 JVM 实现的⼀种锁机制，JVM 原⽣地⽀持它，⽽ ReentrantLock 不是所有的 JDK 版本都⽀持。并且使 ⽤ synchronized 不⽤担⼼没有释放锁⽽导致死锁问题，因为 JVM 会确保锁的释放。

### 3.3.5 自旋锁

- 是指当一个线程在获取锁的时候，如果锁已经被其它线程获取，那么该线程将循环等待，然后不断的判断锁是否能够被成功获取，直到获取到锁才会退出循环。

- **自旋锁尽可能的减少线程的阻塞，非自旋锁在获取不到锁的时候会进入阻塞状态** ，从而进入内核态，当获取到锁的时候需要从内核态恢复，需要线程上下文切换

- 但是如果锁的竞争激烈，或者持有锁的线程需要长时间占用锁执行同步块，这时候就不适合使用自旋锁了

- 例如CAS的实现

  - CAS，`CAS`是`Compare And Swap`的缩写，直译就是**比较并交换**，一种基于乐观锁的操作，我认为原有的值应该是什么，如果是，则将原有的值更新为新值，否则不做修改，并告诉我原来的值是多少。

  - volatile保证了该属性值的线程可见性。在多并发的情况下，一个线程的修改，可以保证到其他线程立马看到修改后的值。

    ```java
    // var1 表示当前对象，var2表示内存地址，var4表示自增步伐
    public final int getAndAddInt(Object var1, long var2, int var4) {
            int var5;
            do {
                // 把当前对象主内存中的值赋给val5
                var5 = this.getIntVolatile(var1, var2);
                // while循环。判断当前对象此刻主内存中的值是否等于val5，如果是，就自增（交换值），否则继续循环，重新获取val5的值。
                // compareAndSwapInt方法，它是一个native方法，这个方法汇编之后是CPU原语指令，原语指令是连续执行不会被打断的，所以可以保证原子性。
            } while(!this.compareAndSwapInt(var1, var2, var5, var5 + var4));
            return var5;
        }
    ```

- 自旋锁实现

  ```java
  public class MyCASLock {
      private AtomicReference<Thread> cas = new AtomicReference<>();//进入cas的实现类
      public void lock() {
          // 利用CAS
          Thread thread = Thread.currentThread();
          // 当期望值为null时，更新为thread
          while (!cas.compareAndSet(null, thread)) {
              try {
                  Thread.sleep(1000L);
              } catch (InterruptedException e) {
                  e.printStackTrace();
              }
              System.out.println(thread + "============>未获取锁");
          }
          System.out.println(thread + "已获取锁");
      }
      public void unlock() {
          Thread current = Thread.currentThread();
          // 当期望值为thread时，更新为null
          cas.compareAndSet(current, null);
          System.out.println(current.getName() + "已释放锁");
      }
  }
  ```

- TicketLock

  - TicketLock主要解决的是公平性的问题。每当有线程获取锁的时候，就给该线程分配一个递增的id，我们称之为排队号，同时，锁对应一个服务号，每当有线程释放锁，服务号就会递增，此时如果服务号与某个线程排队号一致，那么该线程就获得锁，由于排队号是递增的，所以就保证了最先请求获取锁的线程可以最先获取到锁，就实现了公平性。

    ```java
    public class TicketLock {
        /**
         * 服务号
         */
        private AtomicInteger serviceNum = new AtomicInteger();
        /**
         * 排队号
         */
        private AtomicInteger ticketNum = new AtomicInteger();
        /**
         * 新增一个ThreadLocal，用于存储每个线程的排队号，避免线程排队号被修改
         */
        private ThreadLocal<Integer> ticketNumHolder = new ThreadLocal<Integer>();
        /**
         * lock:获取锁，如果获取成功，返回当前线程的排队号，获取排队号用于释放锁. <br/>
         *
         * @return
         */
        public int lock() {
            int currentTicketNum = ticketNum.incrementAndGet();
            ticketNumHolder.set(currentTicketNum);
            while (currentTicketNum != serviceNum.get()) {
                // Do nothing
            }
            return currentTicketNum;
        }
        /**
         * unlock:释放锁 <br/>
         *
         * @param ticketnum
         */
        public void unlock() {
            
            // 释放锁，从ThreadLocal中获取当前线程的排队号
            Integer currentTickNum = ticketNumHolder.get();
            serviceNum.compareAndSet(ticketnum, ticketnum + 1);
        }
    }
    ```

- CLHLock

  ![image-20231109104015280](images\CLHLock.png)

  - CLH锁是一种基于链表的可扩展、高性能、公平的自旋锁，申请线程只在本地变量上自旋，它不断轮询前驱的状态，如果发现前驱释放了锁就结束自旋，获得锁。

    ```java
    /**
     * CLH的发明人是：Craig，Landin and Hagersten。
     * 代码来源：http://ifeve.com/java_lock_see2/
     */
    public class MyCLHLock {
        /**
         * 定义一个节点，默认的lock状态为true
         */
        public static class CLHNode {
            private volatile boolean isLocked = true;
        }
        /**
         * 尾部节点,只用一个节点即可
         */
        private volatile CLHNode tail;
        private static final ThreadLocal<CLHNode> LOCAL = new ThreadLocal<>();
        private static final AtomicReferenceFieldUpdater<MyCLHLock, CLHNode> UPDATER = AtomicReferenceFieldUpdater.newUpdater(MyCLHLock.class, CLHNode.class,
                "tail");
        public void lock() {
            // 新建节点并将节点与当前线程保存起来
            CLHNode node = new CLHNode();
            LOCAL.set(node);
            // 将新建的节点设置为尾部节点，并返回旧的节点（原子操作），这里旧的节点实际上就是当前节点的前驱节点
            CLHNode preNode = UPDATER.getAndSet(this, node);
            if (preNode != null) {
                // 前驱节点不为null表示当锁被其他线程占用，通过不断轮询判断前驱节点的锁标志位等待前驱节点释放锁
                while (preNode.isLocked) {
                }
                preNode = null;
                LOCAL.set(node);
            }
            // 如果不存在前驱节点，表示该锁没有被其他线程占用，则当前线程获得锁
        }
        public void unlock() {
            // 获取当前线程对应的节点
            CLHNode node = LOCAL.get();
            // 如果tail节点等于node，则将tail节点更新为null，同时将node的lock状态置为false，表示当前线程释放了锁
            if (!UPDATER.compareAndSet(this, node, null)) {
                node.isLocked = false;
            }
            node = null;
        }
    }
    ```

- MCSLock

  

  ![image-20231109112445712](images\MCSLock.png)

  - MCS是一种基于单向链表的高性能、公平的自旋锁。申请加锁的线程通过当前节点的变量进行自旋（locked == true）。在前置节点解锁后，会修改当前节点的锁值（locked ==false），这一刻当前节点会结束自旋，并进行加锁

    ```java
    /**
     * MCS:发明人名字John Mellor-Crummey和Michael Scott
     * 代码来源：http://ifeve.com/java_lock_see2/
     */
    public class MCSLock {
        /**
         * 节点，记录当前节点的锁状态以及后驱节点
         */
        public static class MCSNode {
            volatile MCSNode next;
            volatile boolean isLocked = true;
        }
        private static final ThreadLocal<MCSNode> NODE = new ThreadLocal<MCSNode>();
        // 队列
        @SuppressWarnings("unused")
        private volatile MCSNode queue;
        // queue更新器
        private static final AtomicReferenceFieldUpdater<MCSLock, MCSNode> UPDATER = AtomicReferenceFieldUpdater.newUpdater(MCSLock.class, MCSNode.class,
                "queue");
        public void lock() {
            // 创建节点并保存到ThreadLocal中
            MCSNode currentNode = new MCSNode();
            NODE.set(currentNode);
            // 将queue设置为当前节点，并且返回之前的节点
            MCSNode preNode = UPDATER.getAndSet(this, currentNode);
            if (preNode != null) {
                // 如果之前节点不为null，表示锁已经被其他线程持有
                preNode.next = currentNode;
                // 循环判断，直到当前节点的锁标志位为false
                while (currentNode.isLocked) {
                }
            }
        }
        public void unlock() {
            MCSNode currentNode = NODE.get();
            // next为null表示没有正在等待获取锁的线程
            if (currentNode.next == null) {
                // 更新状态并设置queue为null
                if (UPDATER.compareAndSet(this, currentNode, null)) {
                    // 如果成功了，表示queue==currentNode,即当前节点后面没有节点了
                    return;
                } else {
                    // 如果不成功，表示queue!=currentNode,即当前节点后面多了一个节点，表示有线程在等待
                    // 如果当前节点的后续节点为null，则需要等待其不为null（参考加锁方法）
                    while (currentNode.next == null) {
                    }
                }
            } else {
                // 如果不为null，表示有线程在等待获取锁，此时将等待线程对应的节点锁状态更新为false，同时将当前线程的后继节点设为null
                currentNode.next.isLocked = false;
                currentNode.next = null;
            }
        }
    }
    ```

### 3.3.6 等待可中断

- java.lang.InterruptedException被中止异常，当某个线程处于长时间的等待、休眠或其他暂停状态，而此时其他的线程通过Thread的interrupt方法终止该线程时抛出该异常。
- lock.lockInterruptibly，通过lock.lockInterruptibly()方法获取某个锁时，如果不能获取到，只有进行等待的情况下，是可以响应中断的。
  而用synchronized修饰的话，当一个线程处于等待某个锁的状态，是无法被中断的，只有一直等待下去。

### 3.3.7 ReentrantLock锁绑定多个条件

newCondition、await、signal

```java
ReentrantLock lock = new ReentrantLock();
Condition moneyCondition=lock.newCondition();
Condition ticketCondition=lock.newCondition();
// 等待
moneyCondition.await();
// 唤醒
moneyCondition.signal();
ticketCondition.await();
ticketCondition.signal();
```

### 3.3.8 线程协作

- join()

  - 在线程中调⽤另⼀个线程的 join() ⽅法，会将当前线程挂起，⽽不是忙等待，直到⽬标线程结束。

    ```java
    public static void main(String[] args) throws InterruptedException {
            Thread t1 = new Thread(() -> {
                try {
                    Thread.sleep(10000L);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println("=====> t1执行结束");
            });
            t1.start();
            t1.join();
            System.out.println("======> main执行结束");
        }
    ```

- wait() notify() notifyAll()

  - 调⽤ wait() 在等待时会被挂起，notify() 或者 notifyAll() 来唤醒挂起的线程

  - 它们都属于 Object 的⼀部分，⽽不属于 Thread。 

  - 只能⽤在同步⽅法或者同步控制块中使⽤，否则会在运⾏时抛出 IllegalMonitorStateException。 

  - 使⽤ wait() 挂起期间，线程会释放锁。

  - wait() 是 Object 的⽅法，⽽ sleep() 是 Thread 的静态⽅法, wait() 会释放锁，sleep() 不会

    ```java
    public class MyWait {
        public synchronized void before() {
            try {
                Thread.sleep(10000L);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("before");
            this.notifyAll();
        }
    
        public synchronized void after() {
            try {
                this.wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("after");
        }
    }
    ```

- await() signal() signalAll()

  - java.util.concurrent 类库中提供了 Condition 类来实现线程之间的协调，可以在 Condition 上调⽤ await() ⽅法使线程等待，其它线程调⽤ signal() 或 signalAll() ⽅法唤醒等待的线程，await()也会释放锁

    ```java
    public class MyAwait {
        private Lock lock = new ReentrantLock();
        private Condition condition = lock.newCondition();
    
        public void before() {
            lock.lock();
            try {
                System.out.println("before");
                Thread.sleep(10000L);
                condition.signalAll();
            } catch (InterruptedException e) {
                e.printStackTrace();
            } finally {
                lock.unlock();
            }
        }
    
        public void after() {
            lock.lock();
            try {
                condition.await();
                System.out.println("after");
            } catch (InterruptedException e) {
                e.printStackTrace();
            } finally {
                lock.unlock();
            }
        }
    }
    ```

  - 传统的synchronized和Lock实现等待唤醒通知的约束：

    1. 线程需要获得并持有锁，必须在锁块（synchronized或lock中）
    2. 必须要先等待后唤醒，线程才能够被唤醒

- park() unPark(Thread)

  - LockSupport类可以阻塞当前线程以及唤醒指定被阻塞的线程

    ```java
    public static void main(String[] args) {
            Thread thread = new Thread(() -> {
                System.out.println(Thread.currentThread().getName() + "come in");
                LockSupport.park();
                System.out.println(Thread.currentThread().getName() + "被唤醒");
            });
            thread.start();
            new Thread(() -> {
                LockSupport.unpark(thread);
                System.out.println("唤醒动作");
            }).start();
        }
    ```

  - LockSupport类可以先唤醒线程后阻塞线程

  - unpark获取了一个凭证，之后再调用park方法，就可以名正言顺的凭证消费，故不会阻塞，凭证的数量最多为1，连续调用两次unpark和调用一次unpark效果一样，只会增加一个凭证，调用两次park却需要消费两个凭证，证不够，不能放行。

### 3.3.9 线程状态

- 新建（NEW）

  - 创建后尚未启动

- 可运行（RUNABLE）

  - 正在 Java 虚拟机中运⾏

- 阻塞（BLOCKED）

  - 请求获取 monitor lock 从⽽进⼊ synchronized 函数或者代码块，但是其它线程已经占⽤了该 monitor lock，所以处于阻塞状态。要结束该状态进⼊RUNABLE 需要其他线程释放 monitor lock

- 无限期等待（WAITING）

  - 等待其它线程显式地唤醒

  - 阻塞和等待的区别在于，阻塞是被动的，它是在等待获取 monitor lock。⽽等待是主动的，通过调⽤  Object.wait() 等⽅法进⼊

    | 进入方法                               | 退出方法                             |
    | -------------------------------------- | ------------------------------------ |
    | 没有设置Timeout参数的Object.wait()方法 | Object.notify() / Object.notifyAll() |
    | 没有设置Timeout参数的Thread.join()方法 | 被调用的线程执行完毕                 |
    | LockSupport.park()方法                 | LockSupport.unpatk(Thread)           |

- 限期等待（TIMED_WAITING）

  - ⽆需等待其它线程显式地唤醒，在⼀定时间之后会被系统⾃动唤醒

    | 进入方法                           | 退出方法                                        |
    | ---------------------------------- | ----------------------------------------------- |
    | Thread.sleep()方法                 | 时间结束                                        |
    | 设置Timeout参数的Object.wait()方法 | 时间结束 / Object.notify() / Object.notifyAll() |
    | 设置Timeout参数的Thread.join()方法 | 时间结束 / 被调用的线程执行完毕                 |
    | LockSupport.parkNanos()方法        | 时间结束 / LockSupport.unpatk(Thread)           |
    | LockSupport.parkUntil()方法        | 时间结束 / LockSupport.unpatk(Thread)           |

  - 调⽤ Thread.sleep() ⽅法使线程进⼊限期等待状态时，常常⽤“使⼀个线程睡眠”进⾏描述。调⽤ Object.wait() ⽅法使线程进⼊限期等待或者⽆限期等待时，常常⽤“挂起⼀个线程”进⾏描述。睡眠和挂起是⽤来描述⾏为，⽽阻塞和等待⽤来描述状态。

- 死亡（TERMINATED）

  - 可以是线程结束任务之后⾃⼰结束，或者产⽣了异常⽽结束

### 3.3.10 J.U.C - AQS

java.util.concurrent（J.U.C）⼤⼤提⾼了并发性能，AQS（AbstractQueuedSynchronizer） 被认为是 J.U.C 的核⼼，用于实现基于FIFO等待队列的阻塞锁和相关的同步器

- CountDownLatch

  - ⽤来控制⼀个或者多个线程等待多个线程

  - 维护了⼀个计数器 cnt，每次调⽤ countDown() ⽅法会让计数器的值减 1，减到 0 的时候，那些因为调⽤await()⽅法⽽在等待的线程就会被唤醒

    ```java
    public class MyCountDownLatch {
        public static void main(String[] args) throws InterruptedException {
            int totalThread = 10;
            CountDownLatch countDownLatch = new CountDownLatch(totalThread);
            ExecutorService executorService = Executors.newCachedThreadPool();
            for (int i = 0; i < totalThread; i++) {
                int finalI = i;
                executorService.execute(() -> {
                    System.out.println(Thread.currentThread().getName() + "正在执行中" + finalI);
                    countDownLatch.countDown();
                });
            }
            // 等待其他线程执行 countDownLatch.countDown(); 计数器为0后执行
            countDownLatch.await();
            System.out.println("结束执行");
            executorService.shutdown();
        }
    }
    ```

- CyclicBarrier

  - ⽤来控制多个线程互相等待，只有当多个线程都到达时，这些线程才会继续执⾏

  - CyclicBarrier方法可以循环使用，所以也叫做循环屏障

    ```java
    public class MyCyclicBarrier {
        public static void main(String[] args) {
            CyclicBarrier cyclicBarrier = new CyclicBarrier(5, () -> {
                System.out.println("小猪小猪跑的快");
            });
            for (int i = 0; i < 3; i++) {
                for (int j = 0; j < 5; j++) {
                    int finalI = i;
                    int finalJ = j;
                    new Thread(() -> {
                        System.out.println(finalI + "-" + finalJ + "小猪进场了");
                        try {
                            // 此处等待线程满足上面初始化5次条件才会继续执行
                            cyclicBarrier.await();
                        } catch (InterruptedException e) {
                            e.printStackTrace();
                        } catch (BrokenBarrierException e) {
                            e.printStackTrace();
                        }
                    }).start();
                }
                try {
                    Thread.sleep(1000L);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
    ```

- Semaphore

  - Semaphore 类似于操作系统中的信号量，可以控制对互斥资源的访问线程数。

    ```java
    public class MySemaphore {
        public static void main(String[] args) {
            ExecutorService executorService = Executors.newCachedThreadPool();
            Semaphore semaphore = new Semaphore(2);
            for (int i = 0; i < 10; i++) {
                executorService.execute(() -> {
                    try {
                        // 控制访问线程
                        semaphore.acquire();
                        System.out.println(Thread.currentThread().getName() + "执行中===>");
                        Thread.sleep(3000L);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    } finally {
                        semaphore.release();
                    }
                });
            }
            executorService.shutdown();
        }
    }
    ```

### 3.3.11 J.U.C-其他组件

- FutureTask

  - FutureTask 既可以当做⼀个任务执⾏，也可以有返回值。

    ```java
    public class MyFutureTask {
        public static void main(String[] args) throws Exception {
            FutureTask<Integer> futureTask = new FutureTask<>(() -> {
                int result = 0;
                for (int i = 0; i < 100; i++) {
                    Thread.sleep(10);
                    result += i;
                }
                return result;
            });
            Thread thread = new Thread(futureTask);
            thread.start();
    
            Thread thread1 = new Thread(() -> {
                System.out.println("other task is running...");
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            });
            thread1.start();
            System.out.println(futureTask.get());
        }
    }
    ```

- BlockingQueue

  - FIFO队列 LinkedBlockingQueue ArrayBlockingQueue
  - 优先级队列 PriorityBlockingQueue
  - 提供了阻塞的 take() 和 put() ⽅法：如果队列为空 take() 将阻塞，直到队列中有内容；如果队列为满 put() 将阻塞，直到队列有空闲位置。

- ForkJoin

  - 主要⽤于并⾏计算中，和 MapReduce 原理类似，都是把⼤的计算任务拆分成多个⼩任务并⾏计算。

  - ForkJoin 使⽤ ForkJoinPool 来启动，它是⼀个特殊的线程池，线程数量取决于 CPU 核数。

    ```java
    public class MyForkJoin extends RecursiveTask<Integer> {
    
        private final int threshold = 5;
        private int first;
        private int last;
    
        public MyForkJoin(int first, int last) {
            this.first = first;
            this.last = last;
        }
    
        @Override
        protected Integer compute() {
            int result = 0;
            if (last - first <= threshold) {
                for (int i = first; i <= last; i++) {
                    result += i;
                }
            } else {
                int middle = first + (last - first) / 2;
                MyForkJoin myForkJoin1 = new MyForkJoin(first, middle);
                MyForkJoin myForkJoin2 = new MyForkJoin(middle + 1, last);
                myForkJoin1.fork();
                myForkJoin2.fork();
                result += myForkJoin1.join() + myForkJoin2.join();
            }
            return result;
        }
    
        public static void main(String[] args) throws ExecutionException, InterruptedException {
            MyForkJoin myForkJoin = new MyForkJoin(1, 10000);
            ForkJoinPool forkJoinPool = new ForkJoinPool();
            ForkJoinTask<Integer> submit = forkJoinPool.submit(myForkJoin);
            System.out.println(submit.get());
        }
    }
    ```


### 3.3.12 内存模型

![image-20231113095432462](images\workStore.png)

- 所有的变量都存储在主内存中，每个线程还有⾃⼰的⼯作内存，⼯作内存存储在⾼速缓存或者寄存器中，保存了该线程使⽤的变量的主内存副本拷⻉。
- 线程只能直接操作⼯作内存中的变量，不同线程之间的变量值传递需要通过主内存来完成。

![image-20231113095558978](images\workModel.png)

- 内存模型操作
  - read：把⼀个变量的值从主内存传输到⼯作内存中
  - load：在 read 之后执⾏，把 read 得到的值放⼊⼯作内存的变量副本中
  - use：把⼯作内存中⼀个变量的值传递给执⾏引擎
  - assign：把⼀个从执⾏引擎接收到的值赋给⼯作内存的变量
  - store：把⼯作内存的⼀个变量的值传送到主内存中
  - write：在 store 之后执⾏，把 store 得到的值放⼊主内存的变量中
  - lock：作⽤于主内存的变量
  - unlock

- 原子性
  - 原子性是指一个操作是不可中断的。即使在多个线程一起执行的时候，一个操作一旦开始，就不会被其他线程干扰。
  - Java 内存模型保证了 read、load、use、assign、store、write、lock 和 unlock 操作具有原⼦性
  - 可以使用原子类，或者 synchronized 互斥锁
- 可见性
  - 可⻅性指当⼀个线程修改了共享变量的值，其它线程能够⽴即得知这个修改
  - Java 内存模型是通过在变 量修改后将新值同步回主内存，在变量读取前从主内存刷新变量值来实现可⻅性的
  - volatile，synchronized ，final修饰
- 有序性
  - 在本线程内观察，所有操作都是有序的。在⼀个线程观察另⼀个线程，所有操作都是⽆序的，⽆序是因为发⽣了指令重排序。
  - 重排序过程不会影响到单线程程序的执⾏，却会影响到多线程并发执⾏的正确性。
  - volatile 关键字通过添加内存屏障的⽅式来禁⽌指令重排，即重排序时不能把后⾯的指令放到内存屏障之前
  - 也可以通过 synchronized 来保证有序性，它保证每个时刻只有⼀个线程执⾏同步代码，相当于是让线程顺序执⾏同步代码。

### 3.3.13 线程安全

- 不可变
  - 不可变的对象一定是线程安全的，不需要再采取任何线程安全保障措施
- 互斥同步
  - synchronized 和 ReentrantLock。
- 非阻塞同步
  - 互斥同步最主要的问题就是线程阻塞和唤醒所带来的性能问题，因此这种同步也称为阻塞同步
  - 先进⾏操作，如果没有其它线程争⽤共享数据，那操作就成功了，否则采取补偿措施（不断地重试，直到成功为⽌），这种乐观的并发策略的许多实现都不需要将线程阻塞，因此这种同步操作称为⾮阻塞同步。
  - CAS
    - 硬件⽀持的原⼦性操作最典型的是：⽐较并交换（Compare-and-Swap，CAS）
    - CAS 指令需要有3个操作数，分别是内存地址V、旧的预期值A和新值 B。当执⾏操作时，只有当V 的值等于 A，才将V的值更新为B
  - AtomicInteger
  - ABA
    - 如果⼀个变量初次读取的时候是 A 值，它的值被改成了 B，后来⼜被改回为 A，那 CAS 操作就会误认为它从来没有被改变过。
    - J.U.C 包提供了⼀个带有标记的原⼦引⽤类 AtomicStampedReference 来解决这个问题，它可以通过控制变量值的版本来保证 CAS 的正确性。
- ⽆同步⽅案
  - 如果⼀个⽅法本来就不涉及共享数据，那它⾃然就⽆须任何同步措施去保证正确性
  - 栈封闭
    - 多个线程访问同⼀个⽅法的局部变量时，不会出现线程安全问题，因为局部变量存储在虚拟机栈中，属 于线程私有的
  - 线程本地存储（Thread Local Storage）
    - 可以把共享数据的可⻅范围限制在同⼀个线程之内
    - ThreadLocal
  - 可重入代码
    - 这种代码也叫做纯代码（Pure Code），可以在代码执⾏的任何时刻中断它，转⽽去执⾏另外⼀段代码 （包括递归调⽤它本身），⽽在控制权返回后，原来的程序不会出现任何错误。
    - 如不依赖存储在堆上的数据和公⽤的系统资源、⽤到的状态量都由参数中传⼊、不调⽤⾮可重⼊的⽅法等。

### 3.3.14 synchronized锁优化

- 自旋锁
  - ⾃旋锁的思想是让⼀个线程在请求⼀个共享数据的锁时执⾏忙循环（⾃旋）⼀段时间， 如果在这段时间内能获得锁，就可以避免进⼊阻塞状态。
- 锁消除
  - 锁消除是指对于被检测出不可能存在竞争的共享数据的锁进⾏消除。
- 锁粗化
  - 如果⼀系列的连续操作都对同⼀个对象反复加锁和解锁，虚拟机探测到由这样的⼀串零碎的操作都对同⼀个对象加锁，将会把加锁的范围扩展（粗化）到整个操作序列的外部。
- 轻量级锁
  - 轻量级锁是相对于传统的重量级锁⽽⾔，它使⽤ CAS 操作来避免重量级锁使⽤互斥量的开销。对于绝⼤部分的锁，在整个同步周期内都是不存在竞争的，因此也就不需要都使⽤互斥量进⾏同步，可以先采 ⽤ CAS 操作进⾏同步，如果 CAS 失败了再改⽤互斥量进⾏同步
  - ⽆锁状态（unlocked）、偏向锁状态 （biasble）、轻量级锁状态（lightweight locked）和重量级锁状态（inflated）。
- 偏向锁
  - 偏向锁的思想是偏向于让第⼀个获取锁对象的线程，这个线程在之后获取该锁就不再需要进⾏同步操 作，甚⾄连 CAS 操作也不再需要。
  - 当有另外⼀个线程去尝试获取这个锁对象时，偏向状态就宣告结束，此时撤销偏向（Revoke Bias）后 恢复到未锁定状态或者轻量级锁状态。

### 3.3.15 多线程良好规约

- 给线程起个有意义的名字，这样可以⽅便找 Bug
- 缩⼩同步范围，从⽽减少锁争⽤。例如对于 synchronized，应该尽量使⽤同步块⽽不是同步⽅法
- 多⽤同步⼯具少⽤ wait() 和 notify()。⾸先，CountDownLatch, CyclicBarrier, Semaphore 和 Exchanger 这些同步类简化了编码操作，⽽⽤ wait() 和 notify() 很难实现复杂控制流
- 使⽤ BlockingQueue 实现⽣产者消费者问题。
- 多⽤并发集合少⽤同步集合，例如应该使⽤ ConcurrentHashMap ⽽不是 Hashtable
- 使⽤本地变量和不可变类来保证线程安全
- 使⽤线程池⽽不是直接创建线程，这是因为创建线程代价很⾼，线程池可以有效地利⽤有限的线程来启动任务。

## 3.4 Java虚拟机

![image-20231113135139499](images\virtualMachine.png)

### 3.4.1 数据区域

- 程序计数器
  - 记录正在执行的虚拟机字节码指令的地址（如果正在执行的是本地方法则为空）
- java虚拟机栈
  - 每个java方法在执行的同时会创建一个栈帧用于存储局部变量表，操作数栈，常量池引用等信息
  - 可以通过 -Xss 这个虚拟机参数来指定每个线程的 Java 虚拟机栈内存⼤⼩，在 JDK 1.4 中默认为 256K，⽽在 JDK 1.5+ 默认为 1M：
    - java -Xss2M HackTheJava
- 本地⽅法栈
  - 本地⽅法栈为本地⽅法服务
  - 本地⽅法⼀般是⽤其它语⾔（C、C++ 或汇编语⾔等）编写的，并且被编译为基于本机硬件和操作系统 的程序，对待这些⽅法需要特别处理
- 堆
  - 所有对象都在这⾥分配内存，是垃圾收集的主要区域（"GC 堆"）。
    - 新⽣代（Young Generatio）
      - 新生代中一般保存新出现的对象，所以每次垃圾收集时都发现大批对象死去，只有少量对象存活，便采用了**复制算法**，只需要付出少量存活对象的复制成本就可以完成收集
    - ⽼年代（Old Generation）
      - 老年代中一般保存存活了很久的对象，他们存活率高、没有额外空间对它进行分配担保，就必须采用“**标记-清理**”或者“**标记-整理**”算法
    - 永久代（java8永久代已经被移除，被一个称为“元数据区”（元空间）的区域所取代）
      - 元空间并不在虚拟机中，而是使用本地内存。因此，默认情况下，元空间的大小仅受本地内存限制
  - 可以通过 -Xms 和 -Xmx 这两个虚拟机参数来指定⼀个程序的堆内存⼤⼩，第⼀个参数设置初始值，第 ⼆个参数设置最⼤值
    - java -Xms1M -Xmx2M HackTheJava
- 方法区
  - ⽤于存放已被加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。
- 运行时常量池
  - Class ⽂件中的常量池（编译器⽣成的字⾯量和符号引⽤）会在类加载后被放⼊这个区域。
  - 除了在编译期⽣成的常量，还允许动态⽣成，
- 直接内存
  - NIO 类，可以使⽤ Native 函数库直接分配堆外内存，然后通过 Java 堆⾥的 DirectByteBuffer 对象作为这块内存的引⽤进⾏操作，这样能在⼀些场景中显著提⾼性能，因为避免了 在堆内存和堆外内存来回拷⻉数据。

### 3.4.2 垃圾收集

- 引用计数算法

  - 为对象添加⼀个引⽤计数器，当对象增加⼀个引⽤时计数器加 1，引⽤失效时计数器减 1。引⽤计数为 0 的对象可被回收
  - 循环引⽤，引⽤计数器永远不为 0。

- 可达性分析算法

  - 以 GC Roots 为起始点进⾏搜索，可达的对象都是存活的，不可达的对象可被回收

    - 在虚拟机栈(栈帧中的本地变量表)中引用的对象

      ```java
      public class Test1 {
       
          public static void main(String[] args) {
              // test1是栈帧中本地变量，test1为虚拟机栈所引用的对象，可作为GC Roots根对象
              Test1 test1 = new Test1();
          }
       
      }
      ```

    - 在方法区类静态属性引用的对象，比如Java类的引用类型的静态变量

      ```java
      
      public class Test2 {
       	// test1是方法区类静态属性引用的对象
          static Test1 test1 ;
       
          public static void main(String[] args) {
              test1 = new Test1();
          }
       
      }
      ```

    - 在方法区中常量引用的对象，比如字符串常量池里的引用

      ```java
      
      public class Test3 {
       	// 在方法区中常量引用的对象，比如字符串常量池里的引用
          static final Test1 test1 = new Test1() ;
       
          public static void main(String[] args) {
              System.out.println(test1);
          }
       
      }
      ```

    - 在本地方法栈中JNI(Native方法)引用的对象

- 方法区的回收

  - ⽅法区主要存放永久代对象，主要是对常量池的回收和对类的卸载
  - 类的卸载条件
    - 该类所有的实例都已经被回收，此时堆中不存在该类的任何实例。
    - 加载该类的 ClassLoader 已经被回收。
    - 该类对应的 Class 对象没有在任何地⽅被引⽤，也就⽆法在任何地⽅通过反射访问该类⽅法

- finalize()

  - 类似 C++ 的析构函数，⽤于关闭外部资源，⽆法保证各个对象的调⽤顺序，因此最好不要使用。

### 3.4.3 引用类型

- 强引⽤

  - 被强引⽤关联的对象不会被回收，除非手动设置为null，或者离开作用域

    ```java
    // 使⽤ new ⼀个新对象的⽅式来创建强引用
    Object obj = new Object();
    ```

- 软引用

  - 被软引⽤关联的对象只有在内存不够的情况下才会被回收。

    ```java
    Object obj = new Object();
    // 使⽤ SoftReference 类来创建软引⽤
    SoftReference<Object> sf = new SoftReference<Object>(obj);
    obj = null; // 使对象只被软引⽤关联
    ```

-  弱引⽤

  - 被弱引⽤关联的对象⼀定会被回收，也就是说它只能存活到下⼀次垃圾回收发⽣之前。

    ```java
    Object obj = new Object();
    // 使⽤ WeakReference 类来创建弱引⽤
    WeakReference<Object> wf = new WeakReference<Object>(obj);
    obj = null;
    ```

- 虚引⽤

  - ⼜称为幽灵引⽤或者幻影引⽤，⼀个对象是否有虚引⽤的存在，不会对其⽣存时间造成影响，也⽆法通过虚引⽤得到⼀个对象

    ```java
    Object obj = new Object();
    // 使⽤ PhantomReference 来创建虚引⽤。
    PhantomReference<Object> pf = new PhantomReference<Object>(obj, null);
    obj = null;
    ```

### 3.4.4 垃圾收集算法

- 标记-清除算法
  - 标记-清除算法由两个阶段组成，分别是标记和清除。在标记阶段，JVM遍历所有可访问的对象，并打上标记；而在清除阶段，JVM将没有标记的对象视为垃圾，并回收其占用的内存空间。
  - 标记和清除过程效率都不⾼，会产⽣⼤量不连续的内存碎⽚，导致⽆法给⼤对象分配内存。
- 标记-整理算法
  - 标记-整理算法（Mark-Compact）也是将内存垃圾分为两类，即已使用和未使用的对象，但与标记-清除算法不同的是，在整理阶段，标记-整理算法将存活的对象集中到一端，然后清除掉另一端的所有未使用的空间。
  - 不会产⽣内存碎⽚，需要移动⼤量对象，处理效率⽐较低
- 复制算法
  - 复制算法是最早的垃圾回收算法之一，它的基本思路是将可用内存空间分为两个相等的区域，每次只使用其中一个区域，当一个区域用尽后，将所有还存活的对象复制到另一个空闲区域中，然后清除原先的区域中所有的对象。通过反复地执行这个过程，可以保持内存的整洁并避免内存碎片问题。
  - 在Java中，复制算法通常被用于实现新生代的垃圾回收器。新生代包含Eden空间、两个Survivor空间和老年代。当Eden空间被用尽时，JVM会将其中的存活对象复制到一个Survivor空间中，并清空Eden空间。经过多次垃圾回收之后，存活时间较长的对象将逐渐被移动到另一个Survivor空间中，并最终被复制到老年代中。
- 分代算法
  - 将对象按照年龄分为不同的代，然后使用不同的垃圾回收算法来处理不同代的对象。
  - 在 JVM 中，一般将堆分为年轻代和老年代。年轻代包括一个 Eden 区和两个 Survivor 区，新创建的对象首先被分配到 Eden 区，如果 Eden 区没有足够的空间，就会触发一次 Minor GC，此时存活的对象会被复制到其中一个 Survivor 区，另外一个 Survivor 区则被清空。当某个 Survivor 区被充满时，存活下来的对象则会被复制到老年代中，当老年代也满了，就会触发一次 Full GC。
  - 可以通过快速、频繁的 Minor GC 来减少 Full GC 的次数，从而进一步提高程序的性能。

### 3.4.5 垃圾收集器

- JVM client模式和Server模式区别
  - JVM工作在Server模式下可以大大提高性能，Server模式下应用的启动速度会比client模式慢大概10%，但运行速度比Client VM要快至少有10倍；
  - 当JVM用于启动GUI界面的交互应用时适合于使用client模式，当JVM用于运行服务器后台程序时建议用Server模式
  - server:启动慢，编译更完全，编译器是自适应编译器，效率高，针对服务端应用优化，在服务器环境中最大化程序执行速度而设计。
  - client:快速启动，内存占用少，编译快，针对桌面应用程序优化，为在客户端环境中减少启动时间而优化。

- Serial收集器(新生代)

  - 是一个新生代收集器，它以串⾏的⽅式执⾏，是单线程的收集器，使用复制算法，只会使⽤⼀个线程进⾏垃圾收集⼯作，在单个 CPU 环境下，由于没有线程交互的开销，因此拥有最⾼的单线程收集效率，Serial收集器是 Jvm client 模式下默认的新生代收集器。

-  ParNew 收集器(新生代)

  - 它是 Serial 收集器的多线程版本。使用复制算法，是年轻代的垃圾收集器， 它是 Server 场景下默认的新⽣代收集器，除了性能原因外，主要是因为除了 Serial 收集器，只有它能 与 CMS 收集器配合使⽤
  - 默认开启的垃圾收集器线程数就是CPU数量，可通过 `-XX:ParallelGCThreads=m` 参数来限制收集器线程数。

-  Parallel Scavenge 收集器(新生代)

  - 与 ParNew ⼀样是多线程收集器，“吞吐量优先”收集器。这⾥的吞吐量指 CPU ⽤于运⾏⽤户程序的时间占总时间的比值，吞吐量 = 程序运行时间/(程序运行时间 + 垃圾收集时间)

  - 使用复制算法；

  - 吞吐量控制

    - 最大垃圾收集器停顿时间（-XX：MaxGCPauseMillis 大于0的毫秒数，停顿时间小了就要牺牲相应的吞吐量和新生代空间）
    - 设置吞吐量大小（-XX：GCTimeRatio 大于0小于100的整数，默认99，也就是允许最大1%的垃圾回收时间）

  - 停顿时间越短就越适合需要与⽤户交互的程序，良好的响应速度能提升⽤户体验。⽽⾼吞吐量则可以⾼效率地利⽤ CPU 时间，尽快完成程序的运算任务，适合在后台运算⽽不需要太多交互的任务。

  - 缩短停顿时间是以牺牲吞吐量和新⽣代空间来换取的：新⽣代空间变⼩，垃圾回收变得频繁，导致吞吐量下降

  - 可以通过⼀个开关参数打开 GC ⾃适应的调节策略（GC Ergonomics）

    ```
    开启：-XX:+UseAdaptiveSizePolicy
    关闭：-XX:-UseAdaptiveSizePolicy
    ```

- Serial Old收集器(老年代)

  - Serial Old 收集器是 Serial 收集器的老年代版本，它同样使用一个单线程执行收集，使用“标记-整理”算法
  - 主要使用在Client模式下的虚拟机

- Parallel Old 收集器(老年代)

  - Parallel Old 是 Parallel Scavenge 收集器的老年代版本，使用多线程和“标记-整理”算法，

- CMS收集器(老年代)

  - CMS（Concurrent Mark Sweep），Mark Sweep 指的是标记 - 清除算法。
  - 四个流程
    - 初始标记：仅仅只是标记⼀下 GC Roots 能直接关联到的对象，速度很快，需要停顿
    - 并发标记：进⾏ GC Roots Tracing 的过程，它在整个回收过程中耗时最⻓，不需要停顿
    - 重新标记：为了修正并发标记期间因⽤户程序继续运作⽽导致标记产⽣变动的那⼀部分对象的标记 记录，需要停顿
    - 并发清除：不需要停顿
  - 缺点
    - 吞吐量低：低停顿时间是以牺牲吞吐量为代价的，导致 CPU 利⽤率不够⾼
    - ⽆法处理浮动垃圾，可能出现 Concurrent Mode Failure。浮动垃圾是指并发清除阶段由于⽤户线程继续运⾏⽽产⽣的垃圾，这部分垃圾只能到下⼀次 GC 时才能进⾏回收。
    - 标记 - 清除算法导致的空间碎⽚，往往出现⽼年代空间剩余，但⽆法找到⾜够⼤连续空间来分配当 前对象，不得不提前触发⼀次 Full GC

- G1收集器

  - G1（Garbage-First），它是⼀款⾯向服务端应⽤的垃圾收集器，在多 CPU 和⼤内存的场景下有很好的 性能
  - 堆被分为新⽣代和⽼年代，其它收集器进⾏收集的范围都是整个新⽣代或者⽼年代，⽽ G1 可以直接对 新⽣代和⽼年代⼀起回收。
  - G1 把堆划分成多个⼤⼩相等的独⽴区域（Region），新⽣代和⽼年代不再物理隔离。
  - 流程
    - 初始标记
    - 并发标记
    - 最终标记：为了修正在并发标记期间因⽤户程序继续运作⽽导致标记产⽣变动的那⼀部分标记记 录，虚拟机将这段时间对象变化记录在线程的 Remembered Set Logs ⾥⾯，最终标记阶段需要把 Remembered Set Logs 的数据合并到 Remembered Set 中。这阶段需要停顿线程，但是可并⾏执 ⾏。
    - 筛选回收：⾸先对各个 Region 中的回收价值和成本进⾏排序，根据⽤户所期望的 GC 停顿时间来 制定回收计划。此阶段其实也可以做到与⽤户程序⼀起并发执⾏，但是因为只回收⼀部分 Region， 时间是⽤户可控制的，⽽且停顿⽤户线程将⼤幅度提⾼收集效率
  - 空间整合：整体来看是基于“标记 - 整理”算法实现的收集器，从局部（两个 Region 之间）上来看是 基于“复制”算法实现的，这意味着运⾏期间不会产⽣内存空间碎⽚
  - 可预测的停顿：能让使⽤者明确指定在⼀个⻓度为 M 毫秒的时间⽚段内，消耗在 GC 上的时间不得 超过 N 毫秒。

### 3.4.6 内存分配与回收策略

- Minor GC和Full GC
  - Minor GC：回收新⽣代，因为新⽣代对象存活时间很短，因此 Minor GC 会频繁执⾏，执⾏的速度 ⼀般也会⽐较快。
  - Full GC：回收⽼年代和新⽣代，⽼年代对象其存活时间⻓，因此 Full GC 很少执⾏，执⾏速度会⽐ Minor GC 慢很多
- 内存分配策略
  1. 对象优先在 Eden 分配
     - ⼤多数情况下，对象在新⽣代 Eden 上分配，当 Eden 空间不够时，发起 Minor GC
  2. ⼤对象直接进⼊⽼年代
     - -XX:PretenureSizeThreshold，⼤于此值的对象直接在⽼年代分配，避免在 Eden 和 Survivor 之间的⼤ 量内存复制
  3. ⻓期存活的对象进⼊⽼年代
     - 为对象定义年龄计数器，对象在 Eden 出⽣并经过 Minor GC 依然存活，将移动到 Survivor 中，年龄就 增加 1 岁，增加到⼀定年龄则移动到⽼年代中。 -XX:MaxTenuringThreshold ⽤来定义年龄的阈值
  4. 动态对象年龄判定
     - 如果在 Survivor 中相同年龄所有对象⼤⼩的总和⼤于 Survivor 空间的⼀半，则年龄⼤于或等于该年龄的对象可以直接进 ⼊⽼年代，⽆需等到 MaxTenuringThreshold 中要求的年龄。
  5. 空间分配担保
     - 在发⽣ Minor GC 之前，虚拟机先检查⽼年代最⼤可⽤的连续空间是否⼤于新⽣代所有对象总空间，如 果条件成⽴的话，那么 Minor GC 可以确认是安全的
     - 如果不成⽴的话虚拟机会查看 HandlePromotionFailure 的值是否允许担保失败，如果允许那么就会继续 检查⽼年代最⼤可⽤的连续空间是否⼤于历次晋升到⽼年代对象的平均⼤⼩，如果⼤于，将尝试着进⾏ ⼀次 Minor GC；如果⼩于，或者 HandlePromotionFailure 的值不允许冒险，那么就要进⾏⼀次 Full GC
- Full GC 的触发条件
  - 调⽤ System.gc()，虚拟机不⼀定真正去执⾏，不建议使用
  - ⽼年代空间不足
  - 空间分配担保失败
  - JDK 1.7 及以前的永久代空间不⾜
  - Concurrent Mode Failure
    - 执⾏ CMS GC 的过程中同时有对象要放⼊⽼年代，⽽此时⽼年代空间不⾜（可能是 GC 过程中浮动垃 圾过多导致暂时性的空间不⾜），便会报 Concurrent Mode Failure 错误，并触发 Full GC。

### 3.4.7 类加载机制

- 类是在运⾏期间第⼀次使⽤时动态加载的，⽽不是⼀次性加载所有类。因为如果⼀次性加载，那么会占 ⽤很多的内存

- 类的⽣命周期

  ![image-20231113164951759](images\classTime.png)

  - 加载（Loading） 
  - 验证（Verification） 
  - 准备（Preparation） 
  - 解析（Resolution）
  - 初始化（Initialization） 
  - 使⽤（Using）
  - 卸载（Unloading）

- 类加载过程

  - 包含了加载、验证、准备、解析和初始化这 5 个阶段

  - 加载

    - 通过类的完全限定名称获取定义该类的⼆进制字节流。
    - 将该字节流表示的静态存储结构转换为⽅法区的运⾏时存储结构。
    - 在内存中⽣成⼀个代表该类的 Class 对象，作为⽅法区中该类各种数据的访问⼊⼝
    - ⼆进制字节流获取方式
      1. 从 ZIP 包读取，成为 JAR、EAR、WAR 格式的基础
      2. 从⽹络中获取，最典型的应⽤是 Applet
      3. 运⾏时计算⽣成，例如动态代理技术，在 java.lang.reflect.Proxy 使⽤ ProxyGenerator.generateProxyClass 的代理类的⼆进制字节流
      4. 其他⽂件⽣成，例如由 JSP ⽂件⽣成对应的 Class 类

  - 验证

    - 确保 Class ⽂件的字节流中包含的信息符合当前虚拟机的要求，并且不会危害虚拟机⾃身的安全

  -  准备

    - 类变量是被 static 修饰的变量，准备阶段为类变量分配内存并设置初始值，使⽤的是⽅法区的内存。
    - 实例变量不会在这阶段分配内存，它会在对象实例化时随着对象⼀起被分配在堆中。应该注意到，实例化不是类加载的⼀个过程，类加载发⽣在所有实例化操作之前，并且类加载只进⾏⼀次，实例化可以进 ⾏多次。

  - 解析

    - 将常量池的符号引⽤替换为直接引⽤的过程
    - 其中解析过程在某些情况下可以在初始化阶段之后再开始，这是为了⽀持 Java 的动态绑定

  -  初始化

    - 初始化阶段才真正开始执⾏类中定义的 Java 程序代码。初始化阶段是虚拟机执⾏类构造器<clinit>() ⽅ 法的过程，根据程序员通过程序制定的主观计划去初始化类变量和其它资源

    - <clinit>() 是由编译器⾃动收集类中所有类变量的赋值动作和静态语句块中的语句合并产⽣的，编译器收集的顺序由语句在源⽂件中出现的顺序决定。特别注意的是，静态语句块只能访问到定义在它之前的类变量，定义在它之后的类变量只能赋值，不能访问。

      ```java
      public class Test {
       	static {
       		i = 0; // 给变量赋值可以正常编译通过
       		System.out.print(i); // 这句编译器会提示“⾮法向前引⽤”
       	}
       	static int i = 1;
      }
      ```

    - 由于⽗类的 () ⽅法先执⾏，也就意味着⽗类中定义的静态语句块的执⾏要优先于⼦类。

      ```java
      public class MyParentSub {
          static class Parent {
              public static int A = 1;
              static {
                  A = 2;
              }
          }
      
          static class Sub extends Parent {
              public static int B = A;
          }
      
          public static void main(String[] args) {
              System.out.println(Sub.B); // 2
          }
      }
      ```

    - 接⼝中不可以使⽤静态语句块，但仍然有类变量初始化的赋值操作，因此接⼝与类⼀样都会生成<clinit>() ⽅ 法

    - 执⾏接⼝的<clinit> () ⽅法不需要先执⾏⽗接⼝的<clinit> () ⽅ 法。只有当⽗接⼝中定义的变量使⽤时，⽗接⼝才会初始化。另外，接⼝的实现类在初始化时也⼀样不 会执⾏接⼝的<clinit> () ⽅法

    - 虚拟机会保证⼀个类的 <clinit>() ⽅法在多线程环境下被正确的加锁和同步，如果多个线程同时初始化⼀ 个类，只会有⼀个线程执⾏这个类的<clinit> () ⽅法，其它线程都会阻塞等待，直到活动线程执⾏ <clinit>() ⽅法完毕。如果在⼀个类的 <clinit>() ⽅法中有耗时的操作，就可能造成多个线程阻塞，在实际过程中此种阻塞很隐蔽。

### 3.4.8 类初始化时机

- 主动引用

  - 规范严格规定了有且只有下列五种情况必须对类进⾏ 初始化（加载、验证、准备都会随之发⽣）
  - 遇到 new、getstatic、putstatic、invokestatic 这四条字节码指令时，如果类没有进⾏过初始化，则 必须先触发其初始化。
    - new：使⽤ new 关键字实例化对象的时候
    - getstatic、putstatic：读取或设置⼀个类的静态字段（被 final 修饰、已在编译期把结果放⼊常量池的静态字段除外）的时候；
    - invokestatic ：及调⽤⼀个类的静态⽅法的时候
  - 使⽤ java.lang.reflect 包的⽅法对类进⾏反射调⽤的时候，如果类没有进⾏初始化，则需要先触发 其初始化
  - 当初始化⼀个类的时候，如果发现其⽗类还没有进⾏过初始化，则需要先触发其⽗类的初始化
  - 当虚拟机启动时，⽤户需要指定⼀个要执⾏的主类（包含 main() ⽅法的那个类），虚拟机会先初始化这个主类
  - 使⽤ JDK 1.7 的动态语⾔⽀持时，如果⼀个 java.lang.invoke.MethodHandle 实例最后的解析结果为REF_getStatic, REF_putStatic, REF_invokeStatic 的⽅法句柄，并且这个⽅法句柄所对应的类 没有进⾏过初始化，则需要先触发其初始化。

- 被动引用

  - 以上 5 种场景中的⾏为称为对⼀个类进⾏主动引⽤。除此之外，所有引⽤类的⽅式都不会触发初始化， 称为被动引⽤。

  - 通过⼦类引⽤⽗类的静态字段，不会导致⼦类初始化

    ```java
    System.out.println(SubClass.value); // value 字段在 SuperClass 中定义
    ```

  - 通过数组定义来引⽤类，不会触发此类的初始化。该过程会对数组类进⾏初始化，数组类是⼀个由 虚拟机⾃动⽣成的、直接继承⾃ Object 的⼦类，其中包含了数组的属性和⽅法。

    ```java
    SuperClass[] sca = new SuperClass[10];
    ```

  - 常量在编译阶段会存⼊调⽤类的常量池中，本质上并没有直接引⽤到定义常量的类，因此不会触发 定义常量的类的初始化。

    ```java
    System.out.println(ConstClass.HELLOWORLD);
    ```

- 对象相等

  - 两个对象相等，需要类本身相等，并且使⽤同⼀个类加载器进⾏加载。这是因为每⼀个类加载器都拥有⼀ 个独⽴的类名称空间，这⾥的相等，包括类的 Class 对象的 equals() ⽅法、isAssignableFrom() ⽅法、isInstance() ⽅法的返回 结果为 true，也包括使⽤ instanceof 关键字做对象所属关系判定结果为 true

- 类加载器分类

  - Java虚拟机角度

    - 启动类加载器（Bootstrap ClassLoader），使⽤ C++ 实现，是虚拟机⾃身的⼀部分
    - 所有其它类的加载器，使⽤ Java 实现，独⽴于虚拟机，继承⾃抽象类 java.lang.ClassLoader

  - Java开发人员角度

    - 启动类加载器（Bootstrap ClassLoader）此类加载器负责将存放在<JRE_HOME> \lib ⽬录中的， 或者被 -Xbootclasspath 参数所指定的路径中的，并且是虚拟机识别的（仅按照⽂件名识别，如 rt.jar，名字不符合的类库即使放在 lib ⽬录中也不会被加载）类库加载到虚拟机内存中。启动类加 载器⽆法被 Java 程序直接引⽤，⽤户在编写⾃定义类加载器时，如果需要把加载请求委派给启动 类加载器，直接使⽤ null 代替即可
    - 扩展类加载器（Extension ClassLoader）这个类加载器是由 ExtClassLoader（sun.misc.Launcher$ExtClassLoader）实现的。它负责将 <JRE_HOME>/lib/ext 或者被 java.ext.dir 系统变量所指定路径中的所有类库加载到内存中，开发者可以直接使⽤扩展类加 载器
    - 应⽤程序类加载器（Application ClassLoader）这个类加载器是由 AppClassLoader（sun.misc.Launcher$AppClassLoader）实现的。由于这个类加载器是 ClassLoader 中的 getSystemClassLoader() ⽅法的返回值，因此⼀般称为系统类加载器。它负责加 载⽤户类路径（ClassPath）上所指定的类库，开发者可以直接使⽤这个类加载器，如果应⽤程序 中没有⾃定义过⾃⼰的类加载器，⼀般情况下这个就是程序中默认的类加载器

  - 双亲委派模型

    ![image-20231114101041474](images\ParentsDelegationModel.png)

    - 该模型要求 除了顶层的启动类加载器外，其它的类加载器都要有⾃⼰的⽗类加载器。这⾥的⽗⼦关系⼀般通过组合 关系（Composition）来实现，⽽不是继承关系（Inheritance）

## 3.5 Java IO

### 3.5.1 IO基础

- 磁盘操作：File
- 字节操作：InputStream和OutputStream
- 字符操作：Reader和Writer
- 对象操作：Serializable
- 网络操作：Socket
- 新的输入/输出：NIO

### 3.5.2 磁盘操作

- File 类可以⽤于表示⽂件和⽬录的信息，但是它不表示⽂件的内容。

  ```Java
  public class MyFile {
      public static void listAllFiles(File dir) {
          if (dir == null || !dir.exists()) {
              return;
          }
          if (dir.isFile()) {
              System.out.println(dir.getName());
              return;
          }
          for (File file : dir.listFiles()) {
              listAllFiles(file);
          }
      }
  }
  ```

### 3.5.3 字节操作

- 实现文件复制

  ```java
  public static void copyFile(String src, String dist) throws IOException {
      FileInputStream in = new FileInputStream(src);
      FileOutputStream out = new FileOutputStream(dist);
      byte[] buffer = new byte[20 * 1024];
      int cnt;
      // read() 最多读取 buffer.length 个字节
      // 返回的是实际读取的个数
      // 返回 -1 的时候表示读到 eof，即⽂件尾
      while ((cnt = in.read(buffer, 0, buffer.length)) != -1) {
          out.write(buffer, 0, cnt);
      }
      in.close();
      out.close();
  }
  ```

- 装饰者模式

  - Java I/O 使⽤了装饰者模式来实现

  - inputStream 是抽象组件；FileInputStream 是 InputStream 的⼦类，属于具体组件，提供了字节流的输⼊操作；FilterInputStream 属于抽象装饰者，装饰者⽤于装饰组件，为组件提供额外的功能。例如 BufferedInputStream 为 FileInputStream 提供缓存的功能

    ```java
    FileInputStream fileInputStream = new FileInputStream("filePath");
    BufferedInputStream bufferedInputStream = new BufferedInputStream(fileInputStream);
    ```

### 3.5.4 字符操作

- 编码与解码

  - 编码就是把字符转换为字节，⽽解码是把字节重新组合成字符
  - 如果编码和解码过程使⽤不同的编码⽅式那么就出现了乱码
  - GBK 编码中，中⽂字符占 2 个字节，英⽂字符占 1 个字节；
  - UTF-8 编码中，中⽂字符占 3 个字节，英⽂字符占 1 个字节
  - UTF-16be 编码中，中⽂字符和英⽂字符都占 2 个字节

- Reader 与 Write

  - 不管是磁盘还是⽹络传输，最⼩的存储单元都是字节，⽽不是字符。但是在程序中操作的通常是字符形 式的数据，因此需要提供对字符进⾏操作的⽅法

  - InputStreamReader 实现从字节流解码成字符流

  - OutputStreamWriter 实现字符流编码成为字节流

  - 实现逐⾏输出⽂本⽂件的内容

    ```java
    public static void readFileContent(String filePath) throws IOException {
        FileReader fileReader = new FileReader(filePath);
        BufferedReader bufferedReader = new BufferedReader(fileReader);
        String line;
        while ((line = bufferedReader.readLine()) != null) {
            System.out.println(line);
        }
        // 装饰者模式使得 BufferedReader 组合了⼀个 Reader 对象
        // 在调⽤ BufferedReader 的 close() ⽅法时会去调⽤ Reader 的 close() ⽅法
        // 因此只要⼀个 close() 调⽤即可
        bufferedReader.close();
    }
    ```

### 3.5.5 对象操作

- 序列化

  - 序列化就是将⼀个对象转换成字节序列，⽅便存储和传输
  - 序列化：ObjectOutputStream.writeObject()
  - 反序列化：ObjectInputStream.readObject()
  - 不会对静态变量进⾏序列化，因为序列化只是保存对象的状态，静态变量属于类的状态

- Serializable

  - 序列化的类需要实现 Serializable 接⼝，它只是⼀个标准，没有任何⽅法需要实现，但是如果不去实现 它的话⽽进⾏序列化，会抛出异常

    ```java
    public class MySerial {
    
        public static void main(String[] args) throws Exception {
            A a = new A(1, "123");
            A.setZ(15);
            System.out.println(A.z);
            ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream("D://testest.txt"));
            objectOutputStream.writeObject(a);
            objectOutputStream.close();
            ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream("D://testest.txt"));
            A a1 = (A) objectInputStream.readObject();
            objectInputStream.close();
            System.out.println(A.z);
        }
    
        private static class A implements Serializable {
            private int x;
            private String y;
            private static int z;
    
            public A(int x, String y) {
                this.x = x;
                this.y = y;
            }
    
            public int getX() {
                return x;
            }
    
            public void setX(int x) {
                this.x = x;
            }
    
            public String getY() {
                return y;
            }
    
            public void setY(String y) {
                this.y = y;
            }
    
            public static int getZ() {
                return z;
            }
    
            public static void setZ(int z) {
                A.z = z;
            }
        }
    }
    
    ```

  - transient

    - transient 关键字可以使⼀些属性不会被序列化

    - ArrayList 中存储数据的数组 elementData 是⽤ transient 修饰的，因为这个数组是动态扩展的，并不是 所有的空间都被使⽤，因此就不需要所有的内容都被序列化。通过重写序列化和反序列化⽅法，使得可以只序列化数组中有内容的那部分数据。

      ```java
      private transient Object[] elementData;
      ```

### 3.5.6 网络操作

- 网络支持

  - InetAddress：用于表示网络上的硬件资源，即ip地址
  - URL：统一资源定位符；
  - Sockets：使用TCP协议实现网络通信
  - Datagram：使用UDP协议实现网络通信

- InetAddress

  ```java
  InetAddress.getByName(String host);
  InetAddress.getByAddress(byte[] address)
  ```

- URL

  - 可以直接从 URL 中读取字节流数据

    ```java
    public class MyURL {
        public static void main(String[] args) throws Exception {
            URL url = new URL("http://www.baidu.com");
            /* 字节流 */
            InputStream is = url.openStream();
            /* 字符流 */
            InputStreamReader isr = new InputStreamReader(is, "utf-8");
            /* 提供缓存功能 */
            BufferedReader br = new BufferedReader(isr);
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
            br.close();
        }
    }
    ```

- Sockets

  - ServerSocket：服务器端类

  - Socket：客户端类

  - 服务器和客户端通过InputStream和OutputStream进行输入输出。

    ![image-20231114141100419](images\serverSocket.png)

- Datagram

  - DatagramSocket：通信类 
  - DatagramPacket：数据包类

### 3.5.7 NIO

- 流与块

  - I/O 与 NIO 最重要的区别是数据打包和传输的⽅式，I/O 以流的⽅式处理数据，⽽ NIO 以块的⽅式处理 数据
  - ⾯向流的 I/O ⼀次处理⼀个字节数据：⼀个输⼊流产⽣⼀个字节数据，⼀个输出流消费⼀个字节数据。
  - ⾯向块的 I/O ⼀次处理⼀个数据块

- 通道与缓冲区

  - 通道

    - 通道 Channel 是对原 I/O 包中的流的模拟，可以通过它读取和写⼊数据。
    - 流只能在⼀个⽅向上移动(⼀个流必须是 InputStream 或者 OutputStream 的 ⼦类)，⽽通道是双向的，可以⽤于读、写或者同时⽤于读写
    - 通道类型
      - FileChannel：从⽂件中读写数据
      - DatagramChannel：通过 UDP 读写⽹络中数据
      - SocketChannel：通过 TCP 读写⽹络中数据
      - ServerSocketChannel：可以监听新进来的 TCP 连接，对每⼀个新进来的连接都会创建⼀个 SocketChannel

  - 缓冲区

    - 发送给⼀个通道的所有数据都必须⾸先放到缓冲区中，同样地，从通道中读取的任何数据都要先读到缓 冲区中。也就是说，不会直接对通道进⾏读写数据，⽽是要先经过缓冲区。
    - 缓冲区实质上是⼀个数组，但它不仅仅是⼀个数组。缓冲区提供了对数据的结构化访问，⽽且还可以跟 踪系统的读/写进程
    - 缓冲区类型
      - ByteBuffer
      - CharBuffer
      - ShortBuffer
      - IntBuffer
      - LongBuffer
      - FloatBuffer
      - DoubleBuffer
    - 缓冲区状态变量
      - capacity：最⼤容量
      - position：当前已经读写的字节数
      - limit：还可以读写的字节数

  - 状态变量的改变过程

    - 新建⼀个⼤⼩为 8 个字节的缓冲区，此时 position 为 0，⽽ limit = capacity = 8。capacity 变量不会 改变

    ![image-20231114141638124](images\statusInit.png)

    - 从输⼊通道中读取 5 个字节数据写⼊缓冲区中，此时 position 为 5，limit 保持不变

      ![image-20231114141806204](images\statusSecond.png)

    - 在将缓冲区的数据写到输出通道之前，需要先调⽤ flip() ⽅法，这个⽅法将 limit 设置为当前 position，并将 position 设置为 0

      ![image-20231114141902934](images\statusThird.png)

    - 从缓冲区中取 4 个字节到输出缓冲中，此时 position 设为 4

      ![image-20231114141943186](images\statusFour.png)

    - 最后需要调⽤ clear() ⽅法来清空缓冲区，此时 position 和 limit 都被设置为最初位置

      ![image-20231114141638124](images\statusInit.png)

- 文件NIO实例

  ```java
  public class MyFastCopy {
      public static void fastCopy(String src, String dist) throws IOException {
          /* 获得源⽂件的输⼊字节流 */
          FileInputStream fin = new FileInputStream(src);
          /* 获取输⼊字节流的⽂件通道 */
          FileChannel fcin = fin.getChannel();
          /* 获取⽬标⽂件的输出字节流 */
          FileOutputStream fout = new FileOutputStream(dist);
          /* 获取输出字节流的⽂件通道 */
          FileChannel fcout = fout.getChannel();
          /* 为缓冲区分配 1024 个字节 */
          ByteBuffer buffer = ByteBuffer.allocateDirect(1024);
          while (true) {
              /* 从输⼊通道中读取数据到缓冲区中 */
              int r = fcin.read(buffer);
              /* read() 返回 -1 表示 EOF */
              if (r == -1) {
                  break;
              }
              /* 切换读写 */
              buffer.flip();
              /* 把缓冲区的内容写⼊输出⽂件中 */
              fcout.write(buffer);
              /* 清空缓冲区 */
              buffer.clear();
          }
      }
  
      public static void main(String[] args) throws IOException {
          MyFastCopy.fastCopy("D://testest.txt", "D://testestCopy.txt");
      }
  }
  ```

- 选择器

  - NIO 实现了 IO 多路复⽤中的 Reactor 模型，⼀个线程 Thread 使⽤⼀个选择器 Selector 通过轮询的⽅式去监听多个通道 Channel 上的事件，从⽽让⼀个线程就可以处理多个事件。

  - 只有SocketChannel 才能配置为⾮阻塞，⽽ FileChannel 不能，为 FileChannel 配置⾮阻塞也没有意义

    ![image-20231114142738608](images\select.png)

  - 创建选择器

    ```java
    Selector selector = Selector.open();
    ```

  - 将通道注册到选择器上

    ```java
    ServerSocketChannel ssChannel = ServerSocketChannel.open();
    // 通道必须配置为⾮阻塞模式，否则使⽤选择器就没有任何意义了，因为如果通道在某个事件上被阻塞，那么服务器就不能响应其它事件，必须等待这个事件处理完毕才能去处理其它事件，显然这和选择器的作⽤背道⽽驰。
    ssChannel.configureBlocking(false);
    ssChannel.register(selector, SelectionKey.OP_ACCEPT);
    ```

  - 注册具体事件

    - SelectionKey.OP_CONNECT
    - SelectionKey.OP_ACCEPT
    - SelectionKey.OP_READ
    - SelectionKey.OP_WRITE

  - 获取事件

    ```java
    while (true) {
        int num = selector.select();
        Set<SelectionKey> keys = selector.selectedKeys();
        Iterator<SelectionKey> keyIterator = keys.iterator();
        while (keyIterator.hasNext()) {
            SelectionKey key = keyIterator.next();
            if (key.isAcceptable()) {
                // ...
            } else if (key.isReadable()) {
                // ...
            }
            keyIterator.remove();
        }
    }
    ```

- Socket NIO 实例

  - Socket服务端

    ```java
    public class MyNIOServer {
        public static void main(String[] args) throws Exception {
            Selector selector = Selector.open();
            ServerSocketChannel ssChannel = ServerSocketChannel.open();
            ssChannel.configureBlocking(false);
            ssChannel.register(selector, SelectionKey.OP_ACCEPT);
    
            ServerSocket serverSocket = ssChannel.socket();
            InetSocketAddress address = new InetSocketAddress("127.0.0.1", 9999);
            serverSocket.bind(address);
    
            while (true) {
                selector.select();
                Set<SelectionKey> selectionKeys = selector.selectedKeys();
                Iterator<SelectionKey> iterator = selectionKeys.iterator();
                while (iterator.hasNext()) {
                    SelectionKey next = iterator.next();
                    if (next.isAcceptable()) {
                        // 服务器会为每个新连接创建⼀个 SocketChannel
                        ServerSocketChannel channel = (ServerSocketChannel) next.channel();
                        SocketChannel accept = channel.accept();
                        accept.configureBlocking(false);
    
                        // 这个新连接主要⽤于从客户端读取数据
                        accept.register(selector, SelectionKey.OP_READ);
                    } else if (next.isReadable()) {
                        SocketChannel sChannel = (SocketChannel) next.channel();
    
                        System.out.println(readDataFromSocketChannel(sChannel));
                        sChannel.close();
                    }
                    iterator.remove();
                }
            }
        }
        private static String readDataFromSocketChannel(SocketChannel sChannel)
                throws IOException {
            ByteBuffer buffer = ByteBuffer.allocate(1024);
            StringBuilder data = new StringBuilder();
            while (true) {
                buffer.clear();
                int n = sChannel.read(buffer);
                if (n == -1) {
                    break;
                }
                buffer.flip();
                int limit = buffer.limit();
                char[] dst = new char[limit];
                for (int i = 0; i < limit; i++) {
                    dst[i] = (char) buffer.get(i);
                }
                data.append(dst);
                buffer.clear();
            }
            return data.toString();
        }
    }
    ```

  - Socket客户端

    ```java
    public class MyNIOClient {
        public static void main(String[] args) throws Exception {
            Socket socket = new Socket("127.0.0.1", 9999);
            OutputStream out = socket.getOutputStream();
            String s = "hello world";
            out.write(s.getBytes());
            out.close();
        }
    }
    ```

- 内存映射文件

  - 内存映射⽂件 I/O 是⼀种读和写⽂件数据的⽅法，它可以⽐常规的基于流或者基于通道的 I/O 快得多

  - 向内存映射⽂件写⼊可能是危险的，只是改变数组的单个元素这样的简单操作，就可能会直接修改磁盘 上的⽂件。修改数据与将数据保存到磁盘是没有分开的

  - 将⽂件的前 1024 个字节映射到内存中，map() ⽅法返回⼀个 MappedByteBuffer

    ```java
    public class MyMapFile {
        public static void main(String[] args) throws Exception {
            RandomAccessFile randomAccessFile = new RandomAccessFile("D://1.txt", "rw");
            FileChannel channel = randomAccessFile.getChannel();
            MappedByteBuffer map = channel.map(FileChannel.MapMode.READ_WRITE, 0, 10);
            map.put(0, (byte)'H');
            map.put(3, (byte)'J');
            randomAccessFile.close();
        }
    }
    ```

# 四、MySQL

## 4.1 MySQL索引

### 4.1.1 Explain分析索引

```mysql
EXPLAIN SELECT * FROM your_table WHERE column_name = 'value';
```

- `select_type`：表示查询的类型，如简单查询、联合查询等
- `table`：表示相关的表名。  
- `partitions`：表示返回的是MySQL在执行查询时所使用的分区数量。
-  `type`：表示访问表的方式，如系统、常量、单表查询、联合查询等。  
  - `system`：表示查询只需要访问一个系统表，不需要进行实际的数据检索。这是最高效的查询类型。
  - `const`：表示查询只需要访问一个常量表，并且只返回一条记录。这是次高效的查询类型。
  - `eq_ref`：表示查询需要访问一个主键或唯一索引列，并且只返回匹配的唯一记录。这是高效的查询类型。
  - `ref`：表示查询需要访问一个非唯一索引列或多个普通列，并且返回匹配的记录。这是中效的查询类型。
  - `range`：表示查询需要访问一个范围索引列，并且返回满足条件的记录。这是中效的查询类型。
  - `index`：表示查询需要访问一个索引列，并且返回所有记录。这是低效的查询类型。
  - `ALL`：表示查询需要访问整个表，并且返回所有记录。这是最低效的查询类型。
- `possible_keys`：表示可能使用的索引。  
- `key`：表示实际使用的索引。  
- `key_len`：表示使用的索引长度，即使用到的索引列的列长度。  
- `ref`：表示与索引比较的列或常量。  
  - `const,const`：表示查询使用了常量值进行匹配。这通常出现在等值查询中，并且查询条件使用了常量值来匹配索引列。
  - 索引名：表示查询使用了某个索引来加速查询。索引名会显示在`ref`列中，帮助你识别查询使用了哪个索引。
  - NULL：表示查询没有使用索引或者使用了MySQL优化器选择的全表扫描。这种情况下，MySQL会扫描整个表来查找满足查询条件的行。
  - 多个列名或常量值：当查询使用了组合索引或联合索引时，`ref`列可能会返回多个列名或常量值。这是因为查询条件同时使用了多个索引列进行匹配。
-  `rows`：表示MySQL估计需要扫描的行数。通过分析执行计划，你可以判断查询是否使用了正确的索引，以及索引是否有效。
- `filtered`：表示存储引擎返回的数据在server层过滤后，剩下多少满足查询的记录数量的百分比。因此，`filtered`的值越大，说明过滤掉的记录越少，查询结果越符合预期
- `Extra`：这个列提供了关于查询执行计划的额外信息。
  - `Using index`：表示查询使用了覆盖索引（Covering Index），即索引包含了所有需要检索的列数据，而不仅仅是索引列本身。这种情况下，MySQL不需要访问表数据，只需要使用索引即可获取结果。
  - `Using temporary`：表示查询使用了临时表。MySQL在处理一些复杂的查询时，可能会使用临时表来存储中间结果，以便后续处理。
  - `Using filesort`：表示查询需要对结果进行排序，并且MySQL无法使用索引进行排序。这种情况下，MySQL会使用文件排序算法来对结果进行排序。
  - `LooseScan`：表示查询使用了松散扫描（LooseScan）算法。这是一种在处理连接查询时使用的算法，它允许MySQL跳过一些不满足连接条件的行。
  - `using where`：表示数据在 server 层还进行了过滤操作，说明MySQL在执行查询时已经对结果集进行了过滤操作，只返回满足条件的记录。这种过滤操作可以减少结果集的大小，提高查询效率。
  - `using index condition`：表示使用了索引下推

### 4.1.2 MySQL索引失效情况

- InnoDB引擎里面有两种索引类型，一种是主键索引、一种是普通索引。

- InnoDB用了B+树的结构来存储索引数据。

- 使用索引列进行数据查询的时候，最终会到主键索引树中查询对应的数据行进行返回。

- 失效情况

  - 在索引列加上函数运算，导致Mysql无法识别索引列（Mysql8已解决该问题）；

    ```mysql
    # 走索引
    explain select * from test_index where index_num2 = 12 
    # 不走索引
    explain select * from test_index where index_num2 + 12 = 12 
    ```

  - 联合索引，按最左匹配，如果没有最左列，则不走索引

    ```mysql
    # 走索引
    explain select * from test_index where index_num2 = 12 and index_date = "111"
    # 不走索引
    explain select * from test_index where index_date = "111"
    ```

  - 索引列隐式转换，例如字符串用数字匹配

    ```mysql
    # 走索引
    explain select * from test_index where index_uuid = "000004"
    # 不走索引
    explain select * from test_index where index_uuid = 000004
    ```

  - 使用 !=、not查询，如果索引数据的检索效率非常低，Mysql引擎会判断不走索引

  - 使用like通配符匹配后缀%xxx的时候，由于这种方式不符合索引的最左匹配原则，所以也不会走索引

  - 使用or连接查询的时候，or语句前后没有同时使用索引，那么索引会失效。只有or左右查询字段都是 索引列的时候，才会生效

### 4.1.3 MySQL索引规则

- 索引不适合场景
  - 数据量少的不适合加索引
  - 更新比较频繁的也不适合加索引
  - 区分度低的字段不适合加索引（如性别）
- 索引其他规则
  - 覆盖索引
    - 覆盖索引是指索引包含了查询所需的所有列，即索引本身能够覆盖查询的字段需求，无需再通过回表操作来获取数据。换句话说，一个索引包含了（或覆盖了）满足查询结果的数据就叫做覆盖索引。
  - 聚集索引
    - 聚集索引是按照表中主键的顺序组织数据，索引的叶子节点存储的是<font color='red'>主键和所有数据</font>，每个表只能有一个聚集索引。在聚集索引中，数据在物理存储上是连续的，因此查询数据时速度较快。然而，插入数据时，因为需要找到合适的位置插入数据，速度可能会较慢
  - 非聚集索引
    - 非聚集索引是按照表中非主键列的顺序组织数据。在非聚集索引中，索引的叶子节点存储的是<font color='red'>主键和索引列的数据</font>，因此需要先通过索引查找到主键，再通过主键去查找想要的数据，即需要进行回表操作。非聚集索引也叫做二级索引，在建立的时候也未必是单列的，可以多个列来创建索引。
  - 回表
    - 回表是一种数据库查询优化方式，通常用于处理使用非聚集索引的查询。当使用非聚集索引查询时，数据库引擎如果无法直接从索引中获取到满足查询条件的数据，因此需要进行回表操作，即通过索引找到对应行的行指针，然后通过行指针到表中查找完整的行数据。
  - 索引数据结构（B+树）
    - InnoDB在物理存储层面使用一棵B+树来存储所有聚集索引和非聚集索引，但是在逻辑层面，InnoDB会为每个表创建一个主键索引（聚集索引），同时可以创建多个非主键索引（非聚集索引）。
  - 最左前缀原则
  - 索引下推
    - 索引下推（Index Condition Pushdown，简称ICP）是MySQL 5.6版本的新特性，用于优化数据查询。具体来说，当存储引擎通过索引检索到数据后，MySQL服务器会判断数据是否符合条件。如果不使用索引条件下推优化，存储引擎需要将数据返回给MySQL服务器，服务器再判断数据是否符合条件。而如果使用索引条件下推优化，MySQL服务器会将一部分判断条件传递给存储引擎，存储引擎会根据这些条件判断索引是否符合MySQL服务器传递的条件，只有当索引符合条件时才会将数据检索出来返回给MySQL服务器。这样，索引下推能减少存储引擎查询基础表的次数和MySQL服务器从存储引擎接收数据的次数，从而提高查询效率。

### 4.1.4 MySQL创建索引原则

- 最左前缀匹配原则
- 频繁作为查询条件的字段采取创建索引
- 频繁更新的字段不适合创建索引
- 索引列不能参与计算，不能有函数操作
- 优先考虑扩展索引，而不是新建索引，避免不必要的索引
- 在order by 或者 group by 子句中，创建索引需要注意顺序
- 区分度低的数据列不适合做索引列（如 性别）
- 定义有外键的数据列一定要建立索引
- 对于定义为text、image数据类型的列不要建立索引
- 删除不再使用或者很少使用的索引

## 4.2 MySQL存储过程

### 4.2.1 查询，创建，执行，删除存储过程

- 查询存储过程

  ```mysql
  SHOW PROCEDURE STATUS;
  # procedure_name 存储过程名称
  SHOW CREATE PROCEDURE  procedure_name;
  ```

- 创建存储过程

  ```mysql
  CREATE PROCEDURE insert_data()  
  BEGIN  
      DECLARE i INT DEFAULT 1;  
        
      WHILE i <= 500000 DO  
          INSERT INTO your_table_name (column1, column2, column3)  
          VALUES (value1, value2, value3);  
            
          SET i = i + 1;  
      END WHILE;  
  END
  ```

- 执行存储过程

  ```mysql
  CALL insert_data();
  ```

- 删除存储过程

  ```mysql
  # procedure_name 存储过程名称
  DROP PROCEDURE procedure_name;
  ```

## 4.3 MySQL死锁

### 4.3.1 死锁原因

- 死锁是指两个或多个并发进程在互相请求对方所持有的资源的同时,又拒绝释放自己所持有的资源,导致这些进程都无法继续执行下去的情况。在MySQL中,
  死锁通常发生在事务之间,当多个事务同时请求和持有资源时,可能会发生死锁问题。
  - 事务并发执行，在高并发环境下,多个事务可能同时对数据库资源进行读取和写入。当这些事务在相互竞争资源时,可能会导致死锁的发生。
  - 事务锁定顺序不一致，在MySQL中,事务可以通过行锁或表锁来实现对资源的锁定。当事务在不同的顺序锁定资源时,可能会导致循环依赖,从而发生死锁。

### 4.3.2 死锁处理

- MySQL提供了死锁检测机制,当发生死锁时,系统会自动检测到并主动解决。在检测到死锁后,MySQL会选择其中一个事务作为牺牲品,回滚该事务,解除死锁。

- 开发者还可以调整MySQL的参数来优化死锁处理。例如,通通过调整innodb_lock_wait_timeout参数来控制死锁检测的超时时间,或者通过调整
  innodb_locks_unsafe_for_binlog参数来关闭死锁检测。

  ```mysql
  SHOW VARIABLES LIKE 'innodb_locks_unsafe_for_binlog';
  SHOW VARIABLES LIKE 'innodb_lock_wait_timeout';
  ```

## 4.4 MySQL优化

### 4.4.1 优化类别

-  硬件和操作系统层面优化
  - 从硬件层面来说，影响Mysql性能的因素有，CPU、可用内存大小、磁盘读写速度、网络带宽
- 架构设计层面的优化
  - MySQL是一个磁盘IO访问量非常频繁的关系型数据库
  - 搭建Mysql主从集群，单个Mysql服务容易单点故障，一旦服务器宕机，将会导致依赖Mysql数据库的应用全部无法响应。 主从集群或者主主集群可以保证服务的高可用性
  - 读写分离设计，在读多写少的场景中，通过读写分离的方案，可以避免读写冲突导致的性能影响
  - 引入分库分表机制，通过分库可以降低单个服务器节点的IO压力，通过分表的方式可以降低单表数据量，从而提升sql查询的效率
  - 针对热点数据，可以引入更为高效的分布式数据库，比如Redis、MongoDB等
- MySQL程序配置优化
  - 通过Mysql中的配置文件my.cnf来完成
  - Mysql5.7版本默认的最大连接数是151个，这个值可以在my.cnf中修改
  - binlog日志，默认是不开启
  - 缓存池bufferpoll的默认大小配置
  - 配置项
    - 全局参数的设定对于已经存在的会话无法生效
    - 会话参数的设定随着会话的销毁而失效
    - 全局类的统一配置建议配置在默认配置文件中，否则重启服务会导致配置失效
- SQL优化
  - 慢SQL的定位和排查
    - 可以通过慢查询日志和慢查询日志分析工具得到有问题的SQL列表
  - 执行计划分析
    - 针对慢SQL，我们可以使用关键字explain来查看当前sql的执行计划.可以重点关注 type key rows filterd 等字段 ，从而定位该SQL执行慢的根本原因。再有的放矢的进行优化
  - 使用show profile工具

### 4.4.2 分库分表设计

- 分库

  - 分库是指在表数量不变的情况下对库进行切分。

    ![image-20231115151337461](images\sub-treasury.png)

- 分表

  - 分表是指在库数量不变的情况下对表进行切分。

    ![image-20231115151456525](images\submeter.png)

- 分库分表

  - 分库分表是指库和表都切分，数量都发生变化

    ![image-20231115151841709](images\dividDataTable.png)

- 切分方式

  - 水平切分、垂直切分和混合切分

  - 水平切分包含水平分库和水平分表

    - 水平分表

      1. 水平分表指的表结构不变，将单表数据切分成多表

      2. 每个表的结构一样

      3. 每个表的数据不一样

      4. 所有表的数据并集为全量数据

         ![image-20231115152011527](images\HorizontalDivisionTable.png)

    - 水平分库

      1. 水平分库是指，将表水平切分后分到不同的数据库，使得每个库具有相同的表，表中的数据不相同，水平分库一般是伴随水平分表

         ![image-20231115152156637](images\HorizontalSubLibrary.png)

  - 垂直切分包含垂直分库和垂直分表

    - 垂直分表

      1. 垂直分表指将存在一张表中的字段切分到多张表

      2. 每个表的结构不一样

      3. 每个表的数据不一样

      4. 所有表的字段并集是原表的字段

         ![image-20231115152245587](images\VerticalTableDivision.png)

    - 垂直分库

      1. 垂直分库指的是，将单个库中的表分到多个库，每个库包含的表不一样

         ![image-20231115152502542](images\VerticalSubLibrary.png)

  - 混合切分

    - 混合切分其实就是水平切分和垂直切分的组合

      ![image-20231115152623123](images\MixedSegmentation.png)

### 4.4.3 分库分表切分策略

- 主流的切分策略有3种：Range 范围、hash切分、映射表
- Range范围
  - Range 范围是指按某个字段的数据区间来进行切分。
  - 方便扩容，每次数据量达到 range值就新加一张表，可以通过代码实现自动化扩容
  - 存在写偏移，可能有热点问题（读写流量全部集中在最新的表）
- hash切分
  - 通过对分表键 key 进行一定的运算（通常有取余、取模运算，比如：key % m，key / m，hash(key)/m 等等），通过运算结果来决定路由的库和表。
  - 数据分片比较均匀，大大降低热点问题
  - hash 算法选择不合理，后期扩容可能需要迁移数据
  - 数据被切分到不同的库和表中，可能存在跨节点查询和分页等问题
- 映射表
  - 映射表其实是 Range范围 和 hash切分的混合模式，将分表键和数据库的映射关系记录在一个单独的表（表的形式可以是 数据库表，文件或者配置中心）。
  - 可以灵活设置路由规则
  - 方案比较复杂
  - 映射表可能也会随着业务量的增大，同样需要分库分表，带来更多的问题

### 4.4.4 分库分表问题

- 调试和维护难度
  - 单库单表，可以很直观在表中查看数据，分库分表后，需要先根据 key找到库和表，这样在一定意义上增加了开发人员定位问题的难度

- 分布式ID
  - 单库单表，可以直接使用表自增主键保证全局唯一性，分库分表后，需要自己维护全局唯一的ID，常用的算法有：UUID、号段模式（数据库生成全局ID）、雪花算法
  - UUID
    - 性能非常高，本地生成，没有网络消耗
    - 不易于存储：UUID太长，16字节128位，通常以36长度的字符串表示，很多场景不适用
    - 信息不安全：基于MAC地址生成UUID的算法可能会造成MAC地址泄露，这个漏洞曾被用于寻找梅丽莎病毒的制作者位置
    - ID作为主键时在特定的环境会存在一些问题，比如做DB主键的场景下，UUID就非常不适用
  - 号段模式
    - 可以每次获取一个ID，也可以每次获取一批ID
    - 简单，利用现有数据库系统的功能实现
    - ID单调自增，可以实现对ID要求特殊的业务
    - 强依赖发号DB的性能，可能有单点问题（如果一个数据库成为应用程序中所有请求的瓶颈，那么这个数据库就成为了性能瓶颈，也就是所谓的单点故障）
  - 雪花算法
    - 毫秒数在高位，自增序列在低位，整个ID都是趋势递增的
    - 不依赖数据库等第三方系统，以服务的方式部署，稳定性更高，生成ID的性能也是非常高的
    - 可以根据自身业务特性分配bit位，非常灵活
    - 强依赖机器时钟，如果机器时钟回拨，会导致重复或者服务不可用，不过发生的概率比较小

- 分布式事务问题

  - 业务划分的时候规避分布式事务
  - 使用专业的的分布式框架，比如阿里开源的 [Seata](https://link.zhihu.com/?target=https%3A//seata.io/zh-cn/)

- 跨库关联/分页/排序

  - 选择合适的分表字段，规避绝大部分高频查询场景出现跨库
  - 使用专业的分布式框架，比如开源框架：ElasticSearch
  - 业务代码中分别查询，然后组装数据

- 分库分表工具

  - 客户端模式

    - 客户端模式是指在客户端实现直连数据库，客户端通常是通过一些封装好的 jar来实现

    - 常见的开源中间件有：Apache的Sharding-JDBC、淘宝的TDDL、美图的Zebra

      ![image-20231116110045737](images\client.png)

  - 代理模式

    - 代理模式是指需要单独部署服务，客户端连接代理服务，由代理服务再和数据库交互

    - 常见的开源中间件有：Apache的 Sharding-Proxy、阿里的 cobar、国产的 MyCat、360的 Atlas。另外还有 google的 vitess，它是基于 zookeeper，通过 RPC方式进行数据管理

      ![image-20231116110209607](images\proxy.png)


## 4.5 MySQL表类型

### 4.5.1 InnoDB和MyISAM区别

- 数据的存储结构不同

  - MyISAM

    - 每隔MyISAM在磁盘上存储成三个文件，.frm文件存储表定义，.MYD(MYD)存储数据文件，.MYI(MYIndex)存储索引文件

    - MyISAM的索引和数据是分开存储，索引查找MyISAM的叶子节点存储的是数据所在的地址，而不是数据。

      ![image-20231116131847174](images\MyISAM.png)

  - InnoDB

    - 保存为两个文件，.frm文件存储为表结构文件，.ibd文件存储的是数据和索引文件

    - InnoDB叶子节点存储的是整个数据行所有的数据

      ![image-20231116131951246](images\InnoDB.png)

- 存储空间的消耗不同

  - MyISAM可被压缩，存储空间较小。支持三种不同的存储格式：静态表（默认，但是注 意数据末尾不能有空格，会被去掉）、动态表、压缩表。
  - InnoDB需要更多的内存和存储，它会在主内存中建立其专用的缓冲池用于高速缓冲数 据和索引。InnoDB所在的表都保存在同一个数据文件中（也可能是多个文件，或者是独立的表 空间），InnoDB表的大小只受限于操作系统文件的大小，一般为2GB

- 对事务的支持不同

  - MyISAM强调的是性能，每次查询具有原子性，其执行速度比Innodb类型更快，但是不提供事务支持
  - InnoDB除了提供事务支持和外部键等高级数据库功能。还具有事务提交（commit）、回 滚（rollback）和崩溃修复能力（crach recovery capabilities）等这些事务安全 （transaction-safe ACID compliant）型表

- 对锁的支持不同

  - 如果只是执行大量的查询, MyISAM是更好的选择。MyISAM在增删的时候需要锁定整个表格，效率会低一些
  - 而innoDB支持行级锁，删除插入的时候只需要锁定操作行就行。如果有大量的插入、修改 删除操作，使用InnoDB性能能会更高。

- 对外键的支持不同

  - MyISAM不支持外键，而InnoDB支持外键。不同的MySQL版本对两者的支持都有所改进

### 4.5.2 数据库索引B+树

- B树

  - B树是一种多路平衡树，用这种存储结构来存储大量数据，它的整个高度会比二叉树低

  - 树的高度能够决定磁盘IO的次数

    ![image-20231116132727080](images\B-Tree.png)

- B+树

  - B+树的所有数据都存储在叶子节点，非叶子节点只存储索引，所以每一层能够存储的索引数量会增加，意味着B+树在层高相同的情 况下存储的数据量要比B树要多，使得磁盘IO次数更少

  - 叶子节点中的数据使用双向链表的方式进行关联，查询的时候只需查两个节点进行遍历就行，而B树需要获取所有节点

    ![image-20231116133044175](images\B+Tree2.png)

### 4.5.3 聚集索引和非聚集索引

- 聚集索引

  - 就是基于主键创建的索引，是按照每张表的主键来构建一颗 B+树，然后叶子节点里面存储了这个表的每一行数据记录

  - 聚集索引并不仅仅是一种索引类型，还代表着一种数据的存储方式

  - 意味着每个表里面必须要有一个主键，如果没有主键，InnoDB 会默认选择或者添加一 个隐藏列作为主键索引来存储这个表的数据行

  - InnoDB 里面只能存在一个聚集索引

    ![image-20231116133655809](images\ClusteredIndex.png)

- 非聚集索引

  - 除了主键索引以外的其他索引，称为非聚集索引，也叫做二级索引

## 4.6 MySQL隔离级别

### 4.6.1 MySQL脏读、幻读、不可重复读

- 脏读

  - 假设有两个事务T1/T2同时在执行，T1事务有可能会读取到T2事务未提交的数据，但是未提交的事务T2可能会回滚，也就导致了T1事务在开始和最后读取到不同的数据产生脏读的现象
  - 读脏数据是读到的数据是被其他事务修改但会被撤销的数据，所以是脏数据。

  ![image-20231116134100670](images\DirtyReading.png)

- 幻读

  - 假设有两个事务T1/T2同时执行，事务T1执行范围查询或者范围修改的过程中，事务T2插入了一条属于事务T1范围内的数据并且提交了，这时候在事务T1查询发现多出来了一条数据，或者在T1事务发现这条数据没有被修改，看起来像是产生了幻觉，这种现象称为幻读

  - 幻读的重点在于新增或者删除同样的条件，第1次和第2次读出来的记录数不一样

    ![image-20231116135342098](images\PhantomRead.png)

- 不可重复读

  - 假设有两个事务T1/T2同时执行，事务T1在不同的时刻读取同一行数据的时候结果可能不一样，从而导致不可重复读

    ![image-20231116134100670](images\non-repeatableRead.png)

### 4.6.2 事务隔离级别

- 读未提交（RU）

  - 这种隔离级别，可能会产生脏读、不可重复读、幻读

- 读已提交（RC）

  - 这种隔离级别，可能会产生不可重复度，幻读

- 可重复读（RR）

  - 这种隔离级别，可能会产生幻读（MySQL新版本已修复该问题）

- 串行化

  - 这种隔离级别，多个并行事务串行化执行，不会产生安全性问题

- MySQL默认可重复读，保证事务ACID特性中的隔离性特征

  ```mysql
  SET GLOBAL TRANSACTION ISOLATION LEVEL REPEATABLE READ;
  SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED;
  READ UNCOMMITTED：读未提交，允许读取其他事务未提交的数据。
  READ COMMITTED：读已提交，只允许读取其他事务已提交的数据。
  REPEATABLE READ：可重复读，在事务期间多次读取同一数据时，结果始终一致。
  SERIALIZABLE：可串行化，最高级别的隔离级别，确保事务串行执行。
  SELECT @@tx_isolation; 查看当前会话隔离级别
  SELECT @@global.tx_isolation; 查看系统当前隔离级别
  ```

### 4.6.3 MVCC实现原理

- MVCC，直译多版本并发控制，它的全称是Multi-Version Concurrency Control，直白说就是在同一时刻同一条记录在系统中可以存在多个版本，这就是数据库的多版本并发控制。

  ![image-20231116162439620](images\MVCC.png)

- 当下一个事务要操作这条记录时，会先比较trx_id和自己的事务ID大小，同时和自己维护的活跃事务列表ID比较，如果不能直接读取记录行的数据，那么会顺着undo日志的"链条"找到自己能用的数据版本（只能操作小于等于自己的事务ID，且不在自己维护的活跃事务列表ID）这就是MVCC

- trx_id ：每次一个事务对某条聚簇索引记录改动时，都会把自己的事务id重新写到 trx_id 隐藏列。

- roll_pointer ：每次对某条聚簇索引记录进行改动时，都会把旧版本记录写入到 undo日志中，roll_pointer这个隐藏列是一个地址指针，通过它可以找到该聚簇索引记录历史修改信息

- undo 日志：又名undo log，也称回滚日志，它是 Innodb 存储引擎层生成的日志。在数据更新之前，MySQL就需要先把更新前的数据记录到 undo log 日志中，当事务回滚时，可以利用 undo log 来进行回滚。

  - insert undo log：顾名思义，此代表执行insert语句时产生的undo log, 它只在事务回滚时需要，因为这种log只是对本事务可见，其他事务不可见，所以当事务提交后，这种类型的undo log就会被系统直接删除回收（也就是该undo log占用的undo页面链表被释放）。
  - update undo log：事务在进行update或者delete时产生的undo log; 不仅在事务回滚时需要，在快照读时也需要（也就是MVCC），所以不能在事务提交后马上删除，只在提交后放入undo log的链表，等待purge线程进行最后的删除。

- Read View就是事务进行快照读操作的时候产生的读视图(Read View)，在该事务执行的快照读的那一刻，会生成数据库系统当前的一个快照，记录并维护系统数据以及当前活跃事务的ID（就是启动了还没提交的事务）。

  - 当前读：使用到当前读的场景有select lock in share mode(共享锁)、 select for update 、 update、insert、delete(排他锁)等，这些操作都是一种当前读，因为它需要读取记录的最新版本，而且读取时还有可能会通过加锁保证其他事务不能同时修改当前记录。

  - 快照读：快照读一般指不加锁的select操作，当然如果MySQL数据库的事务隔离级别是串行隔离级别，串行级别下的快照读会退化成当前读。

    ![image-20231116162913849](images\ReadView.png)

    - creator_trx_id ：指创建该 Read View 的事务的事务 id。
    - m_ids ：指创建该 Read View 时数据库中所有活跃事务的事务 id 列表，这是一个列表，活跃事务则代表是已启动但未提交的事务。
    - min_trx_id ：指创建 Read View 时数据库中所有活跃事务中最小的事务 id，也就是 m_ids 中的最小值。
    - max_trx_id ：指下一个要创建 Read View 的事务的事务 id，它并不是m_ids中的最大值，需要加以区分。
    - 在可重复读隔离级别下，Read View是在<font color='red'>事务开始（begin）之后且执行第一条快照读sql</font>时创建，创建Read View的同时也就生成了一个新的事务id（直到commit结束），事务会依赖该 Read View保证查询结果保持不变直到该事务结束。

- 可重复读实现原理

  - 可重复读（REPEATABLE READ），指在整个事务过程中该事务看到的记录，自始至终都是一样的。
    - 假如现在Tom的账户余额有100，当前该记录上的事务id是10。
    - ![image-20231116163334108](images\opProcess.png)
    - ![image-20231116163423673](images\opResult.png)
    - 事务A在事务B前启动，但事务A的第一条sql执行前事务B也已启动，所以Read View如上
    - 事务B 修改了Tom的余额记录，Tom的余额记录就会变成200，同时事务id列（trx_id）记录的是事务B的事务id（12）。
    - 事务A读取到 trx_id = 10 的记录，也即查询Tom账户余额还是100，实现了可重复读隔离级别。
    - MySQL通过一种next-key lock的锁机制一定程度上避免了幻读问题

- readview如何判断版本链中的版本可用

  ![image-20231116172558080](images\ReadViewVersion.png)

  - 如果要读取的事务id等于进行读操作的事务id，说明是我读取我自己创建的记录
  - 如果要读取的事务id小于最小的活跃事务id，说明要读取的事务已经提交，那么可以读取。
  - max_trx_id表示生成readview时，分配给下一个事务的id，如果要读取的事务id大于max_trx_id，说明该id已经不在该readview版本链中了，故无法访问
  - m_ids中存储的是活跃事务的id，如果要读取的事务id不在活跃列表，那么就可以读取，反之不行

- mvcc如何实现RC和RR的隔离级别

  - RC的隔离级别下，每个快照读都会生成并获取最新的readview。
  - RR的隔离级别下，只有在同一个事务的第一个快照读才会创建readview，之后的每次快照读都使用的同一个readview，所以每次的查询结果都是一样的。

### 4.6.4 MySQL解决幻读

- 快照读：通过mvcc，RR的隔离级别解决了幻读问题，因为每次使用的都是同一个readview

- 当前读：通过next-key锁（行锁+gap锁），RR隔离级别并不能解决幻读问题。

  - next-key lock，其等同于间隙锁+记录锁的组合。
  - 记录锁，顾名思义，就是给数据行加的锁
  - 间隙锁，bank_balance表中只存在余额balance>0且主键id 为4和6的记录，那么当一个事务使用select * from where balance>0 for update查询时，其他事务就无法插入 id = 5的记录，就像是事务A把(4,6)这个范围锁住了
  - 如果再把id=4和6的记录也同时一起锁了，合起来变成一个闭区间[4, 6]，那么整个区间锁也叫next-key lock。
  - 如果我们的表中只有两条记录，分别是(4, 'Eric', 100,0)、(10, 'Loop', 100,0)，那么当我们执行select *from bank_balance where id > 8 for update时，就只会形成两个next-key lock，它就是(4, 10]，(10, +∞]，如果我们执行insert into bank_balance values(5,'MALL',100,0)将会被阻塞，但是我们执行insert into bank_balance values(2,'MALL',100,0)就不会被阻塞，因为id=2没有被锁住。

- next-key lock规则

  - 原则 1 ：加锁的基本单位是 next-key lock 。 next-key lock 是前开后闭区间。
  - 原则 2 ：查找过程中访问到的对象才会加锁。任何辅助索引上的锁，或者非索引列上的锁，最终都要回溯到主键上，在主键上也要加一把锁。
  - 优化 1 ：索引上的等值查询，给唯一索引加锁的时候， next-key lock 退化为行锁。也就是说如果InnoDB扫描的是一个主键、或是一个唯一索引的话，那InnoDB只会采用行锁方式来加锁
  - 优化 2 ：索引上（不一定是唯一索引）的等值查询，向右遍历时且最后一个值不满足等值条件的时候， next-keylock 退化为间隙锁。
  - 一个 bug ：唯一索引上的范围查询会访问到不满足条件的第一个值为止。

- next-key 例子

  - ```mysql
    CREATE TABLE `test` (
    id` int(11) NOT NULL,
    coll` int(11) DEFAULT NULL,
    col2` int(11) DEFAULT NULL,
    PRIMARY KEY (`id`),
    KEY`c` (`coll`)
    ) ENGINE=InnoDB;
    insert into test values(0,0,0),(5,5,5),
    (10,10,10),(15,15,15),(20,20,20),(25,25,25);
    ```

  - 唯一索引等值查询间隙锁

    ![image-20231116180617029](images\nextKey1.png)

    - 由于表 test 中没有 id=7 的记录，根据原则 1 ，加锁单位是 next-key lock ， session A 加锁范围就是 (5,10] ；
    - 同时根据优化 2 ，这是一个等值查询 (id=7) ，而 id=10 不满足查询条件， next-key lock 退化成间隙锁，因此最终加锁的范围是 (5,10)

  - 非唯一索引等值查询锁

    ![image-20231116180842392](images\nextKey2.png)

    - 这里 session A 要给索引 col1 上 col1=5 的这一行加上读锁，
    - 根据原则 1 ，加锁单位是 next-key lock ，左开右闭，5是闭上的，因此会给 (0,5]加上 next-key lock，
    - 要注意 c 是普通索引，因此仅访问 c=5 这一条记录是不能马上停下来的（可能有col1=5的其他记录），需要向右遍历，查到c=10 才放弃。
    - 根据原则2，需要对所有访问进行加锁，因此需要给区间(5,10]加上next-key lock。
    - 同时这个符合优化 2 ：等值判断，向右遍历，最后一个值不满足 col1=5 这个等值条件，因此退化成间隙锁 (5,10) 。
    - 根据原则 2 ， 只有访问到的对象才会加锁，这个查询使用覆盖索引，并不需要访问主键索引，因此，在主键索引上没有添加任何锁，这解释了为什么会话B的更新语句可以执行成功。
    - 但 session C 要插入一个 (7,7,7) 的记录，就会被 session A 的间隙锁 (5,10) 锁住 这个例子说明，锁是加在索引上的。
    - 执行 for update 时，系统会认为你接下来要更新数据，因此会顺便给主键索引上满足条件的行加上行锁。如果你要用 lock in share mode来给行加读锁避免数据被更新的话，就必须得绕过覆盖索引的优化，因为覆盖索引不会访问主键索引，不会给主键索引上加锁

  - 主键索引范围查询锁

    ![image-20231116181235992](images\nextKey3.png)

    - 开始执行的时候，要找到第一个 id=10 的行，因此本该是 next-key lock(5,10] 。 根据优化 1 ，主键id 上的等值条件，退化成行锁，只加了 id=10 这一行的行锁。
    - 它是范围查询， 范围查找就往后继续找，找到 id=15 这一行停下来，不满足条件，因此需要加next-key lock(10,15] 。
    - session A 这时候锁的范围就是主键索引上，行锁 id=10 和 next-key lock(10,15] 。首次 session A 定位查找id=10 的行的时候，是当做等值查询来判断的，而向右扫描到 id=15 的时候，用的是范围查询判断。

  - 非唯一索引范围查询锁

    ![image-20231116181425335](images\nextKey4.png)

    - 在第一次用 col1=10 定位记录的时候，索引 c 上加了 (5,10] 这个 next-key lock 后，由于索引 col1 是非唯一索引，没有优化规则，也就是 说不会蜕变为行锁，因此最终 sesion A 加的锁是，索引 c 上的 (5,10] 和(10,15] 这两个 next-keylock 。
    - 这里需要扫描到 col1=15 才停止扫描，是合理的，因为 InnoDB 要扫到 col1=15 ，才知道不需要继续往后找了。

  - 唯一索引范围查询锁 bug

    ![image-20231116181528476](images\nextKey5.png)

    - session A 是一个范围查询，按照原则 1 的话，应该是索引 id 上只加 (10,15] 这个 next-key lock ，并且因为 id 是唯一键，所以循环判断到 id=15 这一行就应该停止了。
    - 但是实现上， InnoDB 会往前扫描到第一个不满足条件的行为止，也就是 id=20 。而且由于这是个范围扫描，因此索引 id 上的 (15,20] 这个 next-key lock 也会被锁上。照理说，这里锁住 id=20 这一行的行为，其实是没有必要的。因为扫描到 id=15 ，就可以确定不用往后再找了。

  - 非唯一索引上存在 "  等值 "  的例子

    ![image-20231117145128990](images\nextKey6.png)

    - 给表 t 插入一条新记录：insert into t values(30,10,30);也就是说，现在表里面有两个c=10的行，但是它们的主键值 id 是不同的（分别是 10 和 30 ），因此这两个c=10 的记录之间，也是有间隙的。
    - session A 在遍历的时候，先访问第一个 col1=10 的记录。同样地，根据原则 1 ，这里加的是(col1=5,id=5) 到 (col1=10,id=10) 这个 next-key lock 。
    - 由于c是普通索引，所以继续向右查找，直到碰到 (col1=15,id=15) 这一行循环才结束。根据优化 2 ，这是一个等值查询，向右查找到了不满足条件的行，所以会退化成 (col1=10,id=10) 到 (col1=15,id=15) 的间隙锁。

  - limit 语句加锁

    ![image-20231117145344217](images\nextKey7.png)

    - session A 的 delete 语句加了 limit 2 。表 t 里 c=10 的记录其实只有两条，因此加不加 limit 2 ，删除的效果都是一样的。但是加锁效果却不一样，这是因为，delete 语句明确加了 limit 2 的限制，因此在遍历到 (col1=10, id=30) 这一行之后，满足条件的语句已经有两条，循环就结束了。因此，索引 col1 上的加锁范围就变成了从（ col1=5,id=5)到（ col1=10,id=30) 这个前开后闭区间

  - 一个死锁的例子

    ![image-20231117145527912](images\nextKey8.png)

    - session A 启动事务后执行查询语句加 lock in share mode ，在索引 col1 上加了 next-keylock(5,10] 和间隙锁 (10,15) （索引向右遍历退化为间隙锁）；
    - ession B 的 update 语句也要在索引 c 上加 next-key lock(5,10] ，进入锁等待； 实际上分成了两步，先是加 (5,10) 的间隙锁，加锁成功；然后加 col1=10 的行锁，因为sessionA上已经给这行加上了读锁，此时申请死锁时会被阻塞
    - 然后 session A 要再插入 (8,8,8) 这一行，被 session B 的间隙锁锁住。由于出现了死锁， InnoDB 让session B 回滚

  - [具体可见幻读解决方案网页](https://www.php.cn/faq/554990.html)


## 4.7 MySQL特性

### 4.7.1 乐观锁、悲观锁

- 悲观锁思想就是，当前线程要进来修改数据时，别的线程都得拒之门外

  ```mysql
  select * from User where name=‘jay’ for update
  ```

  - 没用索引/主键的话，select for update 加的就是表锁
  - 查询条件用了索引/主键，会加行锁

- 乐观锁思想就是，有线程过来，先放过去修改，如果看到别的线程没修改过， 就可以修改成功，如 果别的线程修改过，就修改失败或者重试

- 乐观锁一般会使用版本号机制或 CAS 算法实现

### 4.7.2 MySQL事务特性

- ACID
- 原子性（Atomicity）
  - 需要保证多个DML操作是原子的，要么都成功，要么都失败
  - 失败需要对原本执行成功的数据进行回滚，UNDO_LOG表，事务执行过程中，把修改前得数据快照保存到UNDO_LOG里面，一旦出现错误，就直接从UNDO_LOG里面读取数据执行反向操作
- 一致性（Consistency）
  - 表示数据的完整性约束没有被破坏，这个更多是依赖于业务层面的保证，数据 库本身也提供了一些，比如主键的唯一余数，字段长度和类型的保证等等
- 隔离性（Isolation）
  - 是多个并行事务对同一个数据进行操作的时候，如何避免多个事务的干扰导致数据混乱的问题
- 持久性（Durability）
  - 只要事务提交成功，那对于这个数据的结果的影响一定是永久性 的，不能因为宕机或者其他原因导致数据变更失效
  - Redo_LOG文件，这个文件存储了数据被修改之后的值，当我们通过事务对数据 进行变更操作的时候，除了修改内存缓冲区里面的数据以外，还会把本次修改的值追加到 REDO_LOG里面，当提交事务的时候，直接把REDO_LOG日志刷到磁盘上持久化，一旦数据库出现宕机，在Mysql重 启在以后可以直接用REDO_LOG里面保存的重写日志读取出来，再执行一遍从而保证持久性。

### 4.7.3 in和exists区别

- in

  ```mysql
  select * from A where deptId in (select deptId from B)
  ```

  - 先查询部门表 B select deptId from B 再由部门deptId，查询 A 的员工 select * from A where A.deptId = B.deptId

- exists

  ```mysql
  select * from A where exists (select 1 from B where A.deptId = B.deptId)
  ```

  - 因为exists 查询的理解就是，先执行主查询，获得数据后，再放到子查询中做 条件验证，根据验证结果（true 或者false），来决定主查询的数据结果是否得以保留
  - select * from A,先从A 表做循环，select * from B where A.deptId = B.deptId,再从 B 表做循环

- 如果 B 的数据量小于 A，适合使 用 in，如果 B 的数据量大于 A，即适合选择 exists，这就是 in 和 exists 的 区别。

### 4.7.4 MySQL锁

- 根据锁粒度划分

  - 表锁：开销小，加锁快；锁定粒度大，发生锁冲突概率高，并发度最低；不会出现死锁。

    ```mysql
    隐式上锁（默认，自动加锁自动释放）
    select //上读锁
    insert、update、delete //上写锁
    
    显式上锁（手动）
    lock table tableName read;//读锁
    lock table tableName write;//写锁
    
    解锁（手动）
    unlock tables;//所有锁表
    
    lock table test_index read;// 上读锁
    select * from test_index; // session01可以正常读取  
    select * from test_index;// session02可以正常读取
    
    update test_index set index_num = 3 where index_uuid = "000004";//session01报错，因被上读锁不能写操作  
    update test_index set index_num = 3 where index_uuid = "000004";// session02被阻塞
    
    unlock tables;// 解锁
    update test_index set index_num = 3 where index_uuid = "000004";// 更新操作成功
    
    lock table test_index write;// 上写锁
    select * from test_index; // session01可以正常读取  
    select * from test_index;// session02被阻塞
    update test_index set index_num = 4 where index_uuid = "000004";// session01可以正常更新操作  
    update test_index set index_num = 5 where index_uuid = "000004";// session02被阻塞
    unlock tables;// 解锁
    
    select * from test_index;//读取成功
    update test_index set index_num = 5 where index_uuid = "000004";// 更新操作成功
    ```

  - 行锁：开销大，加锁慢；会出现死锁；锁定力度小，发生锁冲突的概率低，并发度高。

    ```mysql
    隐式上锁（默认，自动加锁自动释放）
    
    select //不会上锁
    insert、update、delete //上写锁
    
    显式上锁（手动）
    
    select * from tableName lock in share mode;//读锁
    select * from tableName for update;//写锁
    
    begin;
    select * from test_index where index_uuid = "000004" lock in share mode;// session01上读锁
    select * from test_index where index_uuid = "000004";// session02可以正常读取
    update test_index set index_num = 6 where index_uuid = "000004";// session01可以更新操作  
    update test_index set index_num = 7 where index_uuid = "000004";// session02被阻塞
    commit;
    
    update test_index set index_num = 7 where index_uuid = "000004";// 更新操作成功
    
    begin;
    select * from test_index where index_uuid = "000004" for update;// session01上写锁
    select * from test_index where index_uuid = "000004";// session02可以正常读取
    update test_index set index_num = 9 where index_uuid = "000004";// session01可以更新操作
    update test_index set index_num = 10 where index_uuid = "000004";// session02被阻塞
    rollback;
    
    update test_index set index_num = 10 where index_uuid = "000004";// 更新操作成功
    ```

  - 页锁：开销和加锁速度介于表锁和行锁之间；会出现死锁，锁定粒度介于表锁和行锁之间，并发度一般

  - 为什么行锁上了写锁，别的事务还可以读操作？

    - 因为InnoD‍B有MVCC机制（多版本并发控制），可以使用快照读，而不会被阻塞。

- 根据锁模式划分

  - 记录锁
    - 针对表中的一条记录进行加锁的机制。这种锁类型仅仅锁住一条记录，不会对周围的数据产生影响。记录锁有两种类型：S型记录锁和X型记录锁。S型记录锁用于只读操作，而X型记录锁用于读/写操作
  - gap锁
    - 间隙锁。间隙锁的作用是防止在这个间隙中插入新的记录，从而保证数据的一致性，用于防止幻读
  - next-key锁
    - 是Record锁和Gap锁的组合
  - 意向锁
    - 用于表示某个事务正在锁定一行或将要锁定一行。在MySQL的InnoDB存储引擎中，意向锁分为意向共享锁（IS）和意向排他锁（IX），分别表示事务意图在表中的单个行上设置共享锁或独占锁。
  - 插入意向锁
    - 插入意向锁是一种间隙锁形式的意向锁，在真正执行 INSERT 操作之前设置。当执行插入操作时，总会检查当前插入操作的下一条记录（已存在的主索引节点）上是否存在锁对象，判断是否锁住了 gap。如果锁住了，则判定和插入意向锁冲突，当前插入操作就需要等待，也就是配合上面的间隙锁或者临键锁一起防止了幻读操作。因为插入意向锁是一种意向锁，意向锁只是表示一种意向，所以插入意向锁之间不会互相冲突，多个插入操作同时插入同一个 gap 时，无需互相等待。

- 根据加锁机制划分

  - 乐观锁
  - 悲观锁

- 根据兼容性划分

  - 共享锁
    - 如果一个事务T对数据对象A加上共享锁后，其他事务只能对A再加共享锁，而不能加排他锁，获准共享锁的事务只能读数据，不能修改数据
  - 排他锁
    - 如果一个事务T对数据对象A加上排他锁后，其他事务不能对A再加任何锁，直到T释放A上的排他锁。获准排他锁的事务既能读数据，又能修改数据

### 4.7.5 SQL执行顺序

![image-20231124101656093](images\sqlExeSeq.png)

# 五、Redis

## 5.1 Redis结构

### 5.1.1 Redis简述

- Redis是一个基于内存实现的Key-Value数据结构的Nosql数据库

- 基本数据类型

  - String（字符串）

    - 二进制安全的，可以存储图片或者序列化的对象，值最大存储为512M
    - 应用场景：共享session、分布式锁、计数器、限流

  - Hash（哈希）

    - 在 Redis 中，哈希类型是指 v（值）本身又是一个键值对（k-v）结构
    - 应用场景：缓存用户信息

  - List（列表）

    - 列表（list）类型是用来存储多个有序字符串，一个列表最多可以存储 2^32-1 个元素

    - 应用场景：消息队列，文章列表

      ```
      lpush+lpop=Stack（栈）
      lpush+rpop=Queue（队列）
      lpush+ltrim=Capped Collection（有限集合）
      lpush+brpop=Message Queue（消息队列）
      ```

  - Set（集合）

    - 集合（set）类型也是用来保存多个字符串元素，但是不允许重复元素
    - 应用场景：用户标签，生成随机数抽奖，社交需求

  - Zset（有序集合）

    - 已排序的字符串集合，同时元素不能重复
    - 应用场景：排行榜，社交需求（如用户点赞）

- 特殊数据类型

  - Geo
    - 地理位置定位，用于存储地理位置信息，并对存储的信息进行操作
  - HyperLogLog
    - 用来做基数统计算法（用来统计一组数字中出现频率最高的数字）的数据结构，统计网站的UV（即不同的电脑或网络用户通过互联网访问网站的次数）
  - Bitmaps
    - 用一个比特位来映射某个元素的状态，在Redis 中，它的底层是基于字符串类型实现的 ，可以把 bitmaps 成作一个以比特位为单位的数组

### 5.1.2 Redis速度

- 基于内存实现

- 虚拟内存机制

- 高效的数据结构

  - SDS简单动态字符串
  - 哈希
  - 跳跃表
  - 压缩列表ziplist

- 合理的数据编码

- 合理的线程模型

  - 单线程模型：避免上下文切换

  - I/O多路复用

    - IO多路复用机制，核心思想是让单个线程去监视多个连接，一旦某个连接就绪，也就是触发了读/写 事件，就通知应用程序，去获取这个就绪的连接进行读写操作，也就是在应用程序里面可以使用单个线程同时处理多个客户端连接，在对系统资源消耗较少的情况下 提升服务端的链接处理数量

    - 客户端请求到服务端后，此时客户端在传输数据过程中，为了避 免Server端在read客户端数据过程中阻塞，服务端会把该请求注册到Selector复路器上，服务端此时 不需要等待，只需要启动一个线程，通过selector.select()阻塞轮询复路器上就绪的channel即可， 也就是说，如果某个客户端连接数据传输完成，那么select()方法会返回就绪的channel，然后执行 相关的处理

      ![image-20231124104437800](images\selector.png)

    - 常见的IO多路复用机制的实现方式有： select 、poll、epoll

    - 其中select和poll是基于轮询的方式去获取就绪连接

    - epoll是基于事件驱动的方式获取就绪连接

- IO多路复用详解

  - select

    - 采用轮询和遍历的方式。也就是说，在客户端操作服务器时，会 创建三种文件描述符，简称FD。分别是writefds（写描述符）、readfds（读描述符）和 exceptfds （异常描述符）。
    - 而select会阻塞监视这三种文件描述符，等有数据、可读、可写、出异常或超时都会返回
    - 返回后通过遍历fdset，也就是文件描述符的集合，来找到就绪的FD，然后，触发相应的IO操作
    - 优点是跨平台支持性好，几乎在所有的平台上支持
    - 由于select是采用轮询的方式进行全盘扫描，因此，随着FD数量增多而导 致性能下降
    - 每次调用select()方法，都需要把FD集合从用户态拷贝到内核态，并进行遍历。而操作系统对单个进程打开的FD数量是有限制的，一般默认是1024个，在IO吞吐量巨大的情况下，效率提升仍然有限。

  - poll

    - poll 模型的原理与select模型基本一致，也是采用轮询加遍历，唯一的区别就是 poll 采用链表 的方式来存储FD
    - 优点是没有最大FD的数量限制
    - 缺点和select一样，也是采用轮询方式全盘扫描，同样也会随着FD数量增多而导致性能下降

  - epoll

    - epoll模型是采用事件通知机制来触发相关的IO操作。它没有FD个数限制，而且从用户态拷贝 到内核态只需要一次。它主要通过系统底层的函数来注册、激活FD，从而触发相关的 IO 操作
    - epoll_create()
      - 在系统启动时，会在Linux内核里面申请一个B+树结构的文件系统， 然后，返回epoll对象，也是一个FD
    - epoll_ctl()
      - 每新建一个连接的时候，会同步更新epoll对象中的FD，并且绑定一个 callback回调函数
    - epoll_wait()
      - 轮询所有的callback集合，并触发对应的 IO操作
    - epoll模型最大的优点是将轮询改成了回调，大大提高了CPU执行效率，也不会随FD数量 的增加而导致效率下降。当然，它也没有FD数量限制，也就是说，它能支持的FD上限是操作系统的最大文件句柄数。一般而言，1G 内存大概支持 10 万个句柄。分布式系统中常用的组件如Redis、 Nginx都是优先采用epoll模型
    - 缺点，只能在Linux下工作

    ![image-20231124110249439](images\IOMultiplexing.png)

### 5.1.3 Redis常见问题

- 缓存穿透
  - 查询一个一定不存在的数据，由于缓存是不命中时需要从数据库查询，查不到数据则不写入缓存，这将导致这个不存在的数据每次请求都要到 数据库去查询，进而给数据库带来压力
  - 原因
    - 业务不合理的设计，比如大多数用户都没开守护，但是你的每个请求都去缓存，查询某个 userid 查询有没有守护
    - 业务/运维/开发失误的操作，比如缓存和数据库的数据都被误删除了
    - 黑客非法请求攻击，比如黑客故意捏造大量非法请求，以读取不存在的业务数据
  - 方案
    - 如果是非法请求，我们在 API 入口，对参数进行校验，过滤非法
    - 如果查询数据库为空，我们可以给缓存设置个空值，或者默认值。但是如有有写请求进来话，需要更新缓存，以保证缓存一致性，同时，最后给缓存设置适当过期时间。（业务上比较常用，简单有效）
    - 使用布隆过滤器快速判断数据是否存在。即一个查询请求过来时，先通过布隆过滤器判断值是否存在，存在才继续往下查。它由初始值为 0的位图数组和 N 个哈希函数组成。一个对一 个 key 进行N 个 hash 算法获取 N 个值，在比特数组中将这 N 个值散列后设定 为 1，然后查的时候如果特定的这几个位置都为 1，那么布隆过滤器判断该 key 存在，Redis和单机版BloomFilter都有布隆过滤器
- 缓存雪崩
  - 指缓存中数据大批量到过期时间，而查询数据量巨大，请求都直接 访问数据库，引起数据库压力过大甚至 down 机
  - 原因+方案
    - 缓存雪奔一般是由于大量数据同时过期造成的，对于这个原因，可通过均匀设置过 期时间解决，即让过期时间相对离散一点。如采用一个较大固定值+一个较小的随机值，5 小时+0 到 1800 秒酱紫
    - Redis 故障宕机也可能引起缓存雪奔。这就需要构造 Redis 高可用集群
- 缓存击穿
  - 指热点key 在某个时间点过期时候，而恰好在这个时间点对这个 Key 有大量的并发请求过来，从而大量的请求打到 db。
  - 缓存击穿看着有点像缓存雪崩，其实它两区别是，缓存雪奔是指数据库压力过大甚至 down 机，缓存击穿只是大量并发请求到了 DB 数据库层面。可以认为击穿是 缓存雪奔的一个子集吧
  - 使用互斥锁方案。缓存失效时，而是先使用某些带成 功返回的原子操作命令，如(Redis ✁ setnx）去操作，成功的时候，再去加载 db数据库数据和设置缓存。否则就去重试获取缓存
  - ”永不过期”，是指没有设置过期时间，但是热点数据快要过期时，异步线程去更新和设置过期时间。
- 热key
  - 把访问频率高的 key，称为热点key
  - 如果某一热点 key 的请求到服务器主机时，由于请求量特别大，可能会导致主机资源不足，甚至宕机，从而影响正常的服务
  - 原因
    - 用户消费的数据远大于生产的数据，如秒杀、热点新闻等读多写少的场景
    - 请求分片集中，超过单 Redis 服务器的性能，比如固定名称 key，Hash 落入同 一台服务器，瞬间访问量极大，超过机器瓶颈，产生热点 Key 问题。
  - 识别热key
    - 凭经验判断哪些是热 Key；
    - 客户端统计上报；
    - 服务代理层上报
  - 方案
    - Redis 集群扩容：增加分片副本，均衡读流量
    - 将热 key 分散到不同的服务器
    - 使用二级缓存，即 JVM 本地缓存,减少 Redis 的读请求。

### 5.1.4 Redis过期策略

- 常用过期策略
  - 定时过期
    - 每个设置过期时间的 key 都需要创一个定时器，到过期时间就会立即对 key 进行清除。该策略可以立即清除过期的数据，对内存很友好；但是会占用大量的CPU 资源去处理过期的数据，从而影响缓存的响应时间和吞吐量。
  - 惰性过期
    - 只有当访问一个 key 时，才会判断该 key 是否已过期，过期则清除。该策略可 以最大化地节省 CPU 资源，却对内存非常不友好。极端情况可能出现大量过期 key 没有再次被访问，从而不会被清除，占用大量内存。
  - 定期过期
    - 每隔一定时间，会扫描一定数量数据库expires 字典中一定数量key，并清除其中已过期key。该策略是前两者一个折中方案。通过调整定时扫描时间间隔和每次扫描限定耗时，可以在不同情况下使得 CPU 和内存 资源达到最优平衡效果
    - expires 字典会保存所有设置了过期时间key过期时间数据，其中，key 是指向键空间中某个键指针，value 是该键毫秒精度UNIX 时间戳表 示过期时间。键空间是指该 Redis 集群中保存所有键
- Redis 中同时使用了惰性过期和定期过期两种过期策略

### 5.1.5 Redis内存淘汰策略

- LRU
  - 最近最少使用淘汰算法，其关键在于看页面最后一次被使用到发生替换的时间长短，时间越长，页面就会被置换，实际操作中，每当缓存命中（即缓存数据被访问），则将数据移到链表头部；当链表满的时候，将链表尾部的数据丢弃
- LFU
  - 最不经常使用淘汰算法，其关键在于看一定时间段内页面被使用的频率（次数），使用频率越低，页面就会被置换，在实际操作中，新数据插入到链表头部；每当缓存命中（即缓存数据被访问），则将数据移到链表头部；当链表满的时候，将链表尾部的数据丢弃。
- LRU和LFU的主要区别在于判断淘汰页面的依据不同。LRU看的是最后一次使用时间，而LFU看的是一段时间内的使用频率。
- 内存淘汰策略
  - volatile-lru
    - 当内存不足以容纳新写入数据时，从设置了过期时间key 中 使用 LRU（最近最少使用）算法进行淘汰
  - allkeys-lru
    - 当内存不足以容纳新写入数据时，从所有 key 中使用 LRU（最近 最少使用）算法进行淘汰
  - volatile-lfu
    - 4.0 版本新增，当内存不足以容纳新写入数据时，在过期 key 中，使用 LFU 算法进行删除 key
  - allkeys-lfu
    - 4.0 版本新增，当内存不足以容纳新写入数据时，从所有 key 中 使用 LFU 算法进行淘汰
  - volatile-random
    - 当内存不足以容纳新写入数据时，从设置了过期时间 key 中，随机淘汰数据
  - allkeys-random
    - 当内存不足以容纳新写入数据时，从所有 key 中随机淘汰 数据
  - volatile-ttl
    - 当内存不足以容纳新写入数据时，在设置了过期时间 key 中， 根据过期时间进行淘汰，越早过期优先被淘汰
  - noeviction
    - 默认策略，当内存不足以容纳新写入数据时，新写入操作会报错。

### 5.1.6 Redis持久化

- RDB

  ![image-20231124132347481](images\RDB.png)

  - 通过快照的方式来实现持久化的，也就是说会根据快照的触发条件，把内存里面的数据快照写入到磁盘， 以二进制的压缩文件进行存储
  - RDB快照的触发方式有很多，比如执行bgsave命令触发异步快照，执行save命令触发同步快照，同步快照会阻塞客户端的执行指令
  - RDB是每隔一段时间触发持久化，因此数据安全性低

- AOF

  ![image-20231124132521484](images\AOF.png)

  - 根据redis.conf文件里面的配置，自动触发bgsave主从复制的时候触发AOF持久化，它是一种近乎 实时的方式，把Redis Server执行的事务命令进行追加存储

  - 客户端执行一个数据变更的操作，Redis Server就会把这个命令追加到aof缓冲区的 末尾，然后再把缓冲区的数据写入到磁盘的AOF文件里面，至于最终什么时候真正持久化到磁盘， 是根据刷盘的策略来决定

  - 为AOF这种指令追加的方式，会造成AOF文件过大，带来明显的IO性能问题，所以Redis针 对这种情况提供了AOF重写机制，也就是说当AOF文件的大小达到某个阈值的时候，就会把这个文 件里面相同的指令进行压缩

    ```redis
    set name mic
    set name mic1
    set name mic2
    set name mic3
    AOF重写
    set name mic3
    ```

  - AOF可以做到实时持久化，数据安全性较高 RDB文件默认采用压缩的方式持久化，AOF存储的是执行指令，所以RDB在数据恢复的时候性能比 AOF要好

## 5.2 Redis高可用

### 5.2.1 主从模式

- Redis 主从概念

  - Redis 主从模式，就是部署多台 Redis 服务器，有主库和从库，它们之间通过主 从复制，以保证数据副本一致。
  - 主从库之间采用是读写分离方式，其中主库负责读操作和写操作，从库则负责读操作
  - 如果 Redis 主库挂了，切换其中从库成为主库

- Redis 主从同步过程

  ![image-20231124134110767](images\redisMasterSlave.png)

  - 一阶段：主从库间建立连接、协商同步
    - 从库向主库发送 psync 命令，告诉它要进行数据同步
    - 主库收到 psync 命令后,响应 FULLRESYNC 命令（它表示第一次复制采用是全量复制），并带上主库 runID 和主库目前复制进度 offset。
  - 二阶段：主库把数据同步到从库，从库收到数据后，完成本地加载
    - 主库执行 bgsave 命令，生成 RDB 文件，接着将文件发给从库。从库接收到 RDB 文件后，会先清空当前数据库，然后加载 RDB 文件
    - 主库把数据同步到从库过程中，新来写操作，会记录到 replication buffer。
  - 三阶段，主库把新写命令，发送到从库
    - 主库完成 RDB 发送后，会把 replication buffer 中修改操作发给从库，从 库再重新执行这些操作。这样主从库就实现同步啦。

- Redis 主从的一些注意点

  - 主从数据不一致

    - 因为主从复制是异步进行，如果从库滞后执行，则会导致主从数据不一致
    - 主从库网路延迟
    -  从库收到了主从命令，但是它正在执行阻塞性命令（如 hgetall等）

  - 解决主从数据不一致

    - 可以换更好硬件配置，保证网络畅通
    - 监控主从库间复制进度
    - 读取过期数据

  - 一主多从，全量复制时主库压力问题

    - 主库 fork 进程生成 RDB，这个 fork 过 程是会阻塞主线程处理正常请求。同时，传输大RDB 文件也会占用主库 网络宽带

    - 可以使用主-从-从模式解决。什么是主从从模式呢？其实就是部署主从集群时， 选择硬件网络配置比较好一个从库，让它跟部分从库再立主从关系

      ![image-20231124135451705](images\redisMasterSlave2.png)

  - 主从网络断了

    - 当主从库断开连接后，主库会把断连期间收到写操作命令，写入 replication buffer，同时也会把这些操作命令写入repl_backlog_buffer 这个缓冲区。repl_backlog_buffer 是一个环形缓冲区，主库会记录自己写到位置，从库则会记录自己已经读到位置，主从库重连后，就是利用 repl_backlog_buffer 实现增量复制。

- Redis主从同步方式

  - 全量同步
    - 全量同步，一般发生在第一次建立主从关系、或者跟主断开时间比较久的场景
  - 增量同步
    - 数据同步，slave是定时会发起的，假如每次同步，都把主的所有数据都进行同步，那么性 能会很慢，大部分时候，slave可能只跟master相差一部分数据。那么只需要同步这部分 数据
    - slave发起同步的时候，还会带有上次同步的偏移量，然后跟master的最新的偏移量比较， 如果相差的数据在master的积压缓存（一个专门存储master最新数据并且会覆盖的内存区 间）能查询到的话，那么只需要把相差的数据同步给slave。这就叫做增量同步

- [Redis主从搭建过程](https://zhuanlan.zhihu.com/p/647155496)

  - master配置文件

    ```bash
    # master
    #端口号
    port 6379
    
    #设置客户端连接后进行任何其他指定前需要使用的密码
    requirepass 123456
    
    #daemonize no 将daemonize yes注释起来或者 daemonize no设置，因为该配置和docker run中-d参数冲突，会导致容器一直启动失败
    daemonize no
    
    # 任何主机都可以连接到redis
    bind 0.0.0.0
    
    #是否开启保护模式，默认开启。要是配置里没有指定bind和密码。开启该参数后，redis只会本地进行访问，拒绝外部访问。
    protected-mode no
    
    # 默认情况下，redis会在后台异步的把数据库镜像备份到磁盘，但是该备份是非常耗时的，而且备份也不能很频繁，如果发生诸如拉闸限电、拔插头等状况，那么将造成比较大范围的数据丢失。
    # 所以redis提供了另外一种更加高效的数据库备份及灾难恢复方式。
    # 开启append only模式之后，redis会把所接收到的每一次写操作请求都追加到appendonly.aof文件中，当redis重新启动时，会从该文件恢复出之前的状态。
    # 但是这样会造成appendonly.aof文件过大，所以redis还支持了BGREWRITEAOF指令，对appendonly.aof 进行重新整理。
    # 你可以同时开启asynchronous dumps 和 AOF
    appendonly yes
    ```

  - slave配置文件

    ```bash
    # 连接ip为172.17.0.4的master节点的redis
    SLAVEOF 172.17.0.4 6379
    
    # slave1
    port 6380
    
    #设置客户端连接后进行任何其他指定前需要使用的密码
    requirepass 123456
    
    # 这一步很重要！主从认证密码，否则主从不能同步！！
    masterauth 123456
    
    #daemonize no 将daemonize yes注释起来或者 daemonize no设置，因为该配置和docker run中-d参数冲突，会导致容器一直启动失败
    daemonize no
    
    # 任何主机都可以连接到redis
    bind 0.0.0.0
    
    #是否开启保护模式，默认开启。要是配置里没有指定bind和密码。开启该参数后，redis只会本地进行访问，拒绝外部访问。
    protected-mode no
    
    # 开启AOF
    appendonly yes
    ```
    
  - docker 启动
  
    ```bash
    docker run -p 6379:6379 \
     -v $PWD/data6379:/data  \
     -v $PWD/redis6379.conf:/etc/redis/redis.conf  \
     --privileged=true \
     --name redis-6379 \
     -d hub.c.163.com/library/redis redis-server /etc/redis/redis.conf
    ```
  
  - docker 查看容器
  
    ```bash
    docker exec -it redis-6379 redis-cli -p 6379
    # 查看节点ip
    docker inspect c5dd40f83b74
    ```

### 5.2.2 Redis哨兵

主从模式中，一旦主节点由于故障不能提供服务，需要人工将从节点晋升为主 节点，同时还要通知应用方更新主节点地址

- 哨兵模式

  - 就是由一个或多个哨兵实例组成哨兵系统，它可以监视所有Redis 主节点和从节点，并在被监视主节点进入下线状态时，自动将下线主服务器属下某个从节点升级为新主节点。一般使用多个哨兵来进行 监控 Redis 节点，并且各个哨兵之间还会进行监控

    ![image-20231124155549909](images\sentinel.png)

- 主观下线和客观下线

  - 主观下线
    - 哨兵进程向主库、从库发送 PING 命令，如果主库或者从库没有在规定时间内响 应 PING 命令，哨兵就把它标记为主观下线。

  - 客观下线
    - 如果是主库被标记为主观下线，则正在监视这个主库所有哨兵要以每秒一次频 率，以确认主库是否真进入了主观下线。 当有多数哨兵（一般少数服从多数， 由 Redis 管理员自行设定一个值）在指定时间范围内确认主库确进入了主 观下线状态，则主库会被标记为客观下线，就可以做主从切换

- 哨兵选主

  - 过滤和打分。其实就是在多个从库中，先按照一定筛选条件，把不符合条件从库过滤掉。然后再按照一定规则，给剩下从库逐个打分，将得分最高从库选为新主库

- 哨兵执行主从切换

  - 标记主库客观下线这个哨兵，紧接着向其他哨兵发送命令，再发起投票，希望它可以来执行主从切换。这个投票过程称为 Leader 选举

- [Redis哨兵搭建过程](https://zhuanlan.zhihu.com/p/647382777)

- [Redis哨兵搭建过程2](https://blog.51cto.com/u_16099189/7570232)

  - sentinel.conf配置文件

    ```bash
    # 修改哨兵的监听端口
    port 26379
    
    # 让sentinel服务后台运行(docker的话需要设置为no，非docker运行设置为yes, 因为docker有个-d属性就是让在后台运行的)
    daemonize no
    
    # 当Redis哨兵以守护进程的方式运行的时候,默认会把pid文件放在/var/tmp/sentinel1.log,也可以配置到其他地址，多个哨兵需要重命名文件。
    pidfile /var/run/redis-sentinel.pid
    
    # 修改日志文件的路径
    logfile "/var/tmp/sentinel.log"
    
    # 哨兵sentinel监控的redis主节点的
    ## ip：主机ip地址[docker就是docker内部ip]
    ## port：redis端口号
    ## master-name：可以自己命名的主节点名字（只能由字母A-z、数字0-9 、这三个字符".-_"组成。）
    ## quorum：当这些quorum个数sentinel哨兵认为master主节点失联,那么这时客观上认为主节点失联了,就进行failover(故障转移)
    # sentinel monitor <master-name> <ip> <redis-port> <quorum>
    sentinel monitor mymaster 192.168.51.121 6379 2
    
    # 当在Redis实例中开启了requirepass <foobared>，所有连接Redis实例的客户端都要提供密码。
    sentinel auth-pass mymaster 123456
    
    #超过5秒master还没有连接上，则认为master已经停止
    sentinel down-after-milliseconds mymaster 5000
    
    # 注释掉以下参数，当前redis版本6.2.1，开启参数启动哨兵启报错
    # >>> 'SENTINEL master-reboot-down-after-period mymaster 0'
    # Unrecognized sentinel configuration statement
    # SENTINEL master-reboot-down-after-period mymaster 0
    ```

  - docker启动

    ```bash
    docker run -p 26379:26379 \
    --name sentinel1 \
    -v /etc/redis-sentinel:/usr/local/etc/redis \
    -v /var/tmp/sentinel1.log:/var/tmp/sentinel.log \
    -d hub.c.163.com/library/redis redis-sentinel /usr/local/etc/redis/sentinel1.conf
    ```


### 5.2.3 Redis Cluster 集群

哨兵模式基于主从模式，实现读写分离，它还可以自动切换，系统可用性更高。 但是它每个节点存储数据是一样，浪费内存，并且不好在线扩容。Redis 切片集群将数据分散来存储

![image-20231127163445426](images\RedisCluster.png)

- 哈希槽（Hash Slot）

  - Redis Cluster 方案采用哈希槽（Hash Slot），来处理数据和实例之间映射关系
  - 一个切片集群被分为 16384个 slot（槽），每个进入 Redis 键值对，根据 key 进行散列，分配到这 16384 插槽中一个。使用哈希映射也比较简单， 用CRC16算法计算出一个 16bit值，再对 16384取模。数据库中每个键都属 于这 16384 个槽其中一个，集群中每个节点都可以处理这 16384 个槽。 集群中每个节点负责一部分哈希槽，假设当前集群有 A、B、C3 个节点， 每个节点上负责哈希槽数 =16384/3，那么可能存在一种分配
    - 节点A 负责 0~5460 号哈希槽
    - 节点B 负责 5461~10922 号哈希槽
    - 节点C 负责 10923~16383 号哈希槽

- MOVED 重定向和ASK重定向

  - 在 Redis cluster 模式下，节点对请求处理过程如下

    1. 通过哈希槽映射，检查当前 Redis key 是否存在当前节点
    2. 若哈希槽不由自身节点负责，就返回 MOVED 重定向
    3. 若哈希槽确实由自身负责，且 key 在 slot 中，则返回该 key 对应结果
    4. 若 Redis key 不存在此哈希槽中，检查该哈希槽否正在迁出（MIGRATING）？
    5. 若 Redis key 正在迁出，返回ASK 错误重定向客户端到迁移目的服务器上
    6. 若哈希槽未迁出，检查哈希槽是否导入中？
    7. 若哈希槽导入中且有 ASKING 标记，则直接操作，否则返回 MOVED 重定向

  - MOVED重定向

    - Redis Custer中，客户端可以向集群中任意节点发送请求。此时当前节点先对Key进行CRC 16计算，然后按16384取模确定Slot槽。确定该Slot槽所对应的节点，如果该Slot是当前节点负责，且该Key存在于该Slot中，则直接返回该Key对应的结果；如果该Slot不是当前节点负责，则返回MOVED重定向告知客户端对应的节点地址信息

      ![image-20231127165700128](images\redisMoved.png)

  - ASK 重定向

    - Ask重定向发生于Redis集群进行伸缩（扩容/缩容）时，由于此时会进行Slot槽迁移。当我们去源节点访问时，数据可能已经迁移到目标节点中。故此时需要借助Ask重定向来解决该问题。具体地，在将A节点中的某个槽迁移到B节点过程中：

      当A节点该Slot槽设置为 MIGRATING迁出状态 后，A节点依然可以接受有关此Slot槽的查询命令。如果该Key依然存在于该Slot槽中，则直接返回结果；如果该Key不存在于该Slot槽，说明该Key可能已经迁移到目的节点B当中了，故其会返回ASK重定向以告知客户端该Slot槽迁入的目的节点B地址信息
      当B节点该Slot槽设置为 IMPORTING迁入状态 时，B节点可以接受有关此哈希槽的查询命令。但前提是客户端向B节点发送该Key的查询命令之前，必须要先发送ASKING命令。否则，B节点会返回MOVED重定向以告知客户端A节点的地址信息

    ![image-20231127170034987](images\redisAsk.png)

- Cluster 集群节点通讯协议：Gossip

  - Gossip 协议基本思想：一个节点想要分享一些信息给网络中其他一些节点。 于是，它周期性随机选择一些节点，并把信息传递给这些节点。这些收到信 息节点接下来会做同样事情，即把这些信息传递给其他一些随机选择节 点。一般而言，信息会周期性传递给 N个目标节点，而不只是一个，这个N被称为fanout

  - Redis Cluster 集群通过 Gossip 协议进行通信，节点之前不断交换信息，交换 信息内容包括节点出现故障、新节点加入、主从节点变更信息、slot 信息等等。gossip 协议包含多种消息类型，包括 ping，pong，meet，fail

    ![image-20231127170417542](images\gossip.png)

    - meet 消息：通知新节点加入。消息发送者通知接收者加入到当前集群，meet 消息通信正常完成后，接收节点会加入到集群中并进行周期性ping、pong 消息交换
    - ping 消息：节点每秒会向集群中其他节点发送 ping 消息，消息中带有自己已知两个节点地址、槽、状态信息、最后一次通信时间等
    - pong 消息：当接收到 ping、meet 消息时，作为响应消息回复给发送方确认消息 正常通信。消息中同样带有自己已知两个节点信息
    - fail 消息：当节点判定集群内另一个节点下线时，会向集群内广播一个 fail 消息， 其他节点接收到 fail 消息之后把对应节点更新为下线状态

- 故障转移

  - redis 集群通过 ping/pong 消息，实现故障发现。这个环境包括主观下线和客 观下线

  - 主观下线

    - 某个节点认为另一个节点不可用，即下线状态，这个状态并不是最终故障判定，只能代表一个节点意见，可能存在误判情况

      ![image-20231127170739589](images\redisSubjectiveOffline.png)

      

  - 客观下线

    - 指标记一个节点真正下线，集群内多个节点都认为该节点不可用， 从而达成共识结果。如果持有槽主节点故障，需要为该节点进行故障转移

      ![image-20231127171159486](images\redisObjectivelyOffline.png)

- 故障恢复

  - 故障发现后，如果下线节点主节点，则需要在它从节点中选一个替换它，以保证集群高可用。流程如下
    1. 资格检查：检查从节点是否具备替换故障主节点条件
    2. 准备选举时间：资格检查通过后，更新触发故障选举时间
    3. 发起选举：到了故障选举时间，进行选举
    4.  选举投票：只有持有槽主节点才有票，从节点收集到足够选票（大于一半）， 触发替换主节点操作

- [Redis Cluster集群搭建过程](https://zhuanlan.zhihu.com/p/655514905)

  - Docker Compose

    ```bash
    yum install -y docker-compose
    ```

  - Docker Compose 3主3从的Redis Cluster集群

    ```yml
    # 构建一个3主3从的Redis集群
    # Compose 版本
    version: '3.8'
    
    # 定义服务
    services:
    
      Redis-Service-1:
        image: hub.c.163.com/library/redis
        container_name: node-1
        command: [ "redis-server", "/etc/redis/redis.conf" ]
        ports:
          - "6371:6379"
        volumes:
          - /etc/redis-cluster/redis.conf:/etc/redis/redis.conf
        networks:
          # 使用名为redis_cluster_3m3s_net的网络并设置容器IP
          redis_cluster_3m3s_net:
            ipv4_address: 120.120.120.11
    
      Redis-Service-2:
        image: hub.c.163.com/library/redis
        container_name: node-2
        command: [ "redis-server", "/etc/redis/redis.conf" ]
        ports:
          - "6372:6379"
        volumes:
          - /etc/redis-cluster/redis.conf:/etc/redis/redis.conf
        networks:
          # 使用名为redis_cluster_3m3s_net的网络并设置容器IP
          redis_cluster_3m3s_net:
            ipv4_address: 120.120.120.12
    
      Redis-Service-3:
        image: hub.c.163.com/library/redis
        container_name: node-3
        command: [ "redis-server", "/etc/redis/redis.conf" ]
        ports:
          - "6373:6379"
        volumes:
          - /etc/redis-cluster/redis.conf:/etc/redis/redis.conf
        networks:
          # 使用名为redis_cluster_3m3s_net的网络并设置容器IP
          redis_cluster_3m3s_net:
            ipv4_address: 120.120.120.13
    
      Redis-Service-4:
        image: hub.c.163.com/library/redis
        container_name: node-4
        command: [ "redis-server", "/etc/redis/redis.conf" ]
        ports:
          - "6374:6379"
        volumes:
          - /etc/redis-cluster/redis.conf:/etc/redis/redis.conf
        networks:
          # 使用名为redis_cluster_3m3s_net的网络并设置容器IP
          redis_cluster_3m3s_net:
            ipv4_address: 120.120.120.14
    
      Redis-Service-5:
        image: hub.c.163.com/library/redis
        container_name: node-5
        command: [ "redis-server", "/etc/redis/redis.conf" ]
        ports:
          - "6375:6379"
        volumes:
          - /etc/redis-cluster/redis.conf:/etc/redis/redis.conf
        networks:
          # 使用名为redis_cluster_3m3s_net的网络并设置容器IP
          redis_cluster_3m3s_net:
            ipv4_address: 120.120.120.15
    
      Redis-Service-6:
        image: hub.c.163.com/library/redis
        container_name: node-6
        command: [ "redis-server", "/etc/redis/redis.conf" ]
        ports:
          - "6376:6379"
        volumes:
          - /etc/redis-cluster/redis.conf:/etc/redis/redis.conf
        networks:
          # 使用名为redis_cluster_3m3s_net的网络并设置容器IP
          redis_cluster_3m3s_net:
            ipv4_address: 120.120.120.16
    
    # 定义网络
    networks:
      # 定义一个名为redis_cluster_3m3s_net的网络
      redis_cluster_3m3s_net:
        ipam:
          config:
            # 设置网段
            - subnet: 120.120.120.0/24
    ```

  - redis.conf

    ```bash
    ..
    
    # 注释bind配置项
    # bind 127.0.0.1 -::1
    
    # 设为 no, 关闭保护模式
    protected-mode no
    
    # 端口设为6379
    port 6379
    
    # 设为no, 因为docker启动时会通过-d参数来让其实现后台运行
    daemonize no
    
    # 修改数据库数量, 用于验证配置文件是否生效
    databases 5
    
    # 设置访问主库时的密码
    masterauth "52996"
    
    # 设置Redis密码
    requirepass 52996
    
    # 使能集群模式
    cluster-enabled yes
    
    # 集群是否要求槽全覆盖
    # yes：当负责某个槽的主库下线且没有相应的从库进行故障恢复时，集群整体不可用。即其他槽的节点在线也无法访问
    # no：当负责某个槽的主库下线且没有相应的从库进行故障恢复时，集群仍然可用。即可访问其他槽的数据
    cluster-require-full-coverage yes
    
    ...
    ```

  - redis配置cluster

    ```bash
    docker exec -it node-1 \
        redis-cli -p 6379 -a 52996 --cluster create \
        120.120.120.11:6379 120.120.120.12:6379 \
        120.120.120.13:6379 120.120.120.14:6379 \
        120.120.120.15:6379 120.120.120.16:6379 \
        --cluster-replicas 1
    ```

    Redis Cluster集群中的从节点，官方默认设置的是不分担读请求的、只作备份和故障转移用,当有请求读向从节点时，会被重定向对应的主节点来处理

## 5.3 Redis分布式锁

### 5.3.1 redis命令分布式锁

- 不推荐写法

  - 命令setnx + expire分开写

    - setnx： Redis实现分布式锁的核心便在于SETNX命令，它是SET if Not eXists的缩写，如果键不存在，则将键设置为给定值，在这种情况下，它等于SET；当键已存在时，不执行任何操作；成功时返回1，失败返回0

    - 代码写法

      ```java
      if（jedis.setnx(key,lock_value) == 1）{ //加锁
      	expire（key，100）; //设置过期时间
      	try {
      		do something / / 业务请求
      	} catch(){
          } finally {
      		jedis.del(key); //释放锁
      	}
      }
      ```

    - 如果执行完 setnx加锁，正要执行 expire 设置过期时间时，进程 crash 掉或者 要重启维护了，那这个锁就“长生不老”了，别的线程永远获取不到锁，所以 分布式锁不能这么实现

  - setnx + (value 值 -> 过期时间)

    - 代码实现

      ```java
      long expires = System.currentTimeMillis() + expireTime; //系统时间+设置过期时间String
      String expiresStr = String.valueOf(expires);
      // 如果当前锁不存在，返回加锁成功
      if (jedis.setnx(key, expiresStr) == 1) {
      	return true;
      }
      // 如果锁已经存在，获取锁过期时间
      String currentValueStr = jedis.get(key);
      // 如果获取到过期时间，小于系统当前时间，表示已经过期
      if (currentValueStr != null && Long.parseLong(currentValueStr) < System.currentTimeMillis()) {
      	// 锁已过期，获取上一个锁过期时间，并设置现在锁过期时间
      	String oldValueStr = jedis.getSet(key, expiresStr);
      	if (oldValueStr != null && oldValueStr.equals(currentValueStr)) {
      		// 考虑多线程并发情况，只有一个线程设置值和当前值相同，它才可以加锁
      		return true;
      	}
      }
      //其他情况，均返回加锁失败
      return false;
      ```

    - 过期时间客户端自己生成，分布式环境下，每个客户端时间必须同步

    - 没有保存持有者唯一标识，可能被别客户端释放/解锁

    - 锁过期时候，并发多个客户端同时请求过来，都执行了 jedis.getSet()，最终只能 有一个客户端加锁成功，但该客户端锁过期时间，可能被别客户端覆盖

  - set 扩展命令（set ex px nx）

    - SET key value [EX seconds] [PX milliseconds] [NX|XX]

    - 生存时间（TTL，以秒为单位）

    - EX second ：设置键的过期时间为 second 秒，SET key value EX second 效果等同于 SETEX key second value 

    - PX millisecond ：设置键的过期时间为millisecond毫秒，SET key value PX millisecond 效果等同于 PSETEX key millisecond value 。

    - NX ：只在键不存在时，才对键进行设置操作，SET key value NX 效果等同于 SETNX key value 。

    - XX ：只在键已经存在时，才对键进行设置操作。

    - 代码实现

      ```java
      if（jedis.set(key, lock_value, "NX", "EX", 100s) == 1）{ //加锁
          try {
              do something // 业务处理
          } catch() {
              
          } finally {
              jedis.del(key); // 释放锁
          }
      }
      ```

    - 锁过期释放了，业务还没执行完【可以使用看门狗操作，在业务处理中延长执行时间】

    - 锁被别的线程误删

- 推荐写法

  - set ex px nx + 校验唯一随机值，再删除

    - 代码实现

      ```java
      if（jedis.set(key, uni_request_id, "NX", "EX", 100s) == 1）{ //加锁
      	try {
      		do something / / 业务处理
      	} catch(){
      	} finally {
      		//判断是不是当前线程加锁,才释放
      		if (uni_request_id.equals(jedis.get(key))) {
      			jedis.del(key); //释放锁
      		}
      	}
      }
      ```

    - 但是释放锁代码非原子性，可以优化成lua脚本执行

### 5.3.2 Redisson

分布式锁可能存在锁过期释放，业务没执行完问题。可以给获得锁线程，开启一个定时守护线程，每隔一段时间检查锁否还存在，存在则对锁过期时间延长，防止锁过期提前释放。

![image-20231129102053192](images\Redisson.png)

- Redlock
  1. 按顺序向 5 个 master 节点请求加锁
  2. 根据设置超时时间来判断，要不要跳过该 master 节点。
  3. 如果大于等于三个节点[N/2 + 1]加锁成功，并且使用时间小于锁有效期，即可认定加锁成功
  4. 如果获取锁失败，解锁

## 5.4 Redis和MySQL

### 5.4.1 双写一致性

- 缓存延时双删

  1. 先删除缓存
  2. 再更新数据库
  3.  休眠一会（比如 1 秒），再次删除缓存（存在删除缓存失败问题）

- 删除缓存重试机制

  ![image-20231129102618643](images\retryDel.png)

- 读取binlog 异步删除缓存

  - 可以使用阿里canal 将 binlog 日志采集发送到 MQ 队列里面

  - 然后通过 ACK 机制确认处理这条更新消息，删除缓存，保证数据缓存一致性

    ![image-20231129103050168](images\DelBinlog.png)

## 5.5 Redis机制

### 5.5.1 Redis多线程机制

- Redis6.0 之前，Redis 在处理客户端请求时，包括读 socket、解析、执行、 写socket 等都由一个顺序串行主线程处理，这就所谓“单线程”
- redis 使用多线程并非完全摒弃单线程，redis 还使用单线程模型来处理 客户端请求，只使用多线程来处理数据读写和协议解析，执行命令还 使用单线程。 这样做目的是因为 redis性能瓶颈在于网络 IO 而非 CPU，使用多线程能 提升 IO 读写效率，从而整体提高 redis性能。

### 5.5.2 Redis事务

- Redis 通过 MULTI、EXEC、WATCH 等一组命令集合，来实现事务机制。 事务支持一次执行多个命令，一个事务中所有命令都会被序列化。在事务执行 过程，会按照顺序串行化执行队列中命令，其他客户端提交命令请求不会 插入到事务执行命令序列中

- 简言之，Redis 事务就顺序性、一次性、排他性执行一个队列中一系 列命令

- | 命令    | 描述                                                         |
  | ------- | ------------------------------------------------------------ |
  | MULTI   | 标记一个事务块开始                                           |
  | WATCH   | 监视key ，如果在事务执行之前，该 key 被其他命令所改动，那么事 务将被打断 |
  | UNWATCH | 取消WATCH 命令对所有key监视。                                |
  | EXEC    | 执行所有事务块内命令                                         |
  | DISCARD | 取消事务，放弃执行事务块内所有命令                           |

### 5.5.3 Redis Hash

![image-20231129104121540](images\redisHash.png)

- 为了保持高效，Redis 会对哈希表做 rehash 操作，也就增加哈希桶，减少冲突。为了 rehash 更高效，Redis 还默认使用了两个全局哈希表，一个用于当前使用，称为主哈希表，一个用于扩容，称为备用哈希表

### 5.5.4 Redis线程安全

- Redis服务端

  - Redis Server本身是一个线程安全的K-V数据库，也就是说在Redis Server上执行的指令，不需要任 何同步机制，不会存在线程安全问题
  - 增加的多线程只是用来处理网络IO事件，对于指令 的执行过程，仍然是由主线程来处理，所以不会存在多个线程通知执行操作指令的情况

- Redis客户端

  - 虽然Redis Server中的指令执行是原子的，但是如果有多个Redis客户端同时执行多个指令的时候， 就无法保证原子性。 假设两个redis client同时获取Redis Server上的key1，同时进行修改和写入，因为多线程环境下的 原子性无法被保障，以及多进程情况下的共享资源访问的竞争问题，使得数据的安全性无法得到保障

    ![image-20231129110955984](images\RedisClient.png)

  - 对于客户端层面的线程安全性问题，解决方法有很多，比如尽可能的使用Redis里面的原子指 令，或者对多个客户端的资源访问加锁，或者通过Lua脚本来实现多个指令的操作

# 六、消息队列

## 6.1 消息队列使用

### 6.1.1 消息队列简介

- 生产者：Producer 消息的产生者与调用端 主要负责消息所承载的业务信息的实例化 是一个队列的发起方
- 代理：Broker 主要的处理单元 负责消息的存储、投递、及各种队列附加功能的实现 是消息队列最核心的组成部分
- 消费者：Consumer 一个消息队列的终端，也是消息的调用端 具体是根据消息承载的信息，处理各种业务逻辑
- 消息队列的应用场景
  - 异步处理
    - 用户注册发送验证码、下单通知、发送优惠券等等
  - 应用解耦
    - 比如订单系统与WMS、EHR系统，有关联但不哪么紧密 ，每个系统之间只需要把约定的消息发送到MQ，另外的系统去消费即可。 解决了各个系统可以采用不同的架构、语言来实现，从而大大增加了系统的灵活性
  - 流量削峰
    - 应用在大流量入口且短时间内业务需求处理不完的服务中心
  - 消息通讯
    - 消息队列内置了高效✁通信机制，可用于消息通讯。如实现点对点消息队列、 聊天室等
  - 远程调用
- 市面上常见的消息队列中间件
  - ActiveMQ、RabbitMQ、Kafka、RocketMQ
  - 低吞吐量的一般用ActiveMQ、RabbitMQ较为合适
  - 大数据高吞吐量一般选用Kafka和RocketMQ

### 6.1.2 消息队列消息丢失问题

- 生产者保证不丢消息
  - 采用同步方式发送，send 消息方法返回成功状态，就表示消息正常到达了存储端 Broker
  - 如果 send 消息异常或者返回非成功状态，可以重试
  - 可以使用事务消息，RocketMQ 事务消息机制就为了保证零丢失来设计 
- 存储端不丢消息
  - 同步刷盘，生产者消息发过来时，只有持久化到磁盘，RocketMQ 存储端 Broker 才返回 一个成功ACK 响应。它保证消息不丢失，但影响了性能
  - 异步刷盘，只要消息写入 PageCache 缓存，就返回一个成功ACK 响应。 这样提高了 MQ 性能，但如果这时候机器断电了，就会丢失消息
  - Broker 一般集群部署
    - 同步复制，消息到 Broker 存储端，只有主节点和从节点都写入成功，才反馈成功ack 给生产 者，保证了消息不丢失，但降低了系统吞吐量
    - 异步复制，只要消息写入主节点成功，就返回成功ack，它速度 快，但会有数据问题
- 消费者不丢消息
  - 消费者执行完业务逻辑，再反馈会 Broker 说消费成功，这样才可以保证消费阶段不丢消息

### 6.1.3 消息队列幂等

- 幂等
  - 在计算机编程领域中，幂等是指一个方法被多次重复执行 的时候所期望的结果要和第一次执行所期望的结果保持一致。简单理解就是，一个逻辑即使被重复执 行多次，也不影响最终结果的一致性，这叫幂等
- 接口被重复执行
  - 用户的重复提交或者用户的恶意攻击
  - 分布式系统中，为了避免数据丢失，采用的超时重试机制
  - 这两种情况都有可能导致服务接口被重复调用。所以在程序设计中，对于数据变更类操作的接 口，需要保证接口的幂等性
- 解决幂等性问题
  - 是使用数据库的唯一约束来实现幂等，比如对于数据插入类的场景，比如创建订 单，因为订单号肯定是唯一的，所以如果是多次调用就会触发数据库的唯一约束异常，从而避免一个 请求创建多个订单的问题
  - 使用 Redis 提供的 setNX 指令，比如对于 MQ 消费的场景，为了避免 MQ 重 复消费导致数据多次被修改的问题，可以在接受到 MQ 的消息时，把这个消息通过 setNX 写入到 Redis 中，一旦这个消息被消费过，就不会再次消费
  - 使用状态机来实现幂等，所谓的状态机是指一条数据的完整运行状态的转换流程， 比如 ，因为它的状态只会向前变更，所以多次修改同一条数据的时候，一旦状态发生变更，那么对这条数据修改造成的影响只会发生一次
  - 基于 Token 机制或者增加去重表等方法来实现
  - 接口只允许调用一次，比如唯一约束、基于 Redis 的锁机制
  - 对数据的影响只会触发一次，比如乐观锁

### 6.1.4 消息数据一致性

- 普通MQ消费流程

  ![image-20231129113818947](images\commonMQ.png)

- 事务消息流程

  ![image-20231129114015479](images\transactionMQ.png)

  1. 生产者产生消息，发送一条半事务消息到 MQ 服务器
  2. MQ 收到消息后，将消息持久化到存储系统，这条消息状态待发送状态
  3. MQ 服务器返回 ACK 确认到生产者，此时 MQ 不会触发消息推送事件
  4. 生产者执行本地事务
  5. 如果本地事务执行成功，即 commit 执行结果到 MQ 服务器；如果执行失败，发 送 rollback
  6. 如果正常commit，MQ 服务器更新消息状态为可发送；如果rollback，即 删除消息
  7. 如果消息状态更新为可发送，则 MQ 服务器会 push 消息给消费者。消费者消费完 就回ACK
  8.  如果 MQ 服务器长时间没有收到生产者 commit 或者rollback，它会反查生产 者，然后根据查询到结果执行最终状态

### 6.1.5 阻塞队列

- 阻塞队列，是一种特殊的队列，它在普通队列的基础上提供了两个附加功能
- 当队列为空的时候，获取队列中元素的消费者线程会被阻塞，同时唤醒生产者线程
- 当队列满了的时候，向队列中添加元素的生产者线程被阻塞，同时唤醒消费者线程
- 阻塞队列中能够容纳的元素个数，通常情况下是有界，基于数组的阻塞队列中能够 容纳的元素个数。ArrayBlockingList这种就是有界队列
- 无界队列，就是没有设置固定大小的队列，不过它并不是像我们理解的那种元素没有任何限制，而 是它的元素存储量很大，像LinkedBlockingQueue，它的默认队列长度是Integer.Max_Value，无界队列存在比较大的潜在风险，如果在并发量较大的情况下，线程池中可以几乎无限制的添加任务， 容易导致内存溢出的问题

## 6.2 RabbitMQ

### 6.2.1 RabbitMQ工作原理

![image-20231129140618185](images\RabbitMQ.png)

- Product和Consumer分别是消息的生产者和消息的消费者
- Broker，中文翻译过来叫做代理或者中介，我可以把Broker理解为就是安 装RabbitMQ的服务器，就像是一栋用来存储和转发消息的房子
- Connection连接。无论是生产者发送消息，还是消费者接收消息，都必须要跟 Broker之间建立一个连接，那Connection呢就相当于是一个TCP的长连接
- Channel通道。
  - 在AMQP协议里面引入了Channel的概念，它相当于是一个虚拟的连接。这样我们就可以 在已经连接好的TCP长连接里面去创建和释放Channel，大大了减少了资源消耗，
  - 不同的Channel是相互隔离的，每个Channel都有自己的编号。对于每个客户端线程来说， Channel就没必要共享了，各自用自己的Channel。
  - Channel是RabbitMQ原生API里面的最重要的编程接口，也就是说 我们定义交换机、队列、绑定关系，发送消息，消费消息，调用的都是Channel接口上的方法
- Queue队列。它专门用来存储消息，Queue也是生产者和消费者的纽带，生产者发送的消息会存 储到队列中，而消费者也是从队列中来消费消息
- Exchange交换机。相当于消息的路由器。Exchange不会存储消息，它只做一件事情，根据 规则分发消息
- Binding绑定。
  - Exchange和存储消息的队列必须建立一个绑定关系，并且为每个队列指定一个特殊的标识。 Exchange和队列是多对多的绑定关系，也就说，一个交换机的消息一个路由给多个队列，一 个队列也可以接收来自多个交换机的消息
  - 绑定关系建立好之后，生产者发送消息到Exchange，也会携带一个特殊的标识。当这个标识 跟绑定的标识匹配的时候，消息就会发给一个或者多个符合规则的队列
- Vhost，全称叫Virtual Host虚拟机。为了解决不同业务系统之间的消息隔离， 节约硬件成本，我们可以利用RabbitMQ的Vhost来实现资源的隔离和权限的控制。它的功能和其他 编程语言中的NameSpace比较类似

### 6.2.2 RabbitMQ高可用

- 高可用呢，就是指分布式系统中，如果出现某些节点不可用的情况下，要保证客户端 依旧还能够连接到其他节点，而不至于影响业务的执行

- 普通集群

  - 普通集群模式下，不同的节点之间只会相互同步元数据，而不会同步消息内容

  - 其中元数据包含队列的名称、交换机名称及属性、交换机与队列的绑定关系等。

  - 节点只是起到一个路由的作用

  - 可以节约存储和同步数据的网络开销。但如果需要保证队列的高可用性， 这时候，就需要用到镜像集群的模式

  - [普通集群搭建过程](https://blog.csdn.net/qq_51409098/article/details/124963927)

    ```bash
    docker run -d --hostname rabbitmq01 --name rabbitmqCluster01  -p 15672:15672 -p 5672:5672 -e RABBITMQ_ERLANG_COOKIE='rabbitmqCookie' rabbitmq:3.8-management
     
    docker run -d --hostname rabbitmq02 --name rabbitmqCluster02  -p 15673:15672 -p 5673:5672 -e RABBITMQ_ERLANG_COOKIE='rabbitmqCookie'  --link rabbitmqCluster01:rabbitmq01 rabbitmq:3.8-management
     
    docker run -d --hostname rabbitmq03 --name rabbitmqCluster03  -p 15674:15672 -p 5674:5672 -e RABBITMQ_ERLANG_COOKIE='rabbitmqCookie'  --link rabbitmqCluster01:rabbitmq01 --link rabbitmqCluster02:rabbitmq02  rabbitmq:3.8-management
    
    rabbitmqctl stop_app
    rabbitmqctl reset
    # 参数“--ram”表示设置为内存节点，忽略次参数默认为磁盘节点。
    rabbitmqctl join_cluster --ram rabbit@rabbitmq01
    rabbitmqctl start_app
    ```

- 镜像集群

  - 在镜像队列模式下，消息内容会在所有的镜像节点间同步，可用性更 高。不过也有一定的副作用，系统性能会降低，节点过多的情况下同步数据的代价会比较大

  - [镜像集群搭建过程](https://blog.csdn.net/qgnczmnmn/article/details/129981993)

    ```bash
    # 在普通集群的基础上
    #设置策略匹配所有名称的队列都进行高可用配置
    rabbitmqctl set_policy -p / ha "^" '{"ha-mode":"all","ha-sync-mode":"automatic"}'
    # 使用set policy 命令设置镜像队列策略：
    rabbitmqctl set_policy -p [virtualhost] [Name] [Pattern] [Definition]  [Priority]
    # virtualhost: 虚拟机名称
    # Name：策略名称
    # Pattern：正则表达式
    # Definition：策略定义
    # Priority：优先级
    rabbitmqctl list_policies
    ```

- 负载均衡

  - 集群搭建成功后，要保证高可用，还需要一个负载均衡的组件（例如HAProxy，LVS， Nignx），由负载的组件来做路由。对于生产者或者消费者而言，只需要连接到负载组件的虚拟IP地址就可以了

  - [HAProxy搭建过程](https://blog.csdn.net/xuxingzhuang/article/details/131465263)

    ```bash
    docker pull haproxy:1.9.6
    docker run -d --name haproxy8100 -p 5679:5679 -p 8100:8100 -v /etc/rabbitmq_cluster/haproxy.cfg:/usr/local/etc/haproxy/haproxy.cfg  haproxy:1.9.6
    #logging options
    global
    	log 127.0.0.1 local0 info
    	maxconn 5120
    	chroot /usr/local/etc/haproxy
    	uid 99
    	gid 99
    	daemon
    	pidfile /var/run/haproxy.pid
    
    defaults
    	log global
    	#使用4层代理模式，”mode http”为7层代理模式
    	mode tcp
    	#if you set mode to tcp,then you nust change tcplog into httplog
    	option tcplog
    	option dontlognull
    	retries 3
    	maxconn 2000
    	timeout connect 5s
        #客户端空闲超时时间为 60秒 则HA 发起重连机制
        timeout client 60s
        #服务器端链接超时时间为 15秒 则HA 发起重连机制
        timeout server 15s
    	
    #front-end IP for consumers and producters
    listen rabbitmq_cluster
    	# 5679用于程序生产者及消费者
    	bind 0.0.0.0:5679 
    	#配置TCP模式
    	mode tcp
    	#简单的轮询
    	balance roundrobin
    	#rabbitmq集群节点配置 
    	#inter 每隔五秒对mq集群做健康检查， 2次正确证明服务器可用，2次失败证明服务器不可用，并且配置主备机制
    	# 192.168.1.19 是主机的地址
        server rabbitmq02 192.168.1.19:5673 check inter 5000 rise 2 fall 2
        server rabbitmq03 192.168.1.19:5674 check inter 5000 rise 2 fall 2
    	server rabbitmq01 192.168.1.19:5675 check inter 5000 rise 2 fall 2
    #配置haproxy web监控，查看统计信息
    listen stats
    	bind 0.0.0.0:8100
    	mode http
    	option httplog
    	stats enable
    	#设置haproxy监控地址为http://127.0.0.1:8100/rabbitmq-stats
    	stats uri /rabbitmq-stats
    	stats refresh 5s
    	stats auth admin:123456
    
    #访问地址
    http://192.168.51.121:8100/rabbitmq-stats
    ```

# 七、计算机网络

## 7.1 计算机网络基础

### 7.1.1 HTTP常用状态码

- 1XX 信息性状态码
  - 101 切换请求协议
- 2XX 成功状态码
  - 200 请求成功
- 3XX 重定向状态码
  - 301 永久性重定向，会缓存
  - 302 临时重定向，不会缓存
- 4XX 客户端错误状态码
  - 400 客户端请求的语法错误
  - 403 服务端进制访问，权限有关
  - 404 服务器无法根据客户端请求找到资源
- 5XX 服务端错误状态码
  - 500 服务端错误

### 7.1.2 HTTP请求方式

| 请求方式 | 用途                             |
| -------- | -------------------------------- |
| GET      | 对服务器资源获取的简单请求       |
| POST     | 用于发送包含用户提交数据的请求   |
| PUT      | 向服务器提交数据，以修改数据     |
| HEAD     | 请求页面的首部，获取资源的元信息 |
| DELETE   | 删除服务器上的某些资源           |
| CONNECT  | 用于ssl隧道的基于代理的请求      |
| OPTIONS  | 返回所有可用的方法，常用于跨域   |
| TRACE    | 追踪请求-响应的传输路径          |

- POST和GET区别

  ![image-20231129163223000](images\POSTGET.png)

### 7.1.3 HTTP常用端口

| 端口 | 服务                     |
| ---- | ------------------------ |
| 21   | FTP（文件传输协议）      |
| 22   | SSh                      |
| 23   | Telnet（远程登录）服务   |
| 25   | SMTP（简单邮件传输协议） |
| 53   | DNS域名服务器            |
| 80   | HTTP超文本传输协议       |
| 110  | POP3邮件协议3            |
| 443  | HTTPS                    |
| 1080 | Sockets                  |
| 1521 | Oracle数据库默认端口     |
| 3306 | MySQL服务默认端口        |

### 7.1.4 计算机网络体系结构

![image-20231129162318282](images\netStruct.png)

- OSI 七层模型
  - 应用层：网络服务与最终用户一个接口，常见协议有：HTTP FTP SMTP SNMP DNS
  - 表示层：数据表示、安全、压缩。，确保一个系统应用层所发送信息可 以被另一个系统应用层读取
  - 会话层：建立、管理、终止会话,对应主机进程，指本地主机与远程主机正在进 行会话
  - 传输层：定义传输数据协议端口号，以及流控和差错校验,协议有 TCP UDP
  - 网络层：进行逻辑地址寻址，实现不同网络之间路径选择,协议有 ICMP IGMP IP 等
  - 数据链路层：在物理层提供比特流服务基础上，建立相邻结点之间数据链路
  - 物理层：建立、维护、断开物理连接。

  ![image-20231204101929914](images\netinfo.png)

### 7.1.5 HTTP协议无状态

- 当浏览器第一次发送请求给服务器时，服务器响应了；如果同个浏览器发第二次请求给服务器时，它还会响应，但是呢，服务器不知道你就是刚才那个浏览器。简言之，服务器不会去记住你是谁，所以是无状态协议。
- Http 加了 Cookie可以实现有状态

### 7.1.6 HTTP请求过程

![image-20231129162829851](images\httpRequest.png)

### 7.1.7 HTTP 1.0，1.1，2.0

- HTTP 1.0
  - 默认使用短连接，每次请求都需要建立一个 TCP 连接。它可以设置 Connection: keep-alive这个字段，强制开启长连接。
- HTTP 1.1
  - 引入了持久连接，即 TCP 连接默认不关闭，可以被多个请求复用
  - 分块传输编码，即服务端每产生一块数据，就发送一块，用”流模式”取代”缓存模式”
  - 管道机制，即在同一个 TCP 连接里面，客户端可以同时发送多个请求
- HTTP 2.0
  - 二进制协议，1.1 版本头信息文本（ASCII 编码），数据体可以文本或者二进制；2.0 中，头信息和数据体都二进制
  - 完全多路复用，在一个连接里，客户端和浏览器都可以同时发送多个请求或回应， 而且不用按照顺序一一对应
  - 报头压缩，HTTP 协议不带有状态，每次请求都必须附上所有信息。Http 2.0 引 入了头信息压缩机制，使用 gzip 或 compress 压缩后再发送
  - 服务端推送，允许服务器未经请求，主动向客户端发送资源

### 7.1.8 HTTP与HTTPS区别

HTTPS= HTTP+SSL/TLS，可以理解 Https身披SSL(Secure SocketLayer，安全套层)的HTTP

- HTTPS流程

  - HTTPS = HTTP + SSL/TLS，也就用 SSL/TLS 对数据进行加密和解密，Http 进行传输

  - SSL，即Secure Sockets Layer（安全套层协议），网络通信提供安全及数据完整性一种安全协议。

  - TLS，即 Transport Layer Security(安全传输层协议)，它SSL3.0后续版本

    ![image-20231129163704210](images\HTTPS.png)

    1. 客户端发起 Https 请求，连接到服务器的443 端口。
    2. 服务器必须要有一套数字证书（证书内容有公钥、证书颁发机构、失效日期等）。
    3. 服务器将自己的数字证书发送给客户端（公钥在证书里面，私钥由服务器持有）。
    4. 客户端收到数字证书之后，会验证证书合法性。如果证书验证通过，就会生成一 个随机对称密钥，用证书公钥加密。
    5. 客户端将公钥加密后的对称密钥发送到服务器
    6. 服务器收到客户端发来密文密钥之后，用自己私钥对其进行非对称解密，解密之后就得到客户端密钥，然后用客户端密钥对返回数据进行对称加密， 传输数据密文
    7. 服务器将加密后密文返回到客户端
    8. 客户端收到后，用自己密钥对其进行对称解密，得到服务器返回数据


## 7.2 计算机名词解析

### 7.2.1 数字签名/数字证书

- 数字证书是指在互联网通讯中标志通讯各方身份信息，一个数字认证，人们可 以在网上用它来识别对方身份。为了避免身份被篡改冒充。
- 数字签名是公钥和个人等信息经过 Hash 摘要算法加密，形成信息摘要；将信息摘要拿到拥 有公信力得认证中心（CA），用它得私钥对信息摘要加密，形成数字签名。

![image-20231204100927672](images\CA.png)





### 7.2.2 对称加密/非对称加密

- 对称加密：指加密和解密使用同一密钥，优点运算速度较快，缺点如何安 全将密钥传输给另一方。常见对称加密算法有：DES、AES 等
- 非对称加密：指加密和解密使用不同密钥（即公钥和私钥）。公钥与私钥成对存在，如果用公钥对数据进行加密，只有对应私钥才能解密。常见非对称加密算法有 RSA

### 7.2.3 DNS解析过程

- DNS，domain name system，域名解析系统，Internet上作为域名和IP相互映射得一个分布式数据库，根据域名查出对应IP
- DNS 解析过程（www.baidu.com）
  1. 首先会查找浏览器缓存,看看否能找到www.baidu.com对应 IP 地址， 找到就直接返回；否则进行下一步。
  2. 将请求发往给本地 DNS 服务器，如果查找到也直接返回，否则继续进行下一 步
  3. 本地 DNS 服务器向根域名服务器发送请求，根域名服务器返回负责.com 顶级域名服务器 IP 地址列表
  4. 本地 DNS 服务器再向其中一个负责.com 顶级域名服务器发送一个请求，返 回负责.baidu 权威域名服务器 IP 地址列表
  5. 本地 DNS 服务器再向其中一个权威域名服务器发送一个请求，返回 www.baidu.com 所对应 IP 地址

### 7.2.4 计算机攻击

- CSRF，跨站请求伪造（英文全称 Cross-site request forgery），一种 挟制用户在当前已登录 Web 应用程序上执行非本意操作攻击方法

  - ![image-20231204101709895](images\CSRF.png)

  - 检查Referer 字段,添加校验 token

- Dos，Denial of Service 拒绝服务，一切能引起DOS行为得攻击都被称为DOS攻击，常见Dos有计算机网络宽带攻击、连通性攻击

- DDos，Distributed Denial of Service 分布式拒绝服务，指处于不同位置多个攻击者同时向一个或几个目标发动攻击，或者一个攻击者 控制了位于不同位置多台机器并利用这些机器对受害者同时实施攻击。常见 DDos 有 SYN Flood、Ping of Death、ACK Flood、UDP Flood 等

- DRDoS，Distributed Reflection Denial of Service，分布式反射拒绝服务，该方式靠发送大量带有被害者 IP 地址数据包给攻击主机，然后 攻击主机对 IP 地址源做出大量回应，从而形成拒绝服务攻击

- XSS，跨站脚本攻击（Cross-Site Scripting），因为会与层叠样式表(Cascading Style Sheets, CSS)缩写混淆，因此有人将跨站脚本攻击缩写为 XSS。恶意攻击者往 Web 页面里插入恶意 html 代码，当用户浏览该页之时，嵌入其中 Web 里面 html 代码会被执行，从而达到恶意攻击用户特殊目的。XSS 攻击一般分三种类型： 存储型 、反射型 、DOM 型 XSS

  - ![image-20231204102916730](images\XSS.png)

### 7.2.5 Socket和WebSocket

- Socket 其实就等于 IP 地址 + 端口 + 协议，完成了对 TCP/IP 高度封装，屏蔽网络细 节，以方便开发者更好地进行网络编程，网编编程标准接口
- WebSocket 一个持久化协议，它伴随 H5 而出协议，用来解决 http 不支持持久化连接问题，应用层通信协议

### 7.2.6 forward和redirect

- forward，直接转发方式，服务器转发方式，客户端和浏览器只发出一次请求， Servlet、HTML、JSP 或其它信息资源，由第二个信息资源响应该请求，在请 求对象 request 中，保存对象对于每个信息资源共享
  - ![image-20231204103345665](images\forward.png)
- redirect，间接转发方式，客户端转发方式，实际两次 HTTP 请求，服务器端在响应第一次 请求时候，让浏览器再向另外一个 URL 发出请求，从而达到转发目的
  - ![image-20231204103313760](images\redirect.png)

### 7.2.7 SQL注入

- SQL注入，通过在 web 应用接口传入一些特殊参数字符，来欺应用服务器，执行恶意SQL 命 令，以达到非法获取系统信息目的
- 防止sql注入
  - 使用#{}而不${}，因为#{}一个参数占位符，对于字符串类型，会自动加上""，其他类型不加。由 于 Mybatis 采用预编译，其后参数不会再进行 SQL 编译，所以一定程度上防 止SQL 注入，`${}一个简单字符串替换`，字符串什么，就会解析成什么，存在 SQL 注入 风险
  - 不要暴露一些不必要日志或者安全信息，比如避免直接响应一些 sql 异 常信息
  - 不相信任何外部输入参数，过滤参数中含有一些数据库关键词关键词
  - 适当权限控制

### 7.2.8 URI和URL区别

- URI，全称（ Uniform Resource Identifier)，中文翻译统一资源标志符，主 要作用唯一标识一个资源

- URL，全称（Uniform Resource Location)，中文翻译统一资源定位符，主 要作用提供资源路径。 打个经典比喻吧，URI 像身份证，可以唯一标识一 个人，而 URL 更像一个住址，可以通过 URL 找到这个人

- URL是一种具体的URI，它是URI的一个子集，它不仅唯一标识资源，而且还提供了定位该资源的信息。URI是一种语义上的抽象概念，可以是绝对的，也可以是相对的，而URL则必须提供足够的信息来定位，是绝对的。

- URL组成部分

  - 协议: 通常是https或者http。表示通过何种方式获取该资源。你可能还见过其他协议类型，比如ftp或者file，协议后面跟着://

  - 主机名: 可以是一个已经在DNS服务器注册过的域名 —— 或者是一个IP地址 —— 域名就表示背后的IP地址。一组主要由数字组成的用于标识接入网络的设备的字符串。主机名后面可以指定端口，端口是可选的，如果不指定则使用默认端口，端口和主机名之间通过冒号隔开。

  - 资源路径: 用于表示资源在主机上的文件系统路径。

  - 可以在这之后通过问号连接可选的查询参数，如果有多个查询参数，通过&符连接

  - 最后一项，如果需要的话可以添加#作为需要跳转的页面上的矛点名称。

  - ```
    protocol  ://  hostname / path ? query # fragment
    ```

### 7.2.9 Session和Cookie区别

- Cookie
  - 是客户端浏览器用来保存服务端数据的一种机制，当通过浏览器进行网页访问的时候，服务器可以把某一些状态数据以key-value的方式写入到Cookie 里面存储到客户端浏览器，然后客户端下一次再访问服务器的时候，就可以携带这些状态数据发送到服务器端，服务端可以根据 Cookie里面携带的内容来识别使用者
- Session
  - 表示一个会话，它是属于服务器端的容器对象，默认情况下，针对每一个浏览器的请求。 Servlet容器都会分配一个Session，Session本质上是一个ConcurrentHashMap，可以存储当前会话产生的一些状态数据。Session是用来弥补Http无状态的不足，简单来说，服务器端可以利用session来存储客户端在 同一个会话里面的多次请求记录基于服务端的session存储机制，再结合客户端的Cookie机制，就可以实现有状态的Http协议
- 有状态的Http协议
  - ![image-20231205133752345](images\statusHttp.png)
- Cookie是客户端的存储机制，Session是服务端的存储机制

## 7.3 传输层TCP

### 7.3.1 TCP三次握手

- 握手过程
  1. 第一次握手(SYN=1, seq=x)，发送完毕后，客户端就进入 SYN_SEND 状态
  2. 第二次握手(SYN=1, ACK=1, seq=y, ACKnum=x+1)， 发送完毕后，服务器 端就进入SYN_RCV 状态
  3. 第三次握手(ACK=1，ACKnum=y+1)，发送完毕后，客户端进入 ESTABLISHED 状态，当服务器端接收到这个包时，也进入 ESTABLISHED 状态
- 原因
  - TCP是可靠性通信协议，所以通信双方都必须要维护一个序列号，去标记已经发送出去的数 据包，哪些是已经被对方签收的。而三次握手就是通信双方相互告知序列号的起始值，为了确保这个 序列号被收到，所以双方都需要有一个确认的操作
  - TCP协议需要在一个不可靠的网络环境下实现可靠的数据传输，意味着通信双方必须要通过 某种手段来实现一个可靠的数据传输通道，而三次通信是建立这样一个通道的最小值。当然还可以四 次、五次，只是没必要浪费这个资源
  - 防止历史的重复连接初始化造成的混乱问题，比如说在网络比较差的情况下，客户端连续多次发送建立连接的请求，假设只有两次握手，那么服务端只能选择接受或者拒绝这个连接请求，但是 服务端不知道这次请求是不是之前因为网络堵塞而过期的请求，也就是说服务端不知道当前客户端的 连接是有效还是无效

### 7.3.2 TCP四次挥手

- 挥手过程
  1. 第一次挥手(FIN=1，seq=u)，发送完毕后，客户端进入 FIN_WAIT_1 状态
  2. 第二次挥手(ACK=1，ack=u+1,seq =v)，发送完毕后，服务器端进入 CLOSE_WAIT 状态，客户端接收到这个确认包之后，进入 FIN_WAIT_2 状态。
  3. 第三次挥手(FIN=1，ACK1,seq=w,ack=u+1)，发送完毕后，服务器端进入 LAST_ACK 状态，等待来自客户端最后一个 ACK。
  4. 第四次挥手(ACK=1，seq=u+1,ack=w+1)，客户端接收到来自服务器端关闭请求，发送一个确认包，并进入 TIME_WAIT 状态，等待了某个固定时间（两 个最大段生命周期，2MSL，2 Maximum Segment Lifetime）之后，没有收到服务器端ACK ，认为服务器端已经正常关闭连接，于是自己也关闭连接， 进入 CLOSED 状态。服务器端接收到这个确认包之后，关闭连接，进入 CLOSED 状态
- 2MSL，two Maximum Segment Lifetime，即两个最大段生命周期
  - 为了保证客户端发送的最后一个 ACK 报文段能够到达服务端。 这个 ACK 报文段有可能丢失，因而使处在LAST-ACK 状态服务端就收不到，对已发送FIN + ACK 报文段的确认。服务端会超时重传这个 FIN+ACK 报文段，而客户端就能在 2MSL 时间内（超时 + 1MSL 传输）收到这个重传FIN+ACK 报文段。接着客户端重传一次确认，重新启动 2MSL 计时器。最后，客户端和 服务器都正常进入到 CLOSED 状态
  - 防止已失效连接请求报文段出现在本连接中。客户端在发送完最后一个 ACK 报文段后，再经过时间 2MSL，就可以使本连接持续时间内所产生的所 有报文段都从网络中丢失。这样就可以使下一个连接中不会出现这种旧连接请求报文段

### 7.3.3 TCP确保可靠性

- TCP 连接基于三次握手，而断开则基于四次挥手。确保连接和断开可靠性
- TCP 可靠性，还体现在有状态，TCP 会记录哪些数据发送了，哪些数据被 接收了，哪些没有被接受，并且保证数据包按序到达，保证数据传输不出差错
- TCP 可靠性，还体现在可控制。它有数据包校验、ACK 应答、**超时重传(发送方)**、失序数据重传（接收方）、丢弃重复数据、流量控制（滑动窗口） 和拥塞控制等机制

### 7.3.4 TCP重传机制

- 超时重传
  - 在发送数据报文时，设定一个定时器，每间隔一段时间间隔，如果没收到对方 ACK 应答报文，就会重发该报文
  - RTT（Round-Trip Time，往返时间）一个数据包从发出去到回来ack时间，即数据包一次往返时间。超 时重传时间，就 Retransmission Timeout ，简称 RTO
- 快速重传
  - 快速重传机制，它不以时间驱动，而是以数据驱动。它基于接收端反馈信息 来引发重传
  - 快速重传流程
    1. 发送端发送了 1，2，3，4，5，6 份数据:
    2. 第一份 Seq=1 先送到了，于是就 Ack 回2；
    3. 第二份 Seq=2 也送到了，假设也正常，于是ACK 回 3；
    4. 第三份 Seq=3 由于网络等其他原因，没送到；
    5. 第四份 Seq=4 也送到了，但因为 Seq3 没收到。所以 ACK 回 3；
    6. 后面Seq=5，6 也送到了，但ACK 还回复 3，因为Seq=3没收到。
    7. 发送端连着收到三个重复冗余 ACK=3 确认（实际上 4 个，但前面一个正 常 ACK，后面三个才重复冗余），便知道哪个报文段在传输过程中丢失了， 于是在定时器过期之前，重传该报文段
    8. 最后，接收端收到了 Seq3，此时因为 Seq=4，5，6 都收到了，于是ack回7
  - 但快速重传还可能会有个问题：ACK 只向发送端告知最大有序报文段，到底 哪个报文丢失了呢？并不确定！那到底该重传多少个包呢？重传 Seq3 呢？还是重传 Seq3、Seq4、Seq5、Seq6 呢？因为发送端并 不清楚这三个连续的ACK3 是谁传回来。
- 带选择确认的重传（SACK）
  - SACK 机制就是，在快速重传的基础上，接收端返回最近收到报文段序列号范围，这样发送端就知道接收端哪些数据包没收到；
- D-SACK
  - 即Duplicate SACK（重复 SACK），在 SACK 的基础上做了一些 扩展，，主要用来告诉发送方，有哪些数据包自己重复接受了

### 7.3.5 TCP滑动窗口

- TCP 头部有个字段叫 win，也即那个 16 位窗口大小，它告诉对方本端TCP 接收缓冲区还能容纳多少字节数据，这样对方就可以控制发送数据速度，从而达到流量控制目的
- 发送端的滑动窗口
  - 已发送且已收到 ACK 确认
  - 已发送但未收到 ACK 确认
  - 未发送但可以发送
  - 未发送也不可以发送
  - ![image-20231204144138000](images\TCPWin.png)
  - 虚线矩形框，就是发送窗口
  - SND.WND: 表示发送窗口大小,上图虚线框格子数 14 个，即发送窗口大小  14。
  - SND.NXT：下一个发送位置，它指向未发送但可以发送第一个字节序列号】
  - SND.UNA: 一个绝对指针，它指向已发送但未确认第一个字节序列号。
- 接收方滑动窗口
  - 已成功接收并确认
  - 未收到数据但可以接收
  - 未收到数据并不可以接收的数据
  - ![image-20231204144427723](images\TCPReceiveWin.png)
  - 虚线矩形框，就是接收窗口
  - REV.WND: 表示接收窗口的大小,上图虚线框的格子就是 9 个。
  - REV.NXT:下一个接收✁位置，它指向未收到但可以接收的第一个字节序列号

### 7.3.6 TCP流量控制

1. 假如当前发送方给接收方发送了 200 个字节，那么，发送方SND.NXT会右移 200 个字节，也就说当前可用窗口减少了 200 个字节
2. 接受方收到后，放到缓冲队列里面，REV.WND =400-200=200 字节，所以 win=200 字节返回给发送方。接收方会在 ACK 报文首部带上缩小后的滑动窗 口200 字节
3. 发送方又发送 200 字节过来，200 字节到达，继续放到缓冲队列。不过这时候， 由于大量负载原因，接受方处理不了这么多字节，只能处理 100 字节，剩余 100 字节继续放到缓冲队列。这时候，REV.WND = 400-200-100=100 字 节，即 win=100 返回发送方
4. 发送方继续干活，发送 100 字节过来，这时候，接受窗口 win 变为0
5. 发送方停止发送，开启一个定时任务，每隔一段时间，就去询问接受方，直到 win 大于 0，才继续开始发

### 7.3.7 TCP拥塞控制

- 拥塞控制作用于网络，防止过多数据包注入到网络中，避免出现网络负 载过大情况。它目标主要最大化利用网络上瓶颈链路带宽
- 流量控制作用于接收者✁，根据接收端的实际接收能 力控制发送速度，防止分组丢失
- 发送方维护一个拥塞窗口 cwnd（congestion window） 变量，用来 估算在一段时间内这条链路（水管）可以承载和运输的数据（水）的数量，只要网络中没有出现拥塞，拥塞窗口值就可以再增大一些，以便把更多的数 据包发送出去，但只要网络出现拥塞，拥塞窗口的值就应该减小一些，以减少 注入到网络中的数据包数
- 慢启动算法
  - TCP 连接完成，初始化 cwnd = 1，表明可以传一个 MSS 单位
  - 每当收到一个 ACK，cwnd 就加一
  - 每当过了一个 RTT，cwnd 就增加一倍; 呈指数上升
  - 慢启动阀值ssthresh（slow start threshold）状态变量。当 cwnd 到达该阀值后，就好像水管被关小了水龙头一样，减少拥塞状态。即当 cwnd >ssthresh 时，进 入了拥塞避免算法。
- 拥塞避免算法
  - 一般来说，慢启动阀值 ssthresh 是 65535 字节，cwnd到达慢启动阀值后
    - 每收到一个 ACK 时，cwnd = cwnd + 1/cwnd 
    - 当每过一个 RTT 时，cwnd = cwnd + 1
- 拥塞发生
  - 当网络拥塞发生丢包时，会有两种情况：RTO 超时重传、快速重传
  - RTO 超时重传触发拥塞发生算法
    - 慢启动阀值sshthresh = cwnd /2
    - cwnd 重置为1
    - 进入新的慢启动过程
  - 快速重传
    - 拥塞窗口大小 cwnd = cwnd / 2
    - 慢启动阀值 ssthresh = cwnd
    - 进入快速恢复算法
- 快速恢复
  - 快速重传和快速恢复算法一般同时使用
  - cwnd = sshthresh + 3
  - 重传重复那几个 ACK（即丢失的那几个数据包）
  - 如果再收到重复的 ACK，那么 cwnd = cwnd + 1
  - 如果收到新数据ACK 后, cwnd = sshthresh。因为收到新数据 ACK，表明 恢复过程已经结束，可以再次进入了拥塞避免算法

### 7.3.8 半连接队列/SYN Flood

- TCP进入三次握手前，服务端从CLOSED状态变为LISTEN状态，同时在内部创建了两个队列，半连接队列（SYN队列）和全连接队列（ACCEPT队列）
- TCP 三次握手时，客户端发送 SYN 到服务端，服务端收到之后，便回复 ACK 和 SYN，状态由 LISTEN 变为SYN_RCVD，此时这个连接就被推入了 SYN 队 列，即半连接队列
- 当客户端回复 ACK, 服务端接收后，三次握手就完成了。这时连接会等待被具体应用取走，在被取走之前，它被推入 ACCEPT 队列，即全连接队列
- SYN Flood 是一种典型的DDos攻击，它在短时间内，伪造不存在的 IP地址, 向服务器大量发起 SYN 报文。当服务器回复 SYN+ACK 报文后，不会收到ACK 回应报文，导致服务器上建立大量半连接，半连接队列满了，这就无法处理正常TCP 请求
  - syn cookie：在收到 SYN 包后，服务器根据一定的方法，以数据包源地址、 端口等信息为参数计算出一个 cookie 值作为自己 SYNACK 包序列号，回复 SYN+ACK 后，服务器并不立即分配资源进行处理，等收到发送方 ACK 包后，重新根据数据包源地址、端口计算该包中确认序列号否正确，如 果正确则立连接，否则丢弃该包
  - SYN Proxy 防火墙：服务器防火墙会对收到每一个 SYN 报文进行代理和回 应，并保持半连接。等发送方将 ACK 包返回后，再重新构造SYN 包发到服务 器，建立真正的 TCP连接

### 7.3.9 TCP粘包拆包

![image-20231204153659491](images\TCP.png)

- 要发送的数据小于 TCP 发送缓冲区大小，TCP 将多次写入缓冲区的数据一次 发送出去，将会发生粘包
- 接收数据端应用层没有及时读取接收缓冲区中的数据，将发生粘包
- 要发送的数据大于 TCP 发送缓冲区剩余空间大小，将会发生拆包；
- 待发送数据大于 MSS（最大报文长度），TCP 在传输前将进行拆包。即 TCP 报文长度-TCP 头部长度>MSS
- 解决方案
  - 发送端将每个数据包封装为固定长度
  - 在数据尾部增加特殊字符进行分割
  - 将数据分为两部分，一部分头部，一部分内容体；其中头部结构大小固定，且 有一个字段声明内容体大小

### 7.3.10 Nagle 算法与延迟确认

- Nagle 算法基本定义：任意时刻，最多只能有一个未被确认小段。 所谓“小段”，指小于 MSS 尺寸数据块，所谓“未被确认”，指一个数据 块发送出去后，没有收到对方发送 ACK 确认该数据已收到
- 实现规则
  - 如果包长度达到 MSS，则允许发送
  - 如果该包含有 FIN，则允许发送
  - 设置了TCP_NODELAY 选项，则允许发送
  - 未设置TCP_CORK 选项时，若所有发出去小数据包（包长度小于 MSS）均被确认，则允许发送
  - 上述条件都未满足，但发生了超时（一般为 200ms），则立即发送
- 延迟确认
  - 接收方收到数据包后，如果暂时没有数据要发给对端，它可以等一段时再确认 （Linux 上默认40ms）。如果这段时间刚好有数据要传给对端，ACK 就随着数据传输，而不需要单独发送一次 ACK。如果超过时间还没有数据要发送， 也发送ACK，避免对端以为丢包
  - 但有些场景不能延迟确认，比如发现了乱序包、接收到了大于一个 frame 报文，且需要调整窗口大小等
  - Nagle 算法和延迟确认不能一起使用，Nagle 算法意味着延迟发， 延迟确认意味着延迟接收，酱紫就会造成更大延迟，会产生性能问题

### 7.3.11 TCP和UDP对应应用层协议

- TCP
  - HTTP：HyperText Transfer Protocol（超文本传输协议），默认端口 80
  - FTP: File Transfer Protocol (文件传输协议), 默认端口(20 用于传输数据， 21用于传输控制信息)
  - SMTP: Simple Mail Transfer Protocol (简单邮件传输协议) ,默认端
  - TELNET: Teletype over the Network (网络电传), 默认端口 23
  - SSH： Secure Shell（安全外壳协议），默认端口 22
- UDP
  - DNS : Domain Name Service (域名服务),默认端口 53
  - TFTP: Trivial File Transfer Protocol (简单文件传输协议)，默认端口 69
  - SNMP：Simple Network Management Protocol（简单网络管理协议），通 过 UDP 端口 161 接收，只有 Trap 信息采用UDP 端口 162。

### 7.3.12 TCP保活计时器

- 服务器每收到一次客户数据，就重新设置保活计时器，时间设置通常两个小时。若两个小时都没有收到客户端数据，服务端就发送一个探测报文段，以后则每隔 75 秒钟发送一次。若连续发送 10 个探测报文段后仍然无客户端响应，服务端就认为客户端出了故障，接着就关闭这个连接

## 7.4 网络层

### 7.4.1 IP地址分类

- IP 地址=网络号+主机号
  - 网络号：它标志主机所连接网络地址表示属于互联网哪一个网络
  - 主机号：它标志主机地址表示其属于该网络中哪一台主机
- IP 地址分为 A，B，C，D，E 五大类
  - A 类地址(1~126)：以 0 开头，网络号占前 8 位，主机号
  - B 类地址(128~191)：以 10 开头，网络号占前 16 位，主机号占后面 16 位。
  - C 类地址(192~223)：以 110 开头，网络号占前 24 位，主机号占后面8位
  - D 类地址(224~239)：以 1110 开头，保留位多播地址
  - E 类地址(240~255)：以 11110 开头，保留位为将来使用 
  - ![image-20231204155657050](images\IP.png)
  - 全为0的IP地址被保留为广播地址，而全为1的IP地址被保留为网络地址。因此，只有中间的数值范围（即1到254）可用于分配给特定主机

### 7.4.2 ARP协议

- ARP协议，Address Resolution Protocol，地址解析协议，用于实现IP地址到MAC地址的映射
- ARP过程
  1. 首先，每台主机都会在自己 ARP 缓冲区中建立一个 ARP 列表，以表 示 IP 地址和 MAC 地址对应关系
  2. 当源主机需要将一个数据包要发送到目的主机时，会首先检查自己 ARP 列表，是否存在该 IP 地址对应MAC 地址；如果有，就直接将数据包发送到这个 MAC 地址；如果没有，就向本地网段发起一个 ARP 请 求广播包，查询此目的主机对应 MAC 地址。此 ARP 请求数据包 里，包括源主机 IP 地址、硬件地址、以及目的主机 IP 地址
  3. 网络中所有主机收到这个 ARP 请求后，会检查数据包中目的 IP 是 否和自己 IP 地址一致。如果不相同，就会忽略此数据包；如果相同， 该主机首先将发送端MAC 地址和 IP 地址添加到自己 ARP 列表中， 如果 ARP 表中已经存在该 IP 信息，则将其覆盖，然后给源主机发送 一个 ARP 响应数据包，告诉对方自己是它需要查找的MAC 地址
  4. 源主机收到这个 ARP 响应数据包后，将得到目的主机 IP 地址和 MAC 地址添加到自己 ARP 列表中，并利用此信息开始数据传输。 如果源主机一直没有收到 ARP 响应数据包，表示 ARP 查询失败
- IP 地址和 MAC 地址， 但计算机IP 地址可由用户自行更改，管理起来就相对困难，而 MAC 地址不 可更改，所以一般会把 IP 地址和 MAC 地址组合起来使用
- 对于目的地址在 其他子网数据包，路由只需要将数据包送到那个子网即可。 IP 地址和地域相关，对于同一个子网上 设备，IP 地址前缀都一样，这样路由器通过 IP 地址前缀就知道设备哪个子网上了
- IP 地址可以比作为地址，MAC 地址为收件人，在一次通信过程中，两者缺 一不可

# 八、Spring

## 8.1 Spring 基础

### 8.1.1 Spring 相同id

- 同一个XML配置文件
  - 不能存在id相同的两个bean，否则spring容器启动的 时候会报错
  - Spring对XML文件进行解析转化为BeanDefinition的阶段
- 不同的Spring配置文件
  - 可以存在id相同的两个bean
  - IOC容器在加载Bean的时候，默认会多个相同id的bean进行覆盖
- 使用@Bean注 解实现Bean的声明
  - 在同一个配置类里面声明多个相同名字的bean，在Spring IOC 容器中只会注册第一个声明的Bean的实例

### 8.1.2 Spring解决循环依赖

- Spring bean初始化精简流程

  - 加载bean定义
  - 创建装配流程
    - 创建bean对象
      1. 首先Spring容器启动之后，会根据使用不同类型的ApplicationContext，通过不同的方式去加载Bean配置，如xml方式、注解方式，将这些Bean配置加载到容器中，作为Bean定义包装成BeanDefinition对象保存起来，为下一步创建Bean做准备。
      2. 根据加载的Bean定义信息，通过反射来创建Bean实例，如果是普通Bean，则直接创建Bean，如果是FactoryBean，说明真正要创建的对象为getObject()的返回值，调用getObject()将返回值作为Bean
         - FactoryBean是一个工厂Bean，可以生成某一个类型Bean实例，它最大的一个作用是：可以让我们自定义Bean的创建过程。FactoryBean本质就是用来给我们实例化、或者动态的注入一些比较复杂的Bean，比如像一些接口的代理对象
         - BeanFactory是Spring容器中的一个基本类也是很重要的一个类，在BeanFactory中可以创建和管理Spring容器中的Bean，它对于Bean的创建有一个统一的流程
    - 装配bean属性
    - 将完整的bean对象保存在Spring中
  - 初始化流程
    - 执行bean的前置处理器
    - 执行afterPropertiesSet方法
    - 执行bean的后置处理器

- Spring通过三级缓存解决循环依赖

  - 一级缓存：即单例对象缓存池，beanName->Bean，其中存储的就是实例化，属性赋值成功之后的单例对象

    ```java
    private final Map<String, Object> singletonObjectts = new ConcurrentHashMap<>(256);
    ```

  - 二级缓存：早期的单例对象，beanName->Bean，其中存储的是实例化之后，属性未赋值的单例对象，执行了工厂方法生产出来的Bean，bean被放进去之后， 当bean在创建过程中，就可以通过getBean方法获取到早期单例对象

    ```java
    private final Map<String, Object> earlySingletonobjects = new HashMap<>(16);
    ```

  - 三级缓存：单例工厂的缓存，beanName->ObjectFactory，添加进去的时候实例还未具备属性，用于保存beanName和创建bean的工厂之间的关系map

    ```java
    private final Map<String, ObjectFactory<?>>> siingletonFactories = new HashMap<>(16);
    ```

  - ![image-20231208102429210](images\ResolveCircular.png)

- Spring中哪些情况下，不能解决循环依赖问题

  - 多例Bean通过setter注入的情况，不能解决循环依赖问题
    - A --> B --> A，且 A,B 都是 scope=prototype
    - A 实例创建后，populateBean 时，会触发 B 的加载， B 实例创建后，populateBean 时，会触发 A 的加载。由于A的scope=prototype，从缓存中获取不到 A，要创建一个全新的 A。这样，就会进入一个死循环
  - 构造器注入的Bean的情况，不能解决循环依赖问题
    -  A --> B --> A，且 都是通过构造函数依赖的
    - A 实例在创建时(createBeanInstance)，由于是构造注入，这时会触发 B 的加载，B 实例在创建时(createBeanInstance)，又会触发 A 的加载，此时，A 还没有添加到三级缓存中，所以就会创建一个全新的 A。这样，就会进入一个死循环
  - @Async 增强的 Bean 的循环依赖，不能解决循环依赖问题
    - A --> B --> A, 且 A 是被 @Async 标记的类

### 8.1.3 BeanFactory和FactoryBean

- BeanFactory
  - 保存了所有需要对外提供的Bean的实例
  - 相当于是IOC（控制反转）容器的顶级接口，是IOC容器最基础的实现
  - 完成对Bean的依赖注入（DI）
- FactoryBean
  - FactoryBean是一个工厂Bean，它是一个接口，主要的功能是动态生成某一个类型的 Bean的实例，也就是说，我们可以自定义一个Bean并且加载到IOC容器里面。
  -  它里面有一个重要的方法叫getObject()，这个方法里面就是用来实现动态构建Bean的过 程。 
  - Spring Cloud里面的OpenFeign组件，客户端的代理类，就是使用了FactoryBean来实现 的

### 8.1.4  Spring Bean的生命周期（作用域）

- singleton，也就是单例，意味着在整个Spring容器中只会存在一个Bean实例。
- prototype，翻译成原型，意味着每次从IOC容器去获取指定Bean的时候，都会返回一个 新的实例对象
- 在基于Spring框架下的Web应用
  - request，针对每一次http请求，都会创建一个新的Bean
  - session，以sesssion会话为纬度，同一个session共享同一个Bean实例，不同的session 产生不同的Bean实例
  - globalSession，针对全局session纬度，共享同一个Bean实例

### 8.1.5 Spring事务的传播行为

- REQUIRED：默认的Spring事物传播级别，如果当前存在事务，则加入这个事务，如果不存在事务，就新建一个事务
- REQUIRE_NEW：不管是否存在事务，都会新开一个事务，新老事务相互独立。外部事务抛出异常回滚不会影响内部事务的正常提交
- NESTED：如果当前存在事务，则嵌套在当前事务中执行（嵌套事务是一种特殊的事务，它可以独立于外部事务进行回滚，但提交时仍依赖于外部事务。这种传播行为适用于需要在单个事务内执行多个独立操作的场景。）。如果当前没有事务，则新建一 个事务
- SUPPORTS：表示支持当前事务，如果当前不存在事务，以非事务的方式执行
- NOT_SUPPORTED：表示以非事务的方式来运行，如果当前存在事务，则把当前事务挂起
- MANDATORY：强制事务执行，若当前不存在事务，则抛出异常
- NEVER：以非事务的方式执行，如果当前存在事务，则抛出异常
- 示例：不同传播行为的使用场景
  - 假设有一个银行转账的业务场景，涉及到两个方法：transfer 和 audit。transfer 方法负责实际转账操作，audit 方法负责记录转账操作的审计日志
  - 使用 REQUIRED 传播行为：转账和审计操作在同一个事务中执行，要么都成功，要么都失败。
  - 使用 REQUIRES_NEW 传播行为：转账和审计操作在不同的事务中执行，互不影响
  - 使用 NESTED 传播行为：转账和审计操作在嵌套事务中执行，审计操作可以独立回滚，但提交依赖于转账操作

### 8.1.6 Bean的创建的生命周期

- Class-->推断构造方法-->普通对象-->依赖注入-->初始化前-->初始化-->初始化后(AOP)-->代理对象-->放入Map(单例池)-->Bean对象

## 8.2 Spring 核心-IOC

### 8.2.1 Spring框架概述

![image-20231213142018727](images\SpringTree.png)



- 整个Spring框架构建在Core核心模块之上，它是整个框架的基础。在该模块中，Spring为我们提供了一个IoC（Inversion of Control/控制反转）容器（IoC Container）实现，用于帮助我们以依赖注入的方式管理对象之间的依赖关系，Core核心模块中还包括框架 内部使用的各种工具类（如果愿意，我们也可以在框架之外使用），比如Spring的基础IO工具类
- AOP（Aspect Oriented Programming/面向切面编程）框架，让我们可以以AOP的形式增强各POJO的能力，进而补足OOP（Object Oriented Programming/面向对象编程）/OOSD（Object Oriented Design/面向对象设计）之缺憾
- Spring框架在Core核心模块和AOP模块的基础上，为我们提供了完备的数据访问和事务管理的抽象和集成服务，Spring框架为各种当前业界流行的ORM产品，比如Hibernate、iBATIS、Toplink、 JPA等提供了形式统一的集成支持
- Spring框架为我们提供了针对Java EE服务的集成服务
  - java EE（Java Enterprise Edition/java平台企业版），它包括用于Web开发的Servlet、JSP和JSF技术，以及用于企业级应用的EJB、JMS、JTA等
    - JNDI (Java Naming and Directory Interface)，JNDI是Java EE的一部分，它提供了一个接口，用于查找和访问各种命名和目录服务
    - JMS (Java Message Service)，JMS是Java技术的一部分，它提供了一个消息传递的接口和API，用于实现异步通信
    - JavaMail，JavaMail是Java EE和Java SE的一部分，它提供了一个API，用于发送和接收电子邮件
- Spring框架提供了一套自己的Web MVC框架

### 8.2.2 IOC基本概念

- IOC，Inversion of Control，控制反转，别名依赖注入DI，Dependency  Injection，让别人为你服务
- 通常情况下，被注入对象会直接依赖于被依赖对象。但是，在IoC的场景中，二者之间通过IoC Service  Provider来打交道，所有的被注入对象和依赖对象现在由IoC Service Provider统一管理
- ![image-20231213150049955](images\IOCBeforeAfter.png)
- 依赖注入的方式
  - 构造方法注入
    - 这种注入方式的优点就是，对象在构造完成之后，即已进入就绪状态，可以马上使用。缺点就是，当依赖对象比较多的时候，构造方法的参数列表会比较长。而通过反 射构造对象的时候，对相同类型的参数的处理会比较困难，维护和使用上也比较麻烦。而且 在Java中，构造方法无法被继承，无法设置默认值。对于非必须的依赖处理，可能需要引入多 个构造方法，而参数数量的变动可能造成维护上的不便

  - setter方法注入
    - 因为方法可以命名，所以setter方法注入在描述性上要比构造方法注入好一些。 另外，setter方法可以被继承，允许设置默认值，而且有良好的IDE支持。缺点当然就是对象无 法在构造完成后马上进入就绪状态

  - 接口注入
    - 从注入方式的使用上来说，接口注入是现在不甚提倡的一种方式，基本处于“退 役状态”。因为它强制被注入对象实现不必要的接口，带有侵入性。而构造方法注入和setter 方法注入则不需要如此。

### 8.2.3 IOC Service Provider

- 职责
  - 业务对象的构建管理，IoC Service Provider需要将对象的构建逻辑从客户端对象那里剥离出来，以免这部分逻辑污染业务对象的实现
  - 业务对象间的依赖绑定，IoC Service  Provider通过结合之前构建和管理的所有业务对象，以及各个业务对象间可以识别的依赖关系，将这些对象所依赖的对象注入绑定，从而保证每个业务对象在使用的时候，可以处于就绪状 态。
- 注册对象管理信息
  - 直接编码方式	
    - 以通过程序编码的方式将被注入对象和依赖对象注册到容器中，并明确它们相互之间的依赖注入关系
  - 配置文件方式
    - 像普通文本文件、properties文件、XML文件等，都可以成为管理依赖注入关系的载体
  - 元数据方式
    - 直接在类中使用元数据信息来标注各个对象之间的依赖关系，然后由框架根据这些注解所提供的信息将这些对象组装后，交给客户端对象使用

### 8.2.4 Spring IOC 容器 - BeanFactory

在Spring的IoC容器之上，Spring还提供了 相应的AOP框架支持、企业级服务集成等服务。Spring的IoC容器和IoC Service Provider所提供的服务 之间存在一定的交集

![image-20231222140706255](images\SpringIOC.png)

- 容器类型
  - BeanFactory
    - 基础类型IoC容器，提供完整的IoC服务支持。如果没有特殊指定，默认采用延迟初始化策略（lazy-load）。只有当客户端对象需要访问容器中的某个受管对象的时候，才对 该受管对象进行初始化以及依赖注入操作。所以，相对来说，容器启动初期速度较快，所需要的资源有限。对于资源有限，并且功能要求不是很严格的场景，BeanFactory是比较合适的 IoC容器选择
  - ApplicationContext
    - ApplicationContext在BeanFactory的基础上构建，是相对比较高级的容器实现，除了拥有BeanFactory的所有支持，ApplicationContext还提供了其他高级特性，比如事件发布、国际化信息支持等，在该类型容器启动之后，默认全部初始化并绑定完成。所以，相对于BeanFactory来说，ApplicationContext要求更多的系统资源，同时，因为在启动时就完成所有初始化，容器启动时间较之BeanFactory也会长一些。在那些系统资源充足，并且要求更多功能的场景中， ApplicationContext类型的容器是比较合适的选择。

- 对象注册与依赖绑定方式

  - 直接编码
  - 外部配置文件方式
    - Properties
    - XML

  - 注解方式

- &lt;beans&gt;属性详解

  - &lt;beans&gt;是XML配置文件中的最顶层的元素，它下面可以包含0或者1个&lt;description&gt;和多个&lt;bean&gt;以及&lt;import&gt;或者&lt;alias&gt;
  - beans是所有bean的父级，拥有对应属性对bean进行统一的默认行为设置
  - default-lazy-init。 其值可以指定为true或者false，默认值为false。用来标志是否对所有的bean进行延迟初始化
  - default-autowire。可以取值为no、byName、byType、constructor以及autodetect。默 认值为no，如果使用自动绑定的话，用来标志全体bean使用哪一种默认绑定方式
  - default-dependency-check。可以取值none、objects、simple以及all，默认值为none， 即不做依赖检查。
  - default-init-method。如果所管辖的按照某种规则，都有同样名称的初始化方法的 话，可以在这里统一指定这个初始化方法名，而不用在每一个上都重复单独指定。
  - default-destroy-method。与default-init-method相对应，如果所管辖的bean有按照某种 规则使用了相同名称的对象销毁方法，可以通过这个属性统一指定。

- description属性详解

  - 在配置的文件中指定一些描述性的信息

- import 属性详解

  - 在 想加载主要配置文件，并将主要配置文件所依赖的配置文件同时加载时，可以在这个主要的配置文件 中通过import 元素对其所依赖的配置文件进行引用

    ```xml
    <import resource="B.xml"/>
    ```

-  alias属性详解

  - 为某些bean起一些“外号”（别名），通常情况下是为了减少输入

    ```xml
    <alias name="dataSourceForMasterDatabase" alias="masterDataSource"/>
    ```

- bean属性详解

  - id属性

    - 通过id属性来指定当前注册对 象的beanName是什么

      ```xml
      <bean id="djNewsListener" name="/news/djNewsListener,dowJonesNewsListener" class="..impl.DowJonesNewsListener"> 
      </bean> 
      ```

    - name属性的灵活之处在于，name可以使用id不能使用的一些字符，比如/。而且 还可以通过逗号、空格或者冒号分割指定多个name。name的作用跟使用为id指定多个别名基 本相同

  - class属性

    - 每个注册到容器的对象都需要通过元素的class属性指定其类型


### 8.2.5 Spring IOC启动

- 容器启动伊始，首先会通过某种途径加载Configuration MetaData。除了代码方式比较直接，在大 部分情况下，容器需要依赖某些工具类（BeanDefinitionReader）对加载的Configuration MetaData进行解析和分析，并将分析后的信息编组为相应的BeanDefinition，最后把这些保存了bean定义必 要信息的BeanDefinition，注册到相应的BeanDefinitionRegistry，这样容器启动工作就完成了

- 经过第一阶段，现在所有的bean定义信息都通过BeanDefinition的方式注册到了BeanDefinitionRegistry中。当某个请求方通过容器的getBean方法明确地请求某个对象，或者因依赖关系容器 需要隐式地调用getBean方法时，就会触发第二阶段的活动。 该阶段，容器会首先检查所请求的对象之前是否已经初始化。如果没有，则会根据注册的 BeanDefinition所提供的信息实例化被请求对象，并为其注入依赖。如果该对象实现了某些回调接口，也会根据回调接口的要求来装配它。当该对象装配完毕之后，容器会立即将其返回请求方使用。 如果说第一阶段只是根据图纸装配生产线的话，那么第二阶段就是使用装配好的生产线来生产具体的 产品了

- Spring提供了一种叫做BeanFactoryPostProcessor的容器扩展机制。该机制允许我们在容器实 例化相应对象之前，对注册到容器的BeanDefinition所保存的信息做相应的修改

  - PropertyPlaceholderConfigurer

    - PropertyPlaceholderConfigurer允许我们在XML配置文件中使用占位符（PlaceHolder）， 并将这些占位符所代表的资源单独配置到简单的properties文件中来加载。
    - 当BeanFactory在第一阶段加载完成所有配置信息时，BeanFactory中保存的对象的属性信息还只是以占位符的形式存在，如\${jdbc.url}、\${jdbc.driver}。当 PropertyPlaceholderConfigurer作为BeanFactoryPostProcessor被应用时，它会使用properties 配置文件中的配置信息来替换相应BeanDefinition中占位符所表示的属性值。这样，当进入容器实 现的第二阶段实例化bean时，bean定义中的属性值就是最终替换完成的了

  - PropertyOverrideConfigurer

    - 可以通过PropertyOverrideConfigurer对容器中配置的任何你想处理的bean定义的property信息进行覆盖替换。

      ```properties
      beanName.propertyName=value
      
      # pool-adjustment.properties
      dataSource.minEvictableIdleTimeMillis=1000 
      dataSource.maxActive=50 
      ```

      ```xml
      <bean class="org.springframework.beans.factory.config.PropertyOverrideConfigurer"> 
       <property name="location" value="pool-adjustment.properties"/> 
      </bean> 
      ```

  - CustomEditorConfigurer

    - 其他两个BeanFactoryPostProcessor都是通过对BeanDefinition中的数据进行变更以达到某 种目的。与它们有所不同，CustomEditorConfigurer是另一种类型的BeanFactoryPostProcessor实 现，它只是辅助性地将后期会用到的信息注册到容器，对BeanDefinition没有做任何变动

- ![image-20231229145510805](images\createBean.png)

- Bean的实例化与BeanWrapper

  - 容器在内部实现的时候，采用“策略模式（Strategy Pattern）”来决定采用何种方式初始化bean实例。 通常，可以通过反射或者CGLIB动态字节码生成来初始化相应的bean实例或者动态生成其子类。
  - 容器只要根据相应bean定义的BeanDefintion取得实例化信息，结合CglibSubclassingInstantiationStrategy以及不同的bean定义类型，就可以返回实例化完成的对象实例。但是，返回方 式上有些“点缀”。不是直接返回构造完成的对象实例，而是以BeanWrapper对构造完成的对象实例 进行包裹，返回相应的BeanWrapper实例。
  - BeanWrapper接口通常在Spring框架内部使用，它有一个实现类org.springframework.beans.BeanWrapperImpl。其作用是对某个bean进行“包裹”，然后对这个“包裹”的bean进行操作，比如设置或者获取bean的相应属性值。而在第一步结束后返回BeanWrapper实例而不是原先的对象实例， 就是为了第二步“设置对象属性”
  - Spring会根据对象实例构造一个BeanWrapperImpl实例,然后将之前CustomEditorConfigurer注册的PropertyEditor复制一份给BeanWrapperImpl实例这样，当BeanWrapper转换类型、设置对象属性值时，就不会无从下手了

- 各色的Aware接口

  - org.springframework.beans.factory.BeanNameAware。如果Spring容器检测到当前对象实 例实现了该接口，会将该对象实例的bean定义对应的beanName设置到当前对象实例
  - org.springframework.beans.factory.BeanClassLoaderAware。如果容器检测到当前对 象实例实现了该接口，会将对应加载当前bean的Classloader注入当前对象实例。默认会使用 加载org.springframework.util.ClassUtils类的Classloader
  - org.springframework.beans.factory.BeanFactoryAware。在介绍方法注入的时候，我们 提到过使用该接口以便每次获取prototype类型bean的不同实例。如果对象声明实现了 BeanFactoryAware接口，BeanFactory容器会将自身设置到当前对象实例。这样，当前对象 实例就拥有了一个BeanFactory容器的引用，并且可以对这个容器内允许访问的对象按照需要 进行访问。
  - org.springframework.context.ResourceLoaderAware 。 ApplicationContext 实现了 Spring的ResourceLoader接口。当容器检测到当前对象实例实现了 ResourceLoaderAware接口之后，会将当前ApplicationContext自身设置到对象实例，这样 当前对象实例就拥有了其所在ApplicationContext容器的一个引用
  - org.springframework.context.ApplicationEventPublisherAware。ApplicationContext 作为一个容器，同时还实现了ApplicationEventPublisher接口，这样，它就可以作为ApplicationEventPublisher来使用。所以，当前ApplicationContext容器如果检测到当前实例 化的对象实例声明了ApplicationEventPublisherAware接口，则会将自身注入当前对象
  - org.springframework.context.MessageSourceAware。ApplicationContext通过MessageSource接口提供国际化的信息支持，即（Internationalization）。它自身就实现了MessageSource接口，所以当检测到当前对象实例实现了MessageSourceAware接口，则会将自身注入 当前对象实例。

- BeanPostProcessor

  - BeanPostProcessor的概念容易与BeanFactoryPostProcessor的概念混淆。但只要记住BeanPostProcessor是存在于对象实例化阶段，而BeanFactoryPostProcessor则是存在于容器启动阶段， 这两个概念就比较容易区分了。

  - BeanFactoryPostProcessor通常会处理容器内所有符合条件的BeanDefinition类似，BeanPostProcessor会处理容器内所有符合条件的实例化后的对象实例。该接口声明了两个方法，分别在 两个不同的时机执行

    ```java
    public interface BeanPostProcessor
    { 
     Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException; 
     Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException; 
    }
    ```

- InitializingBean和init-method

  - ```java
    public interface InitializingBean { 
     void afterPropertiesSet() throws Exception; 
    }
    ```

  - 在对象实例化过程调用过“BeanPostProcessor的前置处理” 之后，会接着检测当前对象是否实现了InitializingBean接口，如果是，则会调用其afterPropertiesSet()方法进一步调整对象实例的状态。比如，在有些情况下，某个业务对象实例化完成后，还 不能处于可以使用状态。这个时候就可以让该业务对象实现该接口，并在方法afterPropertiesSet() 中完成对该业务对象的后续处理

  - Spring还提供了另一种方式来指定自定义的对象初始化操作，那就 是在XML配置的时候，使用的init-method属性。 通过init-method，系统中业务对象的自定义初始化操作可以以任何方式命名，而不再受制于 InitializingBean的afterPropertiesSet()。

- DisposableBean与destroy-method

  - 与InitializingBean和init-method用于对象的自定义初始化相对应，DisposableBean和 destroy-method为对象提供了执行自定义销毁逻辑的机会
  - 对于BeanFactory容器来说。我们需要在独立应用程序的主程序退出之前，或者其他被认为是合 适的情况下（依照应用场景而定），调用ConfigurableBeanFactory提供的 destroySingletons()方法销毁容器中管理的所有singleton类型的对象实例
  - 对于ApplicationContext容器来说。道理是一样的。但AbstractApplicationContext为我们 提供了registerShutdownHook()方法，该方法底层使用标准的Runtime类的addShutdownHook()方 式来调用相应bean对象的销毁逻辑，从而保证在Java虚拟机退出之前，这些singtleton类型的bean对象 实例的自定义销毁逻辑会被执行

### 8.2.6 Spring IOC 容器 - ApplicationContext

- 常用容器实现
  - org.springframework.context.support.FileSystemXmlApplicationContext。在默认 情况下，从文件系统加载bean定义以及相关资源的ApplicationContext实现
  - org.springframework.context.support.ClassPathXmlApplicationContext。在默认情 况下，从Classpath加载bean定义以及相关资源的ApplicationContext实现
  - org.springframework.web.context.support.XmlWebApplicationContext。Spring提供 的用于Web应用程序的ApplicationContext实现

- Spring中的Resource
  - ByteArrayResource。将字节（byte）数组提供的数据作为一种资源进行封装，如果通过 InputStream形式访问该类型的资源，该实现会根据字节数组的数据，构造相应的ByteArrayInputStream并返回
  - ClassPathResource。该实现从Java应用程序的ClassPath中加载具体资源并进行封装，可以使 用指定的类加载器（ClassLoader）或者给定的类进行资源加载
  - FileSystemResource。对java.io.File类型的封装，所以，我们可以以文件或者URL的形 式对该类型资源进行访问，只要能跟File打的交道，基本上跟FileSystemResource也可以。
  - UrlResource。通过java.net.URL进行的具体资源查找定位的实现类，内部委派URL进行具 体的资源操作
  - InputStreamResource。将给定的InputStream视为一种资源的Resource实现类，较为少用。 可能的情况下，以ByteArrayResource以及其他形式资源实现代之

- 可用的ResourceLoader 
  - ResourceLoader有一个默认的实现类，即org.springframework.core.io.DefaultResourceLoader，该类默认的资源查找处理逻辑如下
    - 首先检查资源路径是否以classpath:前缀打头，如果是，则尝试构造ClassPathResource类 型资源并返回
    - 否则
      - 尝试通过URL，根据资源路径来定位资源，如果没有抛出MalformedURLException， 有则会构造UrlResource类型的资源并返回
      - 如果还是无法根据资源路径定位指定的资源，则委派 getResourceByPath(String) 方法来定位
      - DefaultResourceLoader 的 getResourceByPath(String)方法默认实现逻辑是，构造ClassPathResource类型的资源并返回
  - FileSystemResourceLoader
    - 继承自DefaultResourceLoader，但覆写了getResourceByPath(String)方法，使之从文件系统加载资源并以 FileSystemResource类型返回
  - ResourcePatternResolver ——批量查找的ResourceLoader
    - ResourceLoader每次只能根据资源路径 返回确定的单个Resource实例，而ResourcePatternResolver则可以根据指定的资源路径匹配模式， 每次返回多个Resource实例

- ApplicationContext与ResourceLoader
  - ApplicationContext继承了ResourcePatternResolver，当 然就间接实现了ResourceLoader接口。所以，任何的ApplicationContext实现都可以看作是一个 ResourceLoader甚至ResourcePatternResolver。而这就是ApplicationContext支持Spring内统一 资源加载策略的真相
  -  扮演ResourceLoader的角色
  - ResourceLoader类型的注入

- 国际化支持

  - Locale

    - 不同的 Locale代表不同的国家和地区，每个国家和地区在Locale这里都有相应的简写代码表示， 包括语言代码以及国家代码，这些代码是ISO标准代码

  - ResourceBundle

    - ResourceBundle用来保存特定于某个Locale的信息（可以是String类型信息，也可以是任何类型 的对象）。通常，ResourceBundle管理一组信息序列，所有的信息序列有统一的一个basename，然后 特定的Locale的信息，可以根据basename后追加的语言或者地区代码来区分,文件名中的messages部分称作ResourceBundle将加载的资源的basename，其他语言或地 区的资源在basename的基础上追加Locale特定代码

      ```properties
      messages.properties 
      messages_zh.properties 
      messages_zh_CN.properties 
      messages_en.properties 
      messages_en_US.properties
      # messages_zh_CN.properties文件中
      menu.file=文件({0}) 
      menu.edit=编辑
      ... 
      # messages_en_US.properties文件中
      menu.file=File({0}) 
      menu.edit=Edit
      ```

  - MessageSource与ApplicationContext

    - ApplicationContext需要其配置文件中有一个名称为messageSource的MessageSource实现
    - org.springframework.context.support.StaticMessageSource。MessageSource接口的简单实现，可以通过编程的方式添加信息条目，多用于测试，不应该用于正式的生产环境
    - org.springframework.context.support.ResourceBundleMessageSource。基于标准的 java.util.ResourceBundle而实现的MessageSource，对其父类AbstractMessageSource 的行为进行了扩展，提供对多个ResourceBundle的缓存以提高查询速度。同时，对于参数化 的信息和非参数化信息的处理进行了优化，并对用于参数化信息格式化的MessageFormat实例也进行了缓存。它是最常用的、用于正式生产环境下的MessageSource实现
    -  org.springframework.context.support.ReloadableResourceBundleMessageSource 。 同样基于标准的java.util.ResourceBundle而构建的MessageSource实现类，但通过其 cacheSeconds属性可以指定时间段，以定期刷新并检查底层的properties资源文件是否有变更。 对于properties资源文件的加载方式也与ResourceBundleMessageSource有所不同，可以通过 ResourceLoader来加载信息资源文件。使用ReloadableResourceBundleMessageSource时， 应该避免将信息资源文件放到classpath中，因为这无助于ReloadableResourceBundleMessageSource定期加载文件变更

- 事件发布

  - Java SE提供了实现自定义事件发布（Custom Event publication）功能的基础类，即java.util.EventObject类和java.util.EventListener接口。所有的自定义事件类型可以通过扩展EventObject 来实现，而事件的监听器则扩展自EventListener
  - Spring 的容器内事件发布类结构
    - ApplicationEvent ,Spring容器内自定义事件类型，继承自java.util.EventObject
      - ContextClosedEvent：ApplicationContext容器在即将关闭的时候发布的事件类型
      - ContextRefreshedEvent：ApplicationContext容器在初始化或者刷新的时候发布的事件类 型。
      - RequestHandledEvent：Web请求处理后发布的事件，其有一子类ServletRequestHandledEvent提供特定于Java EE的Servlet相关事件

    - ApplicationListener,ApplicationContext容器内使用的自定义事件监听器接口定义，继承自java.util.EventListener。
    - ApplicationContext,ApplicationContext容器现在担当的就是 事件发布者的角色

- 多模块配置

  - 以String[]形式传入这些配置文件所在的路径
  - 使用通配符
  - MessengerService类在Classpath中的位置定位配 置文件，而不用指定每个配置文件的完整路径名


### 8.2.7 Spring依赖注入

- @Autowired
  - 构造方法定义（Constructor）。标注于类的构造方法之上的@Autowired，相当于抢夺了原有自 动绑定功能中“constructor”方式的权利，它将根据构造方法参数类型，来决定将什么样的依赖对象 注入给当前对象
  - 域（Filed）或者说属性（Property）。不管它们声明的访问限制符是private、protected还是 public，只要标注了@Autowired，它们所需要的依赖注入需求就都能够被满足
  - 方法定义（Method）。@Autowired不仅可以标注于传统的setter方法之上，而且还可以标注于任 意名称的方法定义之上，只要该方法定义了需要被注入的参数
  - org.springframework.beans.  factory.annotation.AutowiredAnnotationBeanPostProcessor用于激活Autowired
- @Qualifier
  - @Autowired是按照类型进行匹配，如果当前@Autowired标注的依赖在容器中只能找到一个实例 与之对应的话，那还好。可是，要是能够同时找到两个或者多个同一类型的对象实例，就无法使用
  - @Qualifier实际上是byName自动绑定的注解版，既然IoC容器无法自己从多个同一类型的实例中 选取我们真正想要的那个，那么我们不妨就使用@Qualifier直接点名要哪个好了

- 使用JSR250 标注依赖注入关系
  - 用JSR250的@Resource和@PostConstruct以及@PreDestroy
  - @Resource
    - @Resource与@Autowired不同，它遵循的是byName自动绑定形式的行为准则，也就是说，IoC容 器将根据@Resource所指定的名称，到容器中查找beanName与之对应的实例，然后将查找到的对象实 例注入给@Resource所标注的对象
    - 与@Autowired能够存在的地方大致相同

  - @PostConstruct和@PreDestroy不是服务于依赖注入的，它们主要用于标注对象生 命周期管理相关方法
    - 与Spring的InitializingBean和DisposableBean接口，以及配置项中的 init-method和destroy-method起到类似的作用

  - 如果想某个方法在对象实例化之后被调用，以做某些准备工作，或者想在对象销毁之前调用某个 方法清理某些资源，使用@PostConstruct和@PreDestroy来标注这些方法
  - JSR250的这些注解也同样需要一个BeanPostProcessor帮助它们实现自身的价值。这个BeanPostProcessor就是org.springframework.context.  annotation.CommonAnnotationBeanPostProcessor，只有将CommonAnnotationBeanPostProcessor添 加到容器，JSR250的相关注解才能发挥作用

- 在基于XSD的配置文件中使用一个context:annotation-config配置
  - 把 AutowiredAnnotationBeanPostProcessor 和 CommonAnnotationBeanPostProcessor注册到容器，同时还会把PersistenceAnnotationBeanPostProcessor和RequiredAnnotationBeanPostProcessor一并进行注册
  - PersistenceAnnotationBeanPostProcessor
    - 这个处理器主要用于处理与 JPA（Java Persistence API）相关的注解，如 @Entity, @Repository, @EntityListener 等

  - RequiredAnnotationBeanPostProcessor
    - 这个处理器用于处理 @Required 注解。当一个 bean 的属性或构造函数参数上标记了 @Required，并且该属性或参数在注入时没有提供值，那么 Spring 会抛出一个异常

- classpath-scanning
  - classpath-scanning功能可以从某一顶层 包（base package）开始扫描。当扫描到某个类标注了相应的注解之后，就会提取该类的相关信息，构 建对应的BeanDefinition，然后把构建完的BeanDefinition注册到容器
  - classpath-scanning功能的触发是由在基于XSD的配置文件中使用一个context:component-scan决定的
  - context:component-scan默认扫描的注解类型是@Component。不过，在@Component语义基 础上细化后的@Repository、@Service和@Controller也同样可以
  - 在扫描相关类定义并将它们添加到容器的时候，会使用一种默认的 命名规则，来生成那些添加到容器的bean定义的名称（beanName）。比如DowJonesNewsPersister通 过默认命名规则将获得dowJonesNewsPersister作为bean定义名称
  - context:component-scan同时将AutowiredAnnotationBeanPostProcessor和 CommonAnnotationBeanPostProcessor一并注册到了容器中


## 8.3 Spring核心-AOP

### 8.3.1 AOP 基本概念

- Joinpoint
  - 我们可以在HelloBean初始化的执行点进行横切逻辑的织入,可以以在hellomethod方法被调用的执行点上进行横切逻辑的织入,可以在hellomethod方法内部执行行的开始时点上进行织入,也可以在message字段被设置或者取得的执行点上进行横切逻辑的织入。基本上,只要允许,程序执行过程中的任何时点都可以作为横切逻辑的织入点,而所有这些执行时点都是Joinpoint。
  - 方法调用(Method Call)
    - 当某个方法被调用的时候所处的程序执行点
  - 方法调用执行(Method Call execution)
    - 称之为方法执行或许更简洁,该Joinpoint类型代表的是某个方法内部执行开始时点,应该与方法调用类型的Joinpoint进行区分。
    - 方法调用(method call)是在调用对象上的执行点,而方法执行(methodexecution)则是在被调用到的方法逻辑执行的时点。对于同一对象,方法调用要先于方法执行。
  - 构造方法调用(Constructor Call)
    - 程序执行过程中对象调用其构造方法进行初始化的时点
  - 构造方法执行(ConstructorCall Execution)
    - 构造方法执行和村沟造方法调用之间的关系类似于方法执行和方法调用之间的关系,指的是某个对象构造方法内部执行的开始时点。
  - 字段设置(FieldSet)
    - 对象的某个属性通过setter方法被设置或者直接被设置的时点。该Joinpoint的本质是对象的属性被设置,而通过setter方法设置还是直接设置触发的时点是相同的。
  - 字段获取(FieldGet)
    - 相对于字段设置型的Joinpoint,字段获取型的Joinpoint,对应的是某个对象相应属性被访问的时点。可以通过getter方法访问,当然也可以直接访问
  - 异常处理执行(Exception HandlerExecution)
    - 该类型的Joinpoin对应程序执行过程中,在某些类型异常抛出后,对应的异常处理逻辑执行的时点。
  - 类初始化(Classinitialization)
    - 类初始化型的Joinpoint,指的是类中某些静态类型或者静态块的初始化时点。
- Pointcut
  - Pointcut概念代表的是Joinpoint的表述方式。将横切逻辑织入当前系统的过程中,需要参照Pointcut规定的Joinpoint信息,才可以知道应该往系统的哪些Joinpoint上织入横切逻辑
  - 直接指定Joinpoint所在方法名称
    - 这种形式的Pointcut表述方式比较简单,而且功能单一,通常只限于支持方法级别Joinpoint的AOP框架,或者只是方法调用类型的Joinpoint,或者只是方法执行类型的Joinpoint。而且,即使是只针对方法级别的Joinpoint,因为系统中需要织入横切逻辑的方法可能很多,一个一个地指定则过于不便,所以这种方式通常只限于Joinpoint较少且较为简单的情况。
  - 正则表达式
    - 这是比较普遍的Pointcut表达方式,可以充分利用正则表达式的强大功能,来归纳表述需要符合某种条件的多组Joinpoint。儿乎现在大部分的Java平台的AOP产品都支持这种形式的Pointcut表达形式,包括JbossAOP、SpringAOP以及AspectWerkz等。
  - 使用特定的Pointcut表述语言
    - 这是一种最为强大的表达Poirtcut的方式,灵活性也很好,但具体实现起来可能过于复杂,需要设计该表述语言的语法,实现相应的解释器等许多工作。AspectJ使用这种方式来指定Pointcut,它提供了一种类似于正则表达式的针对Pointcut的表述语言,在表达Pointcut方面支持比较完善。
  - Pointcut与Pointcut之间还可以进行逻辑运算,具体使用的逻辑运算语法,会因AOP产品实现的不同而不同。比如在Spring的配置文件中使用and、or等单词作为逻辑运算符,而在AspectJ中,则可以使用&&以及II。
- Advice
  - Advice是单一横切关注点逻辑的载体,它代表将会织入到Joinpoint的横切逻辑。如果将Aspect比作OOP中的Class,那么Advice就相当于Class中的Method。按照Advice在Joinpoint位置执行时机的差异或者完成功能的不同,Advice可以分成多种具体形式。
  - Before Advice
    - Before Advice是在Joint指定位置之前执行的Advice类型。通常,它不会中断程序执行流程,但如果必要,可以通过在BeforeAdvice中抛出异常的方式来中断当前程序流程。如果当前Before Advice将被织入到方法执行类型的Joinpoint,那么这个Before Advice就会先于方法去执行而执行
      通常,可以使用Before Advice做一些系统的初始化工作,比如设置系统初始值,获取必要系统资源等。当然,并非就限于这些情况。如果要用BeforeAdvice来封装安全检查的逻辑,也不是不可以的,但通常情况下,我们会使用另一种形式的Advice。
  - After Advice
    - After Advice就是在相应连接点之后执行的Advice类型
    - After returning Advice
      - 只有当前Joint处执行流程正常完成后,After returning Advice才会执行。比如方法执行正常返回而没有抛出异常。
    - After throwing Advice
      - 又称Throws Advice,只有在当前Joint执行过程中抛出异常的情况下,才会执行。比如某个方法执行类型的Joinpoint抛出某异常而没有有正常返回
    - After Advice
      - 或许叫After(Finally)Advice更为确切,该类型Advice不管Joinpoint处执行流程是正常终了还是抛出异常都会执行,就好像Java中的finally块一样
  - Around Advice
    - Around Advice可以在Joinpoint之前和之后都能执行相应的逻辑,那么,它自然可以完成BeforeAdvice和AfterAdvice的功能。不过,通常情况下,还是应该根据场景选用更为具体的Advice类型。
  - Introduction
    - 在AspectJ中称Inter-Type Declaration,在JBossAOP中称Mix-in,都指的是这同一种类型的Advice。与之前的几种Advice类型不同,Introduction不是根据横切逻辑在Joinpoin处的执行时机来区分的,而是根据它可以完成的功能而区别于其他Advice类型。
    - Introduction可以为原有的对象添加新的特性或者行为,这就就好像你是一个普通公民,当让你穿军装,带军帽,添加了军人类型的Introduction之后,你就拥有军人的特性或者行为。
- Aspect
  - Aspect是对系统中的横切关注点逻辑进行模块化封装的AOP概念实体。通常情况下,Aspect可以包含多个Pointcut以及相关Advice定义。

### 8.3.2 Spring AOP 一世

- SpringAOP属于第二代AOP,采用动态代理机制和字节码生成技术实现。与最初的AspectJ采用编译器将横切逻辑织入目标对象不同,动态代理机制和字节码生成都是在运行期间为目标对象生成一个代理对象,而将横切逻辑织入到这个代理对象中,系统最终使用的是织入了横切逻辑的代理对象,而不是真正的目标对象。
- JDK动态代理
- CGLIB动态字节码
- Joinpoint
  - 在SpringAOP中,仅支持方法级别的Joinpoint。更确切地说,只支持方法执行(Method Execution)类型的Joinpoint。
- Pointcut

  - SpringAOP的Pointcut类型可以划分为StaticMethodMatcher Pointcut和DynamicMethodatcherPointcut两类

  - NameMatchMethodPointcut
    - 这是最简单的Pointcut实现,属于StaticMethodMatcherPointcut的子类,可以根据自身指定的一组方法名称与Joinpoint处的方法名称进行匹配
    - 如果基于"*"通配符的NameMatchMethodPointcut依然无法满足对多个特定Joinpoint的匹配需要,那么使用正则表达式好了。
  - JdkRegexpMethodPointcut和Perl5RegexpMethodPointcut
    - StaticMethodMatcherPointcut的子类中有一个专门提供基于正则表达式的实现分支，JdkRegexpMethodPointcut和Per15RegexpMethodPointcut两种具体实现
  - AnnotationMatchingPointcut
    - AnnotationMatchingPointcut根据目标对象中是否存在指定类型的注解来匹配Joinpoint,要使用该类型的Pointcut,首先需要声明相应的注解。
    - @ClassLevelAnnotation用于类层次,而@MethodLevelAnnotation只能用于方法层次
  - ComposablePointcut
    - Pointcut通常道不提供逻辑运算功能,而ComposablePointcut就是SpringAOP提供的可以进行Pointcut逻辑运算的Pointcut实现。它可以进行Pointcut之间的"并"以及"交"运算
  - ControlFlowPointcut
    - 当织入器按照Pointcut的规定,将Advice织入到目标对象之后,从任何其他地方调用method1,是不会触发Advice所包含的横切逻辑的执行的。只有在ControlFlowPointcut规定的类内部调用目标对象的method1,才会触发Advice中横切逻辑的执行。
- Advice
  - Advice实现了将被织入到Pointcut规定的Joinpoint处的横切逻辑。在Spring中,Advice按照其自身实例(instance)能否在目标对象类的所有实例中共享这一标准,可以以划分为两大类,即per-class类型的Advice和per-instance类型的Advice。
  - per-class 类型的Advice
    - per-class类型的Advice是指,该类型的Advice的实例可以在目标对多象类的所有实例之间共享。这种类型的Advice通常只是提供方法拦截的功能,不会为目标对象类保存任何状态或者添加新的特性。
    - Before Advice
      - Before Advice所实现的横切逻辑将在相应的Joinpoint之前执行,在BBefore Advice执行完成之后,程序执行流程将从Joinpoint处继续执行,所以BeforeAdvice通常不会打断程序的执行流程。

    - ThrowsAdvice
    - AfterReturningAdvice
      - 通过Spring中的AfterReturningAdvice,我们可以访问当前Joinpoint的方法返回值、方法、方法、方法参数以及所在的目标对象。

    - Around Advice
- Aspect
  - Advisor代表Spring中的Aspect,但是,与正常的Aspect不同,Advisor通常只持有一个Pointcut和一个Advice。而理论上,Aspect定义中可以有多个Pointcut和多个Advice,所以,我们可以认为Advisor是一种特殊的Aspect。
  - 为了能够更清楚Advisor的实现结构体系,我们可以将Adviso简单划分为两个分支,一个分支以org.springframework.aop.PointcutAdvisor为首,另一个分子支则以org.springframework.aop.IntroductionAdvisor为头儿

- ProxyFactory
  - 

































































