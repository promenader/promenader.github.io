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







