---
title: 十四种常见的算法
excerpt:  滑动窗口、双指针、快慢指针、区间合并、循环排序、原地反转链表、树上的BFS、树上的DFS、双堆、子集、变种二分、最大前K个元素、K-路归并、拓扑排序。
categories:
- 算法
tags:
- 算法
- 树
- dfs
- bfs
---

## 滑动窗口
滑动窗口类型的题目经常是用来执行数组或是链表上某个区间（窗口）上的操作。比如找最长的全为1的子数组长度。滑动窗口一般从第一个元素开始，一直往右边一个一个元素挪动。当然了，根据题目要求，我们可能有固定窗口大小的情况，也有窗口的大小变化的情况。

下面是一些我们用来判断我们可能需要上滑动窗口策略的方法：
- 这个问题的输入是一些线性结构：比如链表呀，数组啊，字符串啊之类的
- 让你去求最长/最短子字符串或是某些特定的长度要求

常见的问题有：
- 窗口大小为K的最大子数组和（简单）
- 拥有K个不同的字母的最长子串（中等）
- 字符串的同字母异序词（困难）

## 双指针模式
双指针是这样的模式：两个指针朝着左右方向移动（双指针分为同向双指针和异向双指针），直到他们有一个或是两个都满足某种条件。双指针通常用在排好序的数组或是链表中寻找对子。比如，你需要去比较数组中每个元素和其他元素的关系时，你就需要用到双指针了。

我们需要双指针的原因是：如果你只用一个指针的话，你得来回跑才能在数组中找到你需要的答案。这一个指针来来回回的过程就很耗时和浪费空间了 — 这是考虑算法的复杂度分析的时候的重要概念。虽然brute force一个指针的解法可能会奏效，但时间复杂度一般会是O(n²)。在很多情况下，双指针能帮助我们找到空间或是时间复杂度更低的解。

识别使用双指针的招数：
- 一般来说，数组或是链表是排好序的，你得在里头找一些组合满足某种限制条件
- 这种组合可能是一对数，三个数，或是一个子数组

可以放双指针大招的题目：
- 输出一个排好序的数组的平方数组（简单）
- 3-Sum（中等）
- 比较两个字符是否相等，字符中包括得有退格键（中等）

## 快慢指针
这种模式，有一个非常出门的名字，叫龟兔赛跑。解释一下快慢指针：这种算法的两个指针的在数组上（或是链表上，序列上）的移动速度不一样。还别说，这种方法在解决有环的链表和数组时特别有用。

通过控制指针不同的移动速度（比如在环形链表上），这种算法证明了他们肯定会相遇的。快的一个指针肯定会追上慢的一个（可以想象成跑道上面跑得快的人套圈跑得慢的人）。

需要用快慢指针模式的时候：
- 问题需要处理环上的问题，比如环形链表和环形数组
- 当你需要知道链表的长度或是某个特别位置的信息的时候

什么时候用快慢指针而不是上面的双指针呢？
有些情形下，咱们不应该用双指针，比如我们在单链表上不能往回移动的时候。一个典型的需要用到快慢指针的模式的是当你需要去判断一个链表是否是回文的时候。

快慢指针可秒的题目：
- 链表是否有环（简单）
- 链表是否满足回文（中等）
- 环状数组中检测环（困难）

## 区间合并
区间合并模式是一个用来处理有区间重叠的很高效的技术。在设计到区间的很多问题中，通常咱们需要要么判断是否有重叠，要么合并区间，如果他们重叠的话。

怎么识别什么时候用合并区间模式？
- 当你需要产生一堆相互之间没有交集的区间的时候
- 当你听到重叠区间的时候

合并区间的题目：
- 区间交集（中等）
- 最大化CPU负载（困难）

## 循环排序
这种模式讲述的是一直很好玩的方法：可以用来处理数组中的数值限定在一定的区间的问题。这种模式一个个遍历数组中的元素，如果当前这个数它不在其应该在的位置的话，咱们就把它和它应该在的那个位置上的数交换一下。你可以尝试将该数放到其正确的位置上，但这复杂度就会是O(n^2)。这样的话，可能就不是最优解了。因此循环排序的优势就体现出来了。

如何鉴别这种模式：
- 这些问题一般设计到排序好的数组，而且数值一般满足于一定的区间
- 如果问题让你需要在排好序/翻转过的数组中，寻找丢失的/重复的/最小的元素

