# Top-K 问题

!!! question

    给定一个长度为 $n$ 无序数组 `nums` ，请返回数组中前 $k$ 大的元素。

对于该问题，我们先介绍两种思路比较直接的解法，再介绍效率更高的堆解法。

## 方法一：遍历选择

我们可以进行下图所示的 $k$ 轮遍历，分别在每轮中提取第 $1$、$2$、$\dots$、$k$ 大的元素，时间复杂度为 $O(nk)$ 。

此方法只适用于 $k \ll n$ 的情况，因为当 $k$ 与 $n$ 比较接近时，其时间复杂度趋向于 $O(n^2)$ ，非常耗时。

![遍历寻找最大的 k 个元素](top_k.assets/top_k_traversal.png)

!!! tip

    当 $k = n$ 时，我们可以得到完整的有序序列，此时等价于“选择排序”算法。

## 方法二：排序

如下图所示，我们可以先对数组 `nums` 进行排序，再返回最右边的 $k$ 个元素，时间复杂度为 $O(n \log n)$ 。

显然，该方法“超额”完成任务了，因为我们只需要找出最大的 $k$ 个元素即可，而不需要排序其他元素。

![排序寻找最大的 k 个元素](top_k.assets/top_k_sorting.png)

## 方法三：堆

我们可以基于堆更加高效地解决 Top-K 问题，流程如下图所示。

1. 初始化一个小顶堆，其堆顶元素最小。
2. 先将数组的前 $k$ 个元素依次入堆。
3. 从第 $k + 1$ 个元素开始，若当前元素大于堆顶元素，则将堆顶元素出堆，并将当前元素入堆。
4. 遍历完成后，堆中保存的就是最大的 $k$ 个元素。

=== "<1>"
    ![基于堆寻找最大的 k 个元素](top_k.assets/top_k_heap_step1.png)

=== "<2>"
    ![top_k_heap_step2](top_k.assets/top_k_heap_step2.png)

=== "<3>"
    ![top_k_heap_step3](top_k.assets/top_k_heap_step3.png)

=== "<4>"
    ![top_k_heap_step4](top_k.assets/top_k_heap_step4.png)

=== "<5>"
    ![top_k_heap_step5](top_k.assets/top_k_heap_step5.png)

=== "<6>"
    ![top_k_heap_step6](top_k.assets/top_k_heap_step6.png)

=== "<7>"
    ![top_k_heap_step7](top_k.assets/top_k_heap_step7.png)

=== "<8>"
    ![top_k_heap_step8](top_k.assets/top_k_heap_step8.png)

=== "<9>"
    ![top_k_heap_step9](top_k.assets/top_k_heap_step9.png)

总共执行了 $n$ 轮入堆和出堆，堆的最大长度为 $k$ ，因此时间复杂度为 $O(n \log k)$ 。该方法的效率很高，当 $k$ 较小时，时间复杂度趋向 $O(n)$ ；当 $k$ 较大时，时间复杂度不会超过 $O(n \log n)$ 。

另外，该方法适用于动态数据流的使用场景。在不断加入数据时，我们可以持续维护堆内的元素，从而实现最大 $k$ 个元素的动态更新。

=== "Java"

    ```java title="top_k.java"
    [class]{top_k}-[func]{topKHeap}
    ```

=== "C++"

    ```cpp title="top_k.cpp"
    [class]{}-[func]{topKHeap}
    ```

=== "Python"

    ```python title="top_k.py"
    [class]{}-[func]{top_k_heap}
    ```

=== "Go"

    ```go title="top_k.go"
    [class]{}-[func]{topKHeap}
    ```

=== "JS"

    ```javascript title="top_k.js"
    [class]{}-[func]{topKHeap}
    ```

=== "TS"

    ```typescript title="top_k.ts"
    [class]{}-[func]{topKHeap}
    ```

=== "C"

    ```c title="top_k.c"
    [class]{}-[func]{topKHeap}
    ```

=== "C#"

    ```csharp title="top_k.cs"
    [class]{top_k}-[func]{topKHeap}
    ```

=== "Swift"

    ```swift title="top_k.swift"
    [class]{}-[func]{topKHeap}
    ```

=== "Zig"

    ```zig title="top_k.zig"
    [class]{}-[func]{topKHeap}
    ```

=== "Dart"

    ```dart title="top_k.dart"
    [class]{}-[func]{topKHeap}
    ```

=== "Rust"

    ```rust title="top_k.rs"
    [class]{}-[func]{top_k_heap}
    ```
