# 一、数组和集合（不重复的数组）

## 1. 已知一个有100个元素的数组，请回答以下操作需要的步骤数。

a. 读取

数组在内存中是连续的一块，所以根据索引读取，步骤数只需要1；

b. 查找该数组中没有的一个值

无法知道数组中具体值，只能遍历，没有的值就是遍历到最后，所以步骤数需要N

c. 在数组开头插入

在数组前面开辟一块空间存储数据，并将其他值右移一位，所以步骤数为1 + N

d. 在数组末尾插入

在数组后面开辟一块空间存储数据，所以步骤数为1

e. 从数组开头删除

在数组前面删除一个数据，并将其他值左移一位，所以步骤数为1 + N - 1 = N

f. 从数组末尾删除

在数组后面删除一个数据，所以步骤数为1

## 2. 已知一个基于数组的集合有100个元素，请回答以下操作需要的步骤数。

a. 读取

集合数据不重复，但是还是数组，所以根据索引读取，步骤数只需要1；

b. 查找该数组中没有的一个值

集合数据不重复，但是还是数组，无法知道数组中具体值，只能遍历，没有的值就是遍历到最后，所以步骤数需要N

c. 在集合开头插入一个新值
需要判断该值是否存在，遍历全部，在数组前面开辟一块空间存储数据，并将其他值右移一位，所以步骤数为N + 1 + N = 2N + 1

d. 在集合末尾插入一个新值

需要判断该值是否存在，遍历全部，在数组后面开辟一块空间存储数据，所以步骤数为 N + 1

e. 从集合开头删除

在数组前面删除一个数据，并将其他值左移一位，所以步骤数为1 + N - 1 = N

f. 从集合末尾删除

在数组后面删除一个数据，所以步骤数为1

## 3. 通常，数组的查找操作只寻找给定值的第一个实例。但有时我们想找出它的每一个实例。例如，我们可能想统计"apples"在数组中出现的次数。寻找所有的"apples"需要多少步呢？假设数组中有N个元素。

寻找所有的apples需要N步

# 二、有序数组和二分查找

## 1.  在有序数组[2, 4, 6, 8, 10, 12, 13]中线性查找数字8需要多少步？

线性查找需要4步，因为要一个一个索引查过去

## 2. 上一题使用二分查找需要多少步？

二分查找需要1步，刚好在中间

## 3. 对于包含100000个元素的数组，二分查找最多需要多少步

约等于计算log~2~^n^=100000，计算n的值，大约16或者17

# 三、大O计数

阶乘时间O(N!) 指数时间O(2^N^) 平方时间O(N^2^) 线性O(N) 对数O(log N) 常量O(1)

## 1. 下面的函数可以判断输入的年份是否是闰年，请用大O记法描述其时间复杂度。

```javascript
function isLeapYear(year) {
  return (year % 100 === 0) ? (year % 400 === 0) : (year % 4 === 0);
}
```

无for循环，且无论year多大，算法步骤都不会发生变化，所以是O(1)

## 2. 下面的函数可以计算数组中所有数的和，请用大O记法描述其时间复杂度。

```javascript
function arraySum(array) {
  let sum = 0;
  for(let i = 0; i < array.length; i++) {
    sum += array[i];
  }
  return sum;
}
```

存在for循环，且算法步骤随着array数组的大小而增多，所以是O(N)

## 3. 下面的函数是基于一个古老比喻编写的，它描述了复利的可怕之处。

```javascript
function chessboardSpace(numberOfGrains) {
  let chessboardSpaces = 1;
  let placedGrains = 1;
  while (placedGrains < numberOfGrains) {
    placedGrains *= 2;
    chessboardSpaces += 1;
  }
  return chessboardSpaces;
}
```

存在while循环，随着numberOfGrains的增多算法步骤增多，但是placedGrains的增长速度是指数级别，所以是O(log N)

## 4. 下面的函数会读取一个字符串数组，返回一个新数组，其中只包含开头是"a"的字符串。请用大O记法描述其时间复杂度。

```javascript
function selectAStrings(array) {
  let newArray = [];
  for(let i = 0; i < array.length; i++) {
    if (array[i].startsWith("a")) {
      newArray.push(array[i]);
    }
  }
  return newArray;
}
```

