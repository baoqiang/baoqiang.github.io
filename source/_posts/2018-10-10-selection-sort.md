---
layout: post
title:  "Algorithms selection sort"
date:   2018-10-10 14:22:00 +0800
categories: Algorithms
tags: Algorithms
---

* 目录
{:toc}

## 选择排序

首先找到数组中最小的元素，将它和第一个元素交换位置（如果第一个元素就是最小的元素那么就它和自己交换位置）。再次，在剩下的元素中找到最小元素，将它与数组第二个位置交换位置。如此往复，直到将整个数组排序。因为它在不断的选择剩余元素中的最小者。


```java
public class Selection {
    public static void main(String[] args) {
        int[] arr = {3, 20, 19, 7, 5, 9, 8, 10, 20};
        System.out.print("before: ");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            int min = i;
            for (int j = i+1; j < n; j++) {
                if (arr[j] < arr[min]) {
                    min = j;
                }
            }
            
            if(i != min) {
                int temp = arr[i];
                arr[i] = arr[min];
                arr[min] = temp;
            }
        }
        System.out.println("");
        System.out.print("after:  ");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

>  对于长度为 `N` 的数组，选择排序大约需要 `N^2/2` 次比较和 `N` 次交换。

特点：
1. **运行时间与输入无关**。为了找出最小元素而扫描一遍数组并不能为下一遍扫描提供什么信息。这种性质在某些情况下是缺点，使用选择排序的人会发现，一个已经有序的数组或是主键全部相等的的数组和一个元素随机排列的的数组所用的排序时间相同。
2. **数据移动最少**。每次交换都会改变两个数组元素的值，因此选择排序用了 N 次交换。交换次数和数组大小是线性关系。
