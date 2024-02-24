> key：第一步判断指针所在的对象是谁，第二步确定左右指针。
>
> 这两个指针会演变出数值加和，平方和；字符位置改变

# 1. 有序数组-**非递减顺序排列**

167.Two Sum II - Input array is sorted (Easy)

[Leetcode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/) / [力扣](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/description/)

```
Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2
```

* **Question：在有序数组中找出两个数，使它们的和为 target，并返回index**
* **Solution：**

> [!NOTE]
>
> 使用双指针，一个指针指向值较小的元素，一个指针指向值较大的元素。指向较小元素的指针从头向尾遍历，指向较大元素的指针从尾向头遍历。
>
> - 如果两个指针指向元素的和 sum == target，那么得到要求的结果；
> - 如果 sum > target，移动较大的元素，使 sum 变小一些；
> - 如果 sum < target，移动较小的元素，使 sum 变大一些。
>
> 数组中的元素最多遍历一次，时间复杂度为 O(N)。只使用了两个额外变量，空间复杂度为 O(1)。

* **Answer：**

  `Java`

  ```java
  public int[] twoSum(int[] numbers, int target) {
      if (numbers == null) return null;
      int i = 0, j = numbers.length - 1;
      while (i < j) {
          int sum = numbers[i] + numbers[j];
          if (sum == target) {
              return new int[]{i + 1, j + 1};
          } else if (sum < target) {
              i++;
          } else {
              j--;
          }
      }
      return null;
  }
  ```

  `Python`

  ```python
  class Solution:
      def twoSum(self, numbers: List[int], target: int) -> List[int]:
          if numbers is None:
              return None
          i = 0
          j = len(numbers)-1
          while i<j:
              sum=numbers[i]+numbers[j]
              if sum == target:
                  return i+1, j+1
              elif sum > target:
                  j-=1
              else:
                  i+=1
          return None
  ```

  

# 2.两平方之和

633. Sum of Square Numbers (Easy)

[Leetcode](https://leetcode.com/problems/sum-of-square-numbers/description/) / [力扣](https://leetcode-cn.com/problems/sum-of-square-numbers/description/)

```
Input: 5
Output: True
Explanation: 1 * 1 + 2 * 2 = 5
```

* **Question：判断一个非负整数是否为两个整数的平方和**

  Given a non-negative integer `c`, decide whether there're two integers `a` and `b` such that `a2 + b2 = c`.

* **Solution：**

> [!NOTE]
>
> 本题和 167. Two Sum II - Input array is sorted 类似，二者有一个明显区别：一个是和为 target，一个是平方和为 target。本题同样可以使用双指针得到两个数，使其平方和为 target。
>
> 因为都是非负整数，所以左指针最小为0，右指针最大为sqrt(target)
>
> 只需要遍历一次 0~sqrt(target)，所以时间复杂度为 O(sqrt(target))。又因为只使用了两个额外的变量，因此空间复杂度为 O(1)。

* **Answer：**

`Java`

```java
 public boolean judgeSquareSum(int target) {
     if (target < 0) return false;
     int i = 0, j = (int) Math.sqrt(target);
     while (i <= j) {
         int powSum = i * i + j * j;
         if (powSum == target) {
             return true;
         } else if (powSum > target) {
             j--;
         } else {
             i++;
         }
     }
     return false;
 }
```

# 3.反转字符串中的元音字符

345. Reverse Vowels of a String (Easy)

[Leetcode](https://leetcode.com/problems/reverse-vowels-of-a-string/description/) / [力扣](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/description/)

```
Given s = "leetcode", return "leotcede".
```

* **Question：**
* **Solution：**

> [!NOTE]
>
> 使用双指针，一个指针从头向尾遍历，一个指针从尾到头遍历，当两个指针都遍历到元音字符时，交换这两个元音字符。
>
> 为了快速判断一个字符是不是元音字符，我们将全部元音字符添加到集合 HashSet 中，从而以 O(1) 的时间复杂度进行该操作。
>
> - 时间复杂度为 O(N)：只需要遍历所有元素一次
> - 空间复杂度 O(1)：只需要使用两个额外变量

* **Answer：**

  `Java`
  
  ```java
  //private 这表示该字段是私有的，只能在同一个类中访问
  //final: 这表示该字段是不可变的，一旦被赋值后就不能被修改
  //HashSet<Character> vowels，哈希集合vowels中没有重复元素，并且元素没有顺序。Character是一个包装类，用于表示单个字符
  //new HashSet<>赋值给vowels
  private final static HashSet<Character> vowels = new HashSet<>(
          Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));
  
  public String reverseVowels(String s) {
      if (s == null) return null;
      int i = 0, j = s.length() - 1;
    //创建了一个字符数组 result，数组的长度与字符串 s 的长度相同，如果s长度为2，result = ['\0','\0']
    //new 关键字用于创建新的对象实例或者分配新的数组空间
      char[] result = new char[s.length()];
      while (i <= j) {
        //获取字符串 s 中索引为 i 的字符，并将其存储在变量 ci 中
          char ci = s.charAt(i);
          char cj = s.charAt(j);
        //两个元音，那么两个if都不通过，说明两个字母是元音，交换位置，写入result
        //两个非元音，先写入第一个，第二个保持不变
        //一个元音一个非元音，非元音写入
          if (!vowels.contains(ci)) {
            //i++ 是一个后增量操作符，先将ci赋值给result[i]，i再做加1
              result[i++] = ci;
          } else if (!vowels.contains(cj)) {
              result[j--] = cj;
          } else {
              result[i++] = cj;
              result[j--] = ci;
          }
      }
    //将char转换成string格式
      return new String(result);
  } 
  ```
  
  `Python`
  
  ```python
  class Solution:
      vowels = {'a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'}
      def reverseVowels(self, s: str) -> str:
          if s is None:
              return None
          i, j = 0, len(s) - 1
          result = [''] * len(s)
          while i <= j:
              ci, cj = s[i], s[j]
              if ci not in self.vowels:
                  result[i] = ci
                  i += 1
              elif cj not in self.vowels:
                  result[j] = cj
                  j -= 1
              else:
                  result[i], result[j] = cj, ci
                  i += 1
                  j -= 1
          return ''.join(result)
  ```
  
  