存在for循环，随着array数组长度的增大，算法步骤也同步增大，虽然内部存在判断逻辑，但是对整个算法步骤来说还是O(N)

## 5. 下面的函数会计算有序数组的中位数。请用大O记法描述其时间复杂度。

```javascript
function median(array) {
  const middle = Math.floor(array.length / 2);
  // 如果数组有偶数个数：
  if (array.length % 2 === 0) {
    return (array[middle - 1] + array[middle]) / 2;
  } else { // 如果数组有奇数个数：
    return array[middle];
  }
}
```

无论array数组多大，算法步骤不会增大，O(1)

# 四、选择排序，冒泡排序带来的O(N^2^) 

## 1. 对于特定数量的数据元素，不同类型的算法需要多少步？请将下表中的问号替换为相应的步骤数。

100 O(N)  = 100, O(log n) = 7, O(N^2^) =10000

2000 O(N)  = 2000 , O(log n) = 11, O(N^2^) =4000000

## 2. 如果一个O(N^2^) 算法处理数组需要256步，那么这个数组的大小是多少？

数组的大小大约是16

## 3. 用大O记法描述下面函数的时间复杂度。该函数会计算数组中任意两数乘积的最大值。

```python
def greatestProduct(array):
  greatestProductSoFar = array[0] * array[1]
  for i, iVal in enumerate(array):
    for j, jVal in enumerate(array):
      if i != j and iVal * jVal > greatestProductSoFar:
        greatestProductSoFar = iVal * jVal
  return greatestProductSoFar
```

两个for循环，且依赖array的数组大小，O(N^2^)

## 4. 下面的函数会查找数组中的单一最大值，但是其效率是O(N2)。请将函数优化为O(N)算法。

```python
def greatestNumber(array):
  for i in array:
    # 暂时假定i为最大值：
    isIValTheGreatest = True
    for j in array:
      # 假如发现了比i更大的值，那么i就不再是最大值了：
      if j > i:
        isIValTheGreatest = False
    # 如果检查了所有其他数后，i仍保持最大，那么i就是最大值：
    if isIValTheGreatest:
      return i

# 改变如下

def greatestNumber(array):
  greatestNumberSoFar = array[0] 
  for i in array:
    if i > greatestNumberSoFar:
        greatestNumberSoFar = i
  return greatestNumberSoFar
```

# 五、大O算法效率

## 1. 使用大O记法表示一个需要4N +16步的算法的时间复杂度。

O(N)

## 2. 使用大O记法表示一个需要2N2步的算法的时间复杂度。

O(N^2^)

## 3. 下面的函数会先把数组中所有的数加倍，然后再计算它们的和并返回。请用大O记法表示其时间复杂度。

```ruby
def double_then_sum(array)
  doubled_array = []
  array.each do |number|
    doubled_array << number *= 2
  end
  sum = 0
  doubled_array.each do |number|
    sum += number
  end
  return sum
end
```

两个for循环 2N 记为 O(N)

## 4. 下面的函数会读取一个字符串数组，并按不同格式（全部字母大写、全部字母小写、首字母大写）打印每个字符串。请用大O记法表示其时间复杂度。

```php
def multiple_cases(array)
  array.each do |string|
    puts string.upcase
    puts string.downcase
    puts string.capitalize
  end
end
```

O(N)

## 5. 下面的函数会遍历一个数字数组。每次遇到索引为偶数的数，就打印数组中所有数与该数的和。这个函数的时间复杂度是什么？

```ruby
def every_other(array)
  array.each_with_index do |number, index|
    if index.even?
      array.each do |other_number|
        puts number + other_number
      end
    end
  end
end
```

N * 1/2 N 记为 O(N^2^)

# 六、大O算法效率

## 1. 用大O记法描述一个需要3N2 + 2N + 1步的算法的效率。

O(N^2^)

## 2. 用大O记法描述一个需要N + log N步的算法的效率。

O(N)

## 3. 下面的函数可以检查数组中是否含有和为10的两个数。请描述最好、平均以及最坏情况，然后用大O记法表示最坏情况下的复杂度。

```php
function twoSum(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = 0; j < array.length; j++) {
      if (i !== j && array[i] + array[j] === 10) {
        return true;
      }
    }
  }
  return false;
}
```

最好的情况，第一层索引0，第二层索引1