能用循环排序解的题：
- 需要数组中没出现的数字 （简单）
- 寻找最小的没出现的正整数 （中等）

## 原地链表翻转
在众多问题中，题目可能需要你去翻转链表中某一段的节点。通常，要求都是你得原地翻转，就是重复使用这些已经建好的节点，而不使用额外的空间。这个时候，原地翻转模式就要发挥威力了。

这种模式每次就翻转一个节点。一般需要用到多个变量，一个变量指向头结点，另外一个（previous）则指向咱们刚刚处理完的那个节点。在这种固定步长的方式下，你需要先将当前节点（current）指向前一个节点（previous），再移动到下一个。同时，你需要将previous总是更新到你刚刚新鲜处理完的节点，以保证正确性。

如何鉴别这种模式：
- 如果你被问到需要去翻转链表，要求不能使用额外空间的时候

这种模式的适用场景：
- 翻转链表中的一段（中等）
- 翻转每k个元素为一组的子链表段（中等）

## 树上的BFS
这种模式基于宽搜（Breadth First Search (BFS)），适用于需要遍历一颗树。借助于队列数据结构，从而能保证树的节点按照他们的层数打印出来。打印完当前层所有元素，才能执行到下一层。所有这种需要遍历树且需要一层一层遍历的问题，都能用这种模式高效解决。

这种树上的BFS模式是通过把根节点加到队列中，然后不断遍历直到队列为空。每一次循环中，我们都会把队头结点拿出来（remove），然后对其进行必要的操作。在删除每个节点的同时，其孩子节点，都会被加到队列中。

识别树上的BFS模式：
- 如果你被问到去遍历树，需要按层操作的方式（也称作层序遍历）

该模式可解的题：
- 二叉树层序遍历（简单）
- 之字形遍历（中等）

## 树上的DFS
树形DFS基于深搜（Depth First Search (DFS)）技术来实现树的遍历。

咱们可以用递归（或是显示栈，如果你想用迭代方式的话）来记录遍历过程中访问过的父节点。

该模式的运行方式是从根节点开始，如果该节点不是叶子节点，我们需要干三件事：
1. 需要区别我们是先处理根节点（pre-order，前序），处理孩子节点之间处理根节点（in-order，中序），还是处理完所有孩子再处理根节点（post-order，后序）。
2. 递归处理当前节点的左右孩子。

识别树形DFS：
- 你需要按前中后序的DFS方式遍历树
- 如果该问题的解一般离叶子节点比较近。

树形DFS可破的题目：
- 树上所有路径上表示的数字的和（中等）
- 树中所有能形成目标和的路径（中等）

##  双堆模式
很多问题中，我们被告知，我们拿到一大把可以分成两队的数字。为了解决这个问题，我们感兴趣的是，怎么把数字分成两半？使得：小的数字都放在一起，大的放在另外一半。双堆模式就能高效解决此类问题。

正如名字所示，该模式用到了两个堆，是不是很难猜？一个最小堆用来找最小元素；一个最大堆，拿到最大元素。这种模式将一半的元素放在最大堆中，这样你可以从这一堆中秒找到最大元素。同理，把剩下一半丢到最小堆中，O(1)时间找到他们中的最小元素。通过这样的方式，这一大堆元素的中位数就可以从两个堆的堆顶拿到数字，从而计算出来。

判断双堆模式的秘诀：
- 这种模式在优先队列，计划安排问题（Scheduling）中有奇效
- 如果问题让你找一组数中的最大/最小/中位数
- 有时候，这种模式在涉及到二叉树数据结构时也特别有用

典型问题：
- 找数字流中的中位数（中等）

## 子集问题模式
超级多的编程面试问题都会涉及到排列和组合问题。子集问题模式讲的是用BFS来处理这些问题。

这个模式是这样的：

给一组数字 [1, 5, 3]
1. 我们从空集开始：[[]]
2. 把第一个数（1），加到之前已经存在的集合中：[[], [1]];
3. 把第二个数（5），加到之前的集合中得到：[[], [1], [5], [1,5]];
4. 再加第三个数（3），则有：[[], [1], [5], [1,5], [3], [1,3], [5,3], [1,5,3]].

如果判断这种子集模式：
- 问题需要咱们去找数字的组合或是排列

子集模式适用的场景：
- 有重复元素的所有子集（简单）
- 通过改变大小写，找到所有可能的字符串排列（中等）

