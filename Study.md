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

# 二、算法

## 2.1 滑动窗口+HashMap

- 用来处理从左到右满足条件的数据

## 2.2 二分查找法

- 用来将O(n)级别调整为O($log^n$)

# 三、Java

## 3.1 java基础

1. Java中重写equals方法为什么要重写hashcode方法？

   ```
   等价的两个对象散列值⼀定相同，但是散列值相同的两个对象不⼀定等价，这是因为计算哈希值具有随机性，两个值不同的对象可能计算出相同的哈希值。
   HashMap存储值时，先调用hashCode，唯一则存储，不唯一则再调用equals，结果相同则不再存储，结果不同则散列到其他位置。因为hashCode效率更高（仅为一个int值），比较起来更快。
   所以重写equals可能导致对象等价，hashCode不同
   ```

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

java.util.concurrent（J.U.C）⼤⼤提⾼了并发性能，AQS 被认为是 J.U.C 的核⼼

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