平均的情况，第一层索引n/2，第二层索引n/2 + 1

最坏的情况，第一层索引n - 1，第二层索引n，O(N^2^)

## 4. 下面的函数会返回字符串中是否含有大写字母“X”。请用大O记法表示该函数的时间复杂度。然后修改代码，优化其在最好和平均情况下的效率。

```c#
function containsX(string) {
  foundX = false;
  for(let i = 0; i < string.length; i++) {
    if (string[i] === "_X_") {
      foundX = true;
    }
  }
  return foundX;
}

优化
    
function containsX(string) {
  foundX = false;
  for(let i = 0; i < string.length; i++) {
    if (string[i] === "_X_") {
      return true;
    }
  }
  return foundX;
}
    
```

O(N)

# 七、大O算法效率

## 1. 使用大O记法描述下面函数的时间复杂度。如果输入数组是一个“和为100的数组”，那么函数就会返回True，否则会返回False。

“和为100的数组”需要满足以下条件。·第一个元素和最后一个元素的和为100。·第二个元素和倒数第二个元素的和为100。·第三个元素和倒数第三个元素的和为100。以此类推。

```php
def one_hundred_sum?(array)
  left_index = 0
  right_index = array.length - 1
  while left_index < array.length / 2
    if array[left_index] + array[right_index] != 100
      return false
    end
    left_index += 1
    right_index -= 1
  end
  return true
end
```

O(N)

## 2. 使用大O记法描述下面函数的时间复杂度。该函数把两个已排序的数组结合起来为一个新的已排序数组，新数组要包含两个数组中的所有元素。

```ruby
def merge(array_1, array_2)
  new_array = []
  array_1_pointer = 0
  array_2_pointer = 0
  # 只有遍历完两个数组循环才结束：
  while array_1_pointer < array_1.length ||
      array_2_pointer < array_2.length
    # 如果遍历完第一个数组，那么就从第二个数组中添加元素：
    if !array_1[array_1_pointer]
      new_array << array_2[array_2_pointer]
      array_2_pointer += 1
    # 如果遍历完第二个数组，那么就从第一个数组中添加元素：
    elsif !array_2[array_2_pointer]
      new_array << array_1[array_1_pointer]
      array_1_pointer += 1
    # 如果第一个数组当前的数小于第二个数组的当前数，那么就从第一个数组中添加元素：
    elsif array_1[array_1_pointer] < array_2[array_2_pointer]
      new_array << array_1[array_1_pointer]
      array_1_pointer += 1
    # 如果第二个数组当前的数小于第一个数组的当前数，那么就从第二个数组中添加元素：
    else
      new_array << array_2[array_2_pointer]
      array_2_pointer += 1
    end
  end
  return new_array
end
```

O(N + M)

## 3.  使用大O记法描述下面函数的时间复杂度。该函数用来解决著名的“字符串搜索”问题。

needle和haystack都是字符串。假如needle是"def"而haystack是"abcdefghi"，那么因为"def"是"abcdefghi"的子串，所以needle就在haystack之中。但如果needle是"dd"，那么在haystack中就找不到它。如果在haystack中可以找到needle，那么函数就会返回True，否则会返回False

```ruby
def find_needle(needle, haystack)
  needle_index = 0
  haystack_index = 0
  while haystack_index < haystack.length
    if needle[needle_index] == haystack[haystack_index]
      found_needle = true
      while needle_index < needle.length
        if needle[needle_index] != haystack[haystack_index + needle_index]
          found_needle = false
          break
        end
        needle_index += 1
      end
      return true if found_needle
      needle_index = 0
    end
    haystack_index += 1
  end
  return false
end
```

O(N * M)

## 4. 使用大O记法描述下面函数的时间复杂度。该函数会计算输入数组中任意3个数乘积的最大值。

```SQL
def largest_product(array)
  largest_product_so_far = array[0] * array[1] * array[2]
  i = 0
  while i < array.length
    j = i + 1
    while j < array.length
      k = j + 1
      while k < array.length
        if array[i] * array[j] * array[k] > largest_product_so_far
          largest_product_so_far = array[i] * array[j] * array[k]
        end
        k += 1
      end
      j += 1
    end
    i += 1
  end
  return largest_product_so_far
end
```

O(N^3^)

