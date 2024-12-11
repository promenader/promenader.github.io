# 数据结构与算法-Java



## 第一篇：数据结构



### 1、数组

数组初始化

```java
public class ArrayCreation {
    public static void main(String[] args) {
        int length = 5;
        // 1. 声明并初始化
        int[] arr1 = new int[length];                    // 默认值为0
        int[] arr2 = {1, 2, 3, 4, 5};              // 直接初始化
        int[] arr3 = new int[]{1, 2, 3, 4, 5};     // 另一种初始化方式
        
        // 2. 二维数组
        int n =3,m=4;
        int[][] matrix1 = new int[n][m];            // 3行4列
        int[][] matrix2 = {
                {1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}
        };

        // 3. 不规则数组
        int[][] irregular = new int[3][];
        irregular[0] = new int[3];
        irregular[1] = new int[4];
        irregular[2] = new int[2];
    }
}
```

数组基本操作

```java
import java.util.Arrays;

public class ArrayOperations {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};

        // 1. 访问元素
        int firstElement = arr[0];          // 获取第一个元素
        arr[1] = 10;                        // 修改元素

        // 2. 获取长度
        int length = arr.length;            // 数组长度

        // 3. 遍历数组
        // 方式1：for循环
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
        // 方式2：增强for循环
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
        // 方式3：Arrays.toString()
        System.out.println(Arrays.toString(arr));
    }
}
```

Arrays工具类使用

```java
import java.util.Arrays;
import java.util.List;

public class ArraysUtilDemo {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 1, 9};

        // 1. 排序
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));

        // 2. 二分查找（要求数组已排序）
        int index = Arrays.binarySearch(arr, 8);
        System.out.println(index);

        // 3. 填充数组
        int[] newArr = new int[5];
        Arrays.fill(newArr, 10);
        System.out.println(Arrays.toString(newArr));

        // 4. 复制数组
        int[] copy1 = Arrays.copyOf(arr, arr.length);
        int[] copy2 = Arrays.copyOfRange(arr, 1, 4);  // 复制索引1到3的元素
        System.out.println(Arrays.toString(copy1));
        System.out.println(Arrays.toString(copy2));

        // 5. 比较数组
        int[] arr2 = {5, 2, 8, 1, 9};
        boolean isEqual = Arrays.equals(arr, arr2);
        System.out.println(isEqual);

        // 6. 转换为List（注意：转换后的List是固定大小的）
        Integer[] numbers = {1, 2, 3, 4, 5};
        List<Integer> list = Arrays.asList(numbers);
        System.out.println(list);
    }
}
```



### 2、List

List的创建

```java
import java.util.*;

public class ListCreation {
    public static void main(String[] args) {
        // 1. ArrayList创建
        List<String> list1 = new ArrayList<>();
        List<String> list2 = new ArrayList<>(20);  // 指定初始容量

        // 2. 使用Arrays.asList()创建
        List<String> list3 = Arrays.asList("A", "B", "C");

        // 3. 使用List.of()创建不可变List (Java 9+)
        List<String> list4 = List.of("A", "B", "C");

        // 4. LinkedList创建
        List<String> list5 = new LinkedList<>();
    }
}
```



List的基本操作

```java
import java.util.*;
public class ListOperations {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();

        // 1. 添加元素
        list.add("A");                  // 添加到末尾
        list.add(0, "B");              // 在指定位置添加
        list.addAll(Arrays.asList("C", "D")); // 添加集合

        // 2. 访问元素
        String first = list.get(0);     // 获取元素
        list.set(1, "E");              // 修改元素

        // 3. 删除元素
        list.remove(0);                // 按索引删除
        list.remove("A");              // 按对象删除
        list.removeAll(Arrays.asList("B", "C")); // 删除多个元素

        // 4. 查找元素
        boolean contains = list.contains("D");
        int index = list.indexOf("D");
        int lastIndex = list.lastIndexOf("D");

        list.add("B");
        list.add("C");
        // 5. 获取子列表
        List<String> subList = list.subList(1, 3); // [fromIndex, toIndex)

        // 6. 清空列表
        list.clear();

        // 7. 判空和大小
        boolean isEmpty = list.isEmpty();
        int size = list.size();
    }
}
```



List的遍历