## 二分变种
当你需要解决的问题的输入是排好序的数组，链表，或是排好序的矩阵，要求咱们寻找某些特定元素。这个时候的不二选择就是二分搜索。这种模式是一种超级牛的用二分来解决问题的方式。

对于一组满足上升排列的数集来说，这种模式的步骤是这样的：
1. 首先，算出左右端点的中点。最简单的方式是这样的：middle = (start + end) / 2。但这种计算方式有不小的概率会出现整数越界。因此一般都推荐另外这种写法：middle = start + (end — start) / 2
2. 如果要找的目标改好和中点所在的数值相等，我们返回中点的下标就行
3. 如果目标不等的话：我们就有两种移动方式了
4. 如果目标比中点在的值小（key < arr[middle]）：将下一步搜索空间放到左边（end = middle - 1）
5. 如果比中点的值大，则继续在右边搜索，丢弃左边：left = middle + 1

变种二分可以解决的问题：
- 顺序未知的二分（可能翻转过了，简单）
- 无界排序数组的二分（中等）

## 前K大的数模式
任何让我们求解最大/最小/最频繁的K个元素的题，都遵循这种模式。

用来记录这种前K类型的最佳数据结构就是堆了（译者注：在Java中，改了个名，叫优先队列（PriorityQueue））。这种模式借助堆来解决很多这种前K个数值的问题。

这个模式是这样的：
1. 根据题目要求，将K个元素插入到最小堆或是最大堆。
2. 遍历剩下的还没访问的元素，如果当前出来到的这个元素比堆顶元素大，那咱们把堆顶元素先删除，再加当前元素进去。

注意这种模式下，咱们不需要去排序数组，因为堆具有这种良好的局部有序性，这对咱们需要解决问题就够了。

识别最大K个元素模式：
- 如果你需要求最大/最小/最频繁的前K个元素
- 如果你需要通过排序去找一个特定的数

前K个元素模式的场景：
- 前K大的数（简单）
- 前K个最常出现的数字（中等）

## K路归并
K路归并能帮咱们解决那些涉及到多组排好序的数组的问题。

每当你的输入是K个排好序的数组，你就可以用堆来高效顺序遍历其中所有数组的所有元素。你可以将每个数组中最小的一个元素加入到最小堆中，从而得到全局最小值。当我们拿到这个全局最小值之后，再从该元素所在的数组里取出其后面紧挨着的元素，加入堆。如此往复直到处理完所有的元素。

该模式是这样的运行的：
1. 把每个数组中的第一个元素都加入最小堆中
2. 取出堆顶元素（全局最小），将该元素放入排好序的结果集合里面
3. 将刚取出的元素所在的数组里面的下一个元素加入堆
4. 重复步骤2，3，直到处理完所有数字

识别K路归并：
- 该问题的输入是排好序的数组，链表或是矩阵
- 如果问题让咱们合并多个排好序的集合，或是需要找这些集合中最小的元素

K路归并的题目：
- 合并K个排好序的链表（中等）
- K对数和最大（困难）

## 拓扑排序模式
拓扑排序模式用来寻找一种线性的顺序，这些元素之间具有依懒性。比如，如果事件B依赖于事件A，那A在拓扑排序顺序中排在B的前面。

这种模式定义了一种简单方式来理解拓扑排序这种技术。

这种模式是这样奏效的：

1. 初始化
- 借助于HashMap将图保存成邻接表形式。
- 找到所有的起点，用HashMap来帮助记录每个节点的入度
2. 创建图，找到每个节点的入度
- 利用输入，把图建好，然后遍历一下图，将入度信息记录在HashMap中
3. 找所有的起点
- 所有入度为0的节点，都是有效的起点，而且我们讲他们都加入到一个队列中
4. 排序
- 对每个起点，执行以下步骤
把它加到结果的顺序中
将其在图中的孩子节点取到
将其孩子的入度减少1
如果孩子的入度变为0，则改孩子节点成为起点，将其加入队列中b) 重复 （b）过程，直到起点队列为空。

拓扑排序模式识别：
- 待解决的问题需要处理无环图
- 你需要以一种有序的秩序更新输入元素
- 需要处理的输入遵循某种特定的顺序

拓扑排序的试炼场：
- 任务执行顺序安排（中等）
- 树的最小高度（困难）

## 参考链接
[码农找工作之：秒杀算法面试必须掌握的14种模式](https://zhuanlan.zhihu.com/p/247579215)