## 5. 我听说过一个关于人事部门的笑话：“想要瞬间淘汰最不幸的应聘者吗？只要把桌上一半的简历扔进垃圾桶即可。”假设我们要写一个软件，不停地移除一堆简历中的一半，直到只剩下一份简历。可以交替移除上半和下半，也就是先扔掉上面的一半，然后扔掉剩下的简历中下面的一半。交替进行，最后留下一份幸运的简历，并雇用这个应聘者。用大O记法描述这个函数的效率。

```Ruby
def pick_resume(resumes)
  eliminate = "top"
  while resumes.length > 1
    if eliminate == "top"
      resumes = resumes[resumes.length / 2, resumes.length - 1]
      eliminate = "bottom"
    elsif eliminate == "bottom"
      resumes = resumes[0, resumes.length / 2]
      eliminate = "top"
    end
  end
  return resumes[0]
end
```

O(log N)

# 八、哈希表大O

## 1. 请编写一个函数，返回两个数组的交集。两个数组的交集是一个新数组，其中包括了两个数组共有的元素。例如，[1, 2, 3, 4, 5]和[0, 2, 4, 6, 8]的交集是[2, 4]。函数复杂度应为O(N)。（如果你使用的编程语言中有交集函数，那么请不要直接使用。希望你能自己思考算法。）

```java
public static List<Integer> getResult(int[] array1, int[] array2) {
    Set<Integer> set = new HashSet<>();
    List<Integer> list = new ArrayList<>();
    for (int i : array1) {
        set.add(i);
    }
    for (int j : array2) {
        if (set.contains(j)) {
            list.add(j);
        }
    }
    return list;
}
```

## 2. 请编写一个函数，该函数会读取一个字符串数组并返回第一个重复的值。如果输入是["a", "b", "c", "d", "c", "e", "f"]，那么因为"c"在数组中出现了两次，所以函数需要返回"c"。（假设数组中只有一对重复的值。）函数复杂度应为O(N)。

```java
public static String getResult(String[] array) {
    Set<String> set = new HashSet<>();
    for (String i : array) {
        if (set.contains(i)) {
            return i;
        }
        set.add(i);
    }
}
```

## 3. 有的字符串会包含26个英文字母中的25个。例如，字符串"the quick brown box jumps over a lazy dog"包含除了"f"以外的所有字母。请编写一个函数，读取满足上述要求的字符串，并返回缺失的字母。函数复杂度应为O(N)。

```java
public static Character getResult(String str) {
    Set<Character> set = new HashSet<>();
    for (char ch : str.toCharArray()) {
   		set.add(ch);
    }
    for (char ch = 'a'; ch <= 'z'; ch++) {
     	if (!set.contains(ch)) {
            return ch;
        }
    }
    return null;
}
```

## 4. 请编写一个函数，返回输入字符串中第一个不重复的字母。例如，字符串"minimum"中有两个字母只出现了一次，分别为"n"和"u"。因为"n"更早出现，所以函数读取该字符串应该返回"n"。函数复杂度应为O(N)。

```java
public static Character getResult(String str) {
    Map<Character, Integer> map = new HashMap<>();
    for (char ch : str.toCharArray()) {
   		if (map.containsKey(ch)) {
            map.put(ch, map.get(ch) + 1);
        } else {
            map.put(ch, 1);
        }
    }
    for (char ch : str.toCharArray()) {
   		if (map.get(ch) == 1) {
            return ch;
        }
    }
    return null;
}
```

# 九、栈和队列

## 1. 假如你要为客服中心写一个软件，暂时挂起电话并转接到“下一个空闲的客服代表”。你会使用栈还是队列？

要排队，用队列

## 2. 假如按如下顺序压栈：1、2、3、4、5、6。然后又弹出两个元素。你现在能从栈中读取到哪个数呢？

4， 3， 2， 1

## 3. 假如按如下顺序入队：1、2、3、4、5、6。然后出队两个元素。你现在能从队列中读取到哪个数呢？

3，4，5，6

## 4. 编写一个使用栈来反转字符串的函数。（例如，"abcde"会被反转为"edcba"。）你可以使用本章中的Stack类实现。

```java
public static void printStr(String str) {
    Stack<Character> stack = new Stack<>();
    for (char ch : str.toCharArray()) {
        stack.push(ch);
    }
    while (!stack.isEmpty()) {
        stack.pop();
    }
}
```