```java
import java.util.*;

public class ListIteration {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("A", "B", "C", "D");

        // 1. for循环
        for (int i = 0; i < list.size(); i++) {
            System.out.print(list.get(i) + " ");
        }

        // 2. 增强for循环
        for (String item : list) {
            System.out.print(item + " ");
        }

        // 3. Iterator
        Iterator<String> iterator = list.iterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }

        // 4. ListIterator（可以双向遍历）
        ListIterator<String> listIterator = list.listIterator();
        while (listIterator.hasNext()) {
            System.out.print(listIterator.next() + " ");
        }

        // 5. Stream API (Java 8+)
        list.stream().forEach(System.out::print);

        // 6. forEach方法 (Java 8+)
        list.forEach(System.out::print);
    }
}
```

List的排序

```java
import java.util.*;

public class ListSortSearch {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>(Arrays.asList("D", "B", "A", "C"));

        // 1. 排序
        Collections.sort(list);  // 自然顺序排序

        // 使用Comparator排序
        Collections.sort(list, (a, b) -> b.compareTo(a));  // 降序
        list.sort((a, b) -> a.compareTo(b));  // 另一种方式
        list.sort(new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o1.compareTo(o2);
            }
        });//升序
        list.sort(new Comparator<String>() {
            @Override
            public int compare(String o1, String o2) {
                return o2.compareTo(o1);
            }
        });//降序
        // 2. 二分查找（要求列表已排序）
        Collections.sort(list);
        int index = Collections.binarySearch(list, "B");

        // 3. 查找最大最小值
        String max = Collections.max(list);
        String min = Collections.min(list);

        // 4. 频率统计
        int frequency = Collections.frequency(list, "A");
    }
}
```

List的转换

```java
import java.util.*;
import java.util.stream.Collectors;

public class ListConversion {
    public static void main(String[] args) {
        // 1. List转数组
        List<String> list = Arrays.asList("A", "B", "C");

        // 转Object数组
        Object[] objArray = list.toArray();

        // 转指定类型数组
        String[] strArray = list.toArray(new String[0]);

        // 2. 数组转List
        String[] array = {"A", "B", "C"};
        List<String> list1 = Arrays.asList(array);        // 固定大小
        List<String> list2 = new ArrayList<>(Arrays.asList(array)); // 可变大小

        // 3. List转Set
        Set<String> set = new HashSet<>(list);

        // 4. Stream转换
        List<String> upperList = list.stream()
                .map(String::toUpperCase)
                .collect(Collectors.toList());
    }
}
```

List自定义对象的使用

```java
import java.util.*;
class Person {
    public String name;
    public int age;

    public Person(String name, int age) {
        this.name=name;
        this.age=age;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person person = (Person) o;
        return age == person.age && Objects.equals(name, person.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
}

public class CustomObjectList {
    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();

        // 添加对象
        people.add(new Person("Alice", 25));
        people.add(new Person("Bob", 30));

        // 排序
        Collections.sort(people, new Comparator<Person>() {
            @Override
            public int compare(Person o1, Person o2) {
                return o1.age-o2.age;
            }
        });//根据age进行升序排列
        Collections.sort(people, new Comparator<Person>() {
                    @Override
                    public int compare(Person o1, Person o2) {
                        return o1.name.compareTo(o2.name);
                    }
        });//根据name升序排列

                // 查找
                Person searchPerson = new Person("Alice", 25);
        boolean contains = people.contains(searchPerson); // 需要正确实现equals方法
    }
}
```



### 3、Set集合

集合是一组不重复数据的集合

set集合的创建

```java
import java.util.*;

public class SetCreation {
    public static void main(String[] args) {
        // 1. HashSet - 无序
        Set<String> hashSet = new HashSet<>();
        Set<String> hashSet2 = new HashSet<>(Arrays.asList("A", "B", "C"));

        // 2. LinkedHashSet - 保持插入顺序
        Set<String> linkedHashSet = new LinkedHashSet<>();

        // 3. TreeSet - 有序（自然顺序或指定比较器）
        Set<String> treeSet = new TreeSet<>();
        Set<String> treeSet2 = new TreeSet<>((a, b) -> b.compareTo(a)); // 降序

        // 4. 不可变Set (Java 9+)
        Set<String> immutableSet = Set.of("A", "B", "C");

        // 5. 同步Set
        Set<String> syncSet = Collections.synchronizedSet(new HashSet<>());
    }
}
```



Set的基本操作

