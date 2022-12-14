## 经典算法

### 1.LRU缓存算法

### 2.排序算法
#### 2.1总览
![image](https://static001.geekbang.org/resource/image/1f/fd/1f6ef7e0a5365d6e9d68f0ccc71755fd.jpg?wh=1142*698)
1.排序的稳定性:  
如果待排序的序列中存在值相等的元素，经过排序之后，相等元素之间原有的先后顺序不变。  
2.原地排序:  
空间复杂度为O(1)的排序算法。
#### 2.2冒泡排序
冒泡排序只会操作相邻的两个数据。每次冒泡操作都会对相邻的两个元素进行比较，看是否满足大小关系要求。如果不满足就让它俩互换。一次冒泡会让至少一个元素移动到它应该在的位置，重复 n 次，就完成了 n 个数据的排序工作。  
#### 2.3插入排序
1.将数组分为两个区间,已排序和未排序区间。  
2.初始已排序空间的元素只有一个->数组的第一个元素。  
3.核心思想:取未排序区间中的元素，在已排序区间中找到合适的插入位置将其插入，并保证已排序区间数据一直有序。重复这个过程，直到未排序区间中元素为空。
#### 2.4选择排序
1.将数组分为两个区间,已排序和未排序区间。    
2.首先找到最小的元素放入已排序区间的第一位。  
3.每次从未排序区间中找到最小的元素，将其放到已排序区间的末尾。  
#### 2.5归并排序  
TODO
#### 2.6快速排序
TODO

### 3.二分查找
#### 3.1二分查找基础模板
```
public int bsearch(int[] a, int n, int value) {
  int low = 0;
  int high = n - 1;

  while (low <= high) {
    int mid = (low + high) / 2;
    if (a[mid] == value) {
      return mid;
    } else if (a[mid] < value) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }

  return -1;
}
```
#### 3.2二分查找-查找第一个值等于给定值的元素
```
public int bsearch(int[] a, int n, int value) {
  int low = 0;
  int high = n - 1;
  while (low <= high) {
    int mid =  low + ((high - low)/2);
    if (a[mid] > value) {
      high = mid - 1;
    } else if (a[mid] < value) {
      low = mid + 1;
    } else {
      if ((mid == 0) || (a[mid - 1] != value)) {
      return mid;
      }else{
      high = mid - 1;
      } 
    }
  }
  return -1;
}
```
#### 3.3二分查找-查找最后一个值等于给定值的元素
```
public int bsearch(int[] a, int n, int value) {
  int low = 0;
  int high = n - 1;
  while (low <= high) {
    int mid =  low + ((high - low)/2);
    if (a[mid] > value) {
      high = mid - 1;
    } else if (a[mid] < value) {
      low = mid + 1;
    } else {
      if ((mid == n - 1) || (a[mid + 1] != value)) return mid;
      else low = mid + 1;
    }
  }
  return -1;
}
```
#### 3.4二分查找-查找第一个大于等于给定值的元素
```
public int bsearch(int[] a, int n, int value) {
  int low = 0;
  int high = n - 1;
  while (low <= high) {
    int mid =  low + ((high - low)/2);
    if (a[mid] >= value) {
      if ((mid == 0) || (a[mid - 1] < value)) return mid;
      else high = mid - 1;
    } else {
      low = mid + 1;
    }
  }
  return -1;
}
```
#### 3.5查找最后一个小于等于给定值的元素
```
public int bsearch7(int[] a, int n, int value) {
  int low = 0;
  int high = n - 1;
  while (low <= high) {
    int mid =  low + ((high - low) >> 1);
    if (a[mid] > value) {
      high = mid - 1;
    } else {
      if ((mid == n - 1) || (a[mid + 1] > value)) return mid;
      else low = mid + 1;
    }
  }
  return -1;
}
```