# 十、递归

## 1. 下面的函数会把low和high之间的数字每隔一个打印出来。如果low是0而high是10，那么函数会打印如下数字。请指出该函数的基准情形。

```ruby
0
2
4
6
8
10
def print_every_other(low, high)
  return if low > high
  puts low
  print_every_other(low + 2, high)
end
```

基准情形 当low的值大于high的时候

## 2. 我家小孩儿在玩我的计算机时，把factorial函数的计算方式从n * factorial(n - 1)改成了n * factorial(n - 2)。请预测factorial(10)的行为。

```ruby
def factorial(n)
  return 1 if n == 1
  return n * factorial(n - 2)
end
```

factorial(10)会无限递归，直到栈溢出

## 3. 下面的函数接受两个输入：low和high。函数会返回low和high之间所有数的和。如果low是1，high是10，那么函数就会返回1和10之间所有数的和，也就是55。不过，这段代码缺少基准情形，会无限运行下去。请添加正确的基准情形来修复代码

```python
def sum(low, high)
  if high == low :
      return low
  return high + sum(low, high - 1)
end
```

## 4. 下面的数组中既包含数字，也包含其他数组，而这些数组又可能包含数字和数组。请编写一个递归函数，打印其中的所有数字（只打印数字）。

```c#
array = [  1,
           2,
           3,
           [4, 5, 6],
           7,
           [8,
             [9, 10, 11,
               [12, 13, 14]
             ]
           ],
           [15, 16, 17, 18, 19,
             [20, 21, 22,
               [23, 24, 25,
                 [26, 27, 29]
               ], 30, 31
             ], 32
           ], 33
        ]
```

```java
public static void printArray(Object[] objecArray) {
    for (Object obj : objecArray) {
        if (obj instanceof int) {
            print(obj)
        } else {
            printArray(obj);
        }
    }
}
```

递归类别：重复执行， 计算，递归是实现自上而下策略的唯一方法

# 十一、递归

## 1. 使用递归编写一个函数，读取一个字符串数组，返回所有字符串的字母数之和。如果输入数组是["ab", "c", "def", "ghij"]，那么因为一共有10个字母，所以函数应该返回10。

```java
public static int getStrNum(String[] strArr) {
    if (strArr.length == 1) {
        return strArr[0].length();
    }
    String[] dest = new String[strArr.length - 1];
    System.arraycopy(strArr, 1, dest, 0, strArr.length - 1);
    return strArr[0].length() + getStrNum(dest);
}
```

## 2. 使用递归编写一个函数，读取一个数字数组，返回一个新数组，其中只包含原数组中的偶数。

```java
public static List<Integer> getNumArr(int[] numArr) {
    List<Integer> list = new ArrayList<>();
    if (numArr.length == 1) {
        if (numArr[0] % 2 == 0) {
            list.add(numArr[0]);
        }
        return list;
    }
    if (numArr[0] % 2 == 0) {
        list.add(numArr[0]);
    }
    int[] dest = new int[numArr.length - 1];
    System.arraycopy(numArr, 1, dest, 0, numArr.length - 1);
    list.addAll(getNumArr(dest));
    return list;
}
```

## 3. 有一个叫作“三角数”的数列。这个数列开头的几个数是1、3、6、10、15、21。数列的第N个数正好是前一个数加上N。例如，数列的第7个数是28，也就是7（N）加上21（数列中前一个数）。编写一个函数，读取N的值，返回数列中对应的数。换言之，如果函数的输入是7，那么它需要返回28。

```java
public static int getResult(int num) {
    if (num == 1) {
        return 1;
    }
    return num + getResult(num - 1);
}
```

## 4. 使用递归编写一个函数，读取一个字符串，返回字母“x”第一次出现的位置。例如，字符串"abcdefghijklmnopqrstuvwxyz"中“x”第一次出现在索引23处。为简单起见，假设字符串一定至少有一个“x”。

```java
public static int getIndex(String str, int index) {
    if (str.charAt(index) == 'x') {
        return index;
    }
    return getIndex(str, ++index);
}
```

## 5. 下面这个问题也被称为“不同路径”问题：假设你有一个网格。编写一个函数，以网格的行数和列数作为输入，计算从网格左上角到右下角“最短”路径的个数。例如，下图是一个3行7列的网格。你需要从“S”（起点）走到“F”（终点）。最短”路径的意思是：每一步都只能向右移动1步,或者向下移动1步