```java
import java.util.*;

public class SetOperations {
    public static void main(String[] args) {
        Set<String> set = new HashSet<>();

        // 1. 添加元素
        set.add("A");
        set.addAll(Arrays.asList("B", "C", "D"));

        // 2. 删除元素
        set.remove("A");
        set.removeAll(Arrays.asList("B", "C"));

        // 3. 查询操作
        boolean contains = set.contains("D");
        boolean isEmpty = set.isEmpty();
        int size = set.size();

        // 4. 清空Set
        set.clear();

        // 5. 集合操作
        Set<String> set1 = new HashSet<>(Arrays.asList("A", "B", "C"));
        Set<String> set2 = new HashSet<>(Arrays.asList("B", "C", "D"));

        // 并集
        Set<String> union = new HashSet<>(set1);
        union.addAll(set2);

        // 交集
        Set<String> intersection = new HashSet<>(set1);
        intersection.retainAll(set2);

        // 差集
        Set<String> difference = new HashSet<>(set1);
        difference.removeAll(set2);
    }
}
```

Set的遍历操作

```java
import java.util.*;

public class SetIteration {
    public static void main(String[] args) {
        Set<String> set = new HashSet<>(Arrays.asList("A", "B", "C"));

        // 1. 增强for循环
        for (String element : set) {
            System.out.print(element + " ");
        }

        // 2. Iterator
        Iterator<String> iterator = set.iterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }

        // 3. forEach方法 (Java 8+)
        set.forEach(System.out::print);

        // 4. Stream API (Java 8+)
        set.stream()
                .forEach(System.out::print);
    }
}
```



Set的不同实现方式

```java
import java.util.*;
public class SetImplementations {
    public static void main(String[] args) {
        // 1. HashSet - 最快的实现，无序
        Set<String> hashSet = new HashSet<>();
        hashSet.add("B");
        hashSet.add("A");
        hashSet.add("C");
        System.out.println("HashSet: " + hashSet); // 输出顺序不确定

        // 2. LinkedHashSet - 保持插入顺序
        Set<String> linkedHashSet = new LinkedHashSet<>();
        linkedHashSet.add("B");
        linkedHashSet.add("A");
        linkedHashSet.add("C");
        System.out.println("LinkedHashSet: " + linkedHashSet); // 按插入顺序输出

        // 3. TreeSet - 有序（自然顺序或自定义顺序）
        Set<String> treeSet = new TreeSet<>();
        treeSet.add("B");
        treeSet.add("A");
        treeSet.add("C");
        System.out.println("TreeSet: " + treeSet); // 按字母顺序输出

        // 自定义排序的TreeSet
        Set<String> customTreeSet = new TreeSet<>((a, b) -> b.compareTo(a));
        customTreeSet.addAll(Arrays.asList("B", "A", "C"));
        System.out.println("Custom TreeSet: " + customTreeSet); // 按字母降序输出
    }
}
```

Set的转换

```java
import java.util.*;
import java.util.stream.Stream;

public class SetConversion {
    public static void main(String[] args) {
        Set<String> set = new HashSet<>(Arrays.asList("A", "B", "C"));

        // 1. Set转数组
        String[] array = set.toArray(new String[0]);

        // 2. Set转List
        List<String> list = new ArrayList<>(set);

        // 3. Set转Stream
        Stream<String> stream = set.stream();

        // 4. 不同Set实现之间的转换
        Set<String> hashSet = new HashSet<>(set);
        Set<String> linkedHashSet = new LinkedHashSet<>(set);
        Set<String> treeSet = new TreeSet<>(set);
    }
}
```



### 4、Map类型

Map的创建

```java
import java.util.*;

public class MapCreation {
    public static void main(String[] args) {
        // 1. HashMap - 无序
        Map<String, Integer> hashMap = new HashMap<>();
        // 初始容量和负载因子,负载因子越小冲突越少，内存使用越多
        Map<String, Integer> hashMap2 = new HashMap<>(16, 0.75f);

        // 2. TreeMap - 按键排序
        Map<String, Integer> treeMap = new TreeMap<>();
        Map<String, Integer> treeMap2 = new TreeMap<>((a, b) -> b.compareTo(a)); // 自定义排序

        // 3. LinkedHashMap - 保持插入顺序
        Map<String, Integer> linkedHashMap = new LinkedHashMap<>();

        // 4. 不可变Map (Java 9+)
        Map<String, Integer> immutableMap = Map.of(
                "A", 1,
                "B", 2,
                "C", 3
        );

        // 5. 同步Map
        Map<String, Integer> syncMap = Collections.synchronizedMap(new HashMap<>());

        // 6. 使用Map.entry创建
        Map<String, Integer> map = Map.ofEntries(
                Map.entry("A", 1),
                Map.entry("B", 2)
        );
    }
}
```