```java
public static int getShortResult(int row, int column) {
    if (row == 1 || column == 1) {
        return 1;
    }
    return getShortResult(row, column - 1) + getShortResult(row - 1, column);
}
```

# 十二、动态规划

使用记忆化消除递归的重复调用，就是记录已经计算的值；

或者使用循环自下而上的解决问题

## 1.  下面的函数会以一个数字数组作为输入。只要没有某一个数让数组中数的和超过100，就返回这个和。如果某一个数会让和大于100，就跳过它。不过这个函数存在不必要的递归调用。请修改代码，消除这些不必要的递归。

```sql
def add_until_100(array)
  return 0 if array.length == 0
  if array[0] + add_until_100(array[1, array.length - 1]) > 100
    return add_until_100(array[1, array.length - 1])
  else
    return array[0] + add_until_100(array[1, array.length - 1])
  end
end

感觉像3^N

def add_until_100(array)
  return 0 if array.length == 0
  temp = add_until_100(array[1, array.length - 1])
  if array[0] + temp > 100
    return temp
  else
    return array[0] + temp
  end
end
```

## 2. 下面的函数会使用递归来计算“格伦布数列”的第N项，但它非常低效。请用记忆化来优化代码。（不了解格伦布数列也能完成这个习题。）

```ruby
def golomb(n, mmem={})
  return 1 if n == 1
  if !mmem[n]
  	mmem[n] = 1 + golomb(n - golomb(golomb(n - 1, mmem), mmem), mmem);
  end
  return mmem[n]
end
```

## 3. 下面是第11章“不同路径”问题的一种解法。请用记忆化来优化它的效率。

```sql
def unique_paths(rows, columns, mmem={})
  return 1 if rows == 1 || columns == 1
  if !mmem[[rows, columns]]
  	mmem[[rows, columns]] = unique_paths(rows - 1, columns, mmem) + unique_paths(rows, columns - 1, mmem)
  end
  return mmem[[rows, columns]]
end
```

# 十三、快速排序和快速选择 递归

快速排序和快速选择，都是通过快排，分区，找出基准值，不断递归得到结果

## 1. 请编写一个函数，返回正数数组中任意3个数的最大乘积。使用三层嵌套循环的算法很慢，复杂度是O(N3)。请利用排序让函数的复杂度降至O(N log N)。（其实还有更快的实现，但这里只关注如何用排序给算法提速。）

```java
public static void quickSort(int leftIndex, int rightIndex, int[] arr) {
    // 1.找到右边第一个做为基准值
    // 2.最左边是左角标，右边倒数第二个就是右角标
    // 3.判断左角标对应的值是否大于等于基准值，不大于向右走
    // 4.判断右角标对应的值是否小于等于基准值，不小于向左走，走到最左边停止
    // 5.如果左角标小于右角标，重复3,4步骤
    // 6.如果左角标大于等于右角标，交换左角标及基准值，基准值左边的值都小于等于基准值，基准值右边的值都大于等于基准值，递归两边的值
    if (rightIndex - leftIndex <= 0) {
        return;
    }
    int tempLeftIndex = leftIndex;
    int tempRightIndex = rightIndex;
    int pointIndex = rightIndex;
    rightIndex -= 1;
    while (true) {
        while (arr[leftIndex] < arr[pointIndex]) {
            leftIndex++;
        }
        while (arr[rightIndex] > arr[pointIndex] && rightIndex > 0) {
            rightIndex--;
        }
        if (leftIndex < rightIndex) {
            int temp = arr[leftIndex];
            arr[leftIndex] = arr[rightIndex];
            arr[rightIndex] = temp;
        } else {
            int temp = arr[leftIndex];
            arr[leftIndex] = arr[pointIndex];
            arr[pointIndex] = temp;
            pointIndex = leftIndex;
            break;
        }
    }
    quickSort(tempLeftIndex, pointIndex - 1, arr);
    quickSort(pointIndex + 1, tempRightIndex, arr);
}

public static int getMaxResult(int[] arr) {
    quickSort(0, arr.length - 1, arr);
    return arr[arr.length - 1] * arr[arr.length - 2] * arr[arr.length - 3];
}
```

## 2. 下面的函数可以找出整数数组中“缺失的数”。这些数组本应包含0和数组长度之间的所有整数，但是现在缺少一个数。例如，数组[5, 2, 4, 1, 0]就缺少3，而数组[9, 3,2, 5, 6, 7, 1, 0, 4]则缺少8。下面的实现复杂度是O(N2)。（因为计算机需要搜索整个数组找到n，所以includes方法本身就已经是O(N)了。）

```php
function findMissingNumber(array) {
  for(let i = 0; i < array.length; i++) {
    if(!array.includes(i)) {
      return i;
    }
  }
  // 如果所有数都存在：
  return null;
}
```

请用排序实现该函数，把复杂度降至O(N log N)。（其实还有更快的实现，但这里只关注如何用排序给算法提速。）

```java
public static int getMissNum(int[] arr) {
    quickSort(0, arr.length - 1, arr);
    for (int i = 0; i < arr.length; i++) {
        if (i != arr[i]) {
            return i;
        }
    }
    return -1;
}
```

## 3.  请写出3种寻找数组最大值的实现，使它们的复杂度分别为O(N2)、O(N log N)和O(N)。

```java
public static int getMaxNum1(int[] arr) {
    selectSort(arr);
    return arr[arr.length - 1];
}

public static int getMaxNum2(int[] arr) {
    quickSort(0, arr.length - 1, arr);
    return arr[arr.length - 1];
}

public static int getMaxNum3(int[] arr) {
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}
```

# 十四、链表 队列

# 十五、二叉树 各方面优秀的有序队列

# 十六、堆 优先队列

# 十七、字典树 补充单词

# 十八、图 深度优先搜索（递归） 广度优先搜索（队列） 社交网络 图数据库 加权图 最短路径问题 迪杰斯特拉算法

# 十九、空间复杂度的大O记法

对一个有O(1)时间复杂度的算法来说，无论数据量多大，它的运行速度都保持恒定。同理，对一个有O(1)空间复杂度的算法来说，无论数据量多大，它消耗的内存都保持恒定。

我们只关注算法消耗的额外空间。这个额外空间有一个正式名称——辅助空间。

## 1. 下面是7.2节介绍过的“构词程序”算法。请用大O记法描述其空间复杂度。

```php
function wordBuilder(array) {
  let collection = [];
  for(let i = 0; i < array.length; i++) {
    for(let j = 0; j < array.length; j++) {
      if (i !== j) {
        collection.push(array[i] + array[j]);
      }
    }
  }
  return collection;
}
```

O(N^2^)

## 2. 下面是一个数组逆序函数。请用大O记法描述其空间复杂度。

```php
function reverse(array) {
  let newArray = [];
  for (let i = array.length - 1; i >= 0; i--) {
    newArray.push(array[i]);
  }
  return newArray;
}
```

O(N)

## 3. 请编写一个新的只使用O(1)额外空间的数组逆序函数。

```java
public static void reverse(int[] array) {
    int i = 0;
    int j = array.length - 1;
    while (i < j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
        i++;
        j--;
    }
}
```

## 4. 下面是同一个函数的3种不同实现。该函数以一个数字数组为参数，返回一个新数组，新数组的值等于原数组中对应值的两倍。如果输入是[5, 4, 3, 2, 1]，那么输出就是[10, 8, 6, 4, 2]。

```php
function doubleArray1(array) {
  let newArray = [];
  for(let i = 0; i < array.length; i++) {
    newArray.push(array[i] * 2);
  }
  return newArray;
}
function doubleArray2(array) {
  for(let i = 0; i < array.length; i++) {
    array[i] *= 2;
  }
  return array;
}
function doubleArray3(array, index=0) {
  if (index >= array.length) { return; }
  array[index] *= 2;
  doubleArray3(array, index + 1);
  return array;
}
```

时间 O(N) 空间 O(N)

时间 O(N) 空间 O(1)

时间 O(N) 空间 O(N)

# 二十、代码优化技巧 贪心算法

(1) 确定当前算法的复杂度。（也就是前置工作。）

(2) 确定当前问题的最理想复杂度。

(3) 如果最理想复杂度比当前复杂度低，那么就可以尝试优化代码，让它的复杂度尽可能接近最理想复杂度。

