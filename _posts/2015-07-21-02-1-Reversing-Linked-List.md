---
layout: post
title: "PAT 02-1 Reversing Linked List (25) 单链表逆序"
date: 2015-07-21
comments: true
categories: 学习
tag:
  - Python
  - Data Structure
  - PAT
---
## [02-1. Reversing Linked List (25)][3]

时间限制  400 ms  内存限制   65536 kB   代码长度限制  8000 B  判题程序  Standard  作者CHEN, Yue

Given a constant K and a singly linked list L, you are supposed to reverse the links of every K elements on L. For example, given L being 1→2→3→4→5→6, if K = 3, then you must output 3→2→1→6→5→4; if K = 4, you must output 4→3→2→1→5→6.

### Input Specification:

Each input file contains one test case. For each case, the first line contains the address of the first node, a positive N (<= 105) which is the total number of nodes, and a positive K (<=N) which is the length of the sublist to be reversed. The address of a node is a 5-digit nonnegative integer, and NULL is represented by -1.

Then N lines follow, each describes a node in the format:

Address Data Next

where Address is the position of the node, Data is an integer, and Next is the position of the next node.

### Output Specification:

For each case, output the resulting ordered linked list. Each node occupies a line, and is printed in the same format as in the input.

### Sample Input:

~~~
00100 6 4
00000 4 99999
00100 1 12309
68237 6 -1
33218 3 00000
99999 5 68237
12309 2 33218

### Sample Output:

~~~
00000 4 33218
33218 3 12309
12309 2 00100
00100 1 99999
99999 5 68237
68237 6 -1
~~~

---

刚学Python，折腾了好久，输入输出是我自己写的，但是核心的逆转算法其实是抄的[ice_camel 同学][1]，
判定结果只有21分，测试点0-4结果正确，测试点5和6没有得分。根据[kevin-ye 的这篇解题报告][2]应该是我没有考虑异常情况，没耐心了，不想改了，代码如下：

~~~ python
class LNode:
	'''
	定义了Node，实际上我是用了一个元素为100000个的线性表，每个元素里存两个值：data, next
	address 就直接用在元素在表中的位置上了，即List[address]
	'''
	def __init__(self, data):
		self.data = data
		self.next = None

def reverse_K(head, N, K):
	'''
	逆转函数
	两层循环
	:param head: 表头
	:param N: 表的长度N
	:param K: 逆转的单位长度K
	:return: 返回逆转后的表头 head，即原来表的第 K 个元素
	'''
	cur = head	# cur 指向当前节点
	pre = -1	# per 指向当前节点的前一个节点
	curSubHead = -1	# curSubHead 记录当前子链表的表头
	for y in range(int(N/K)):	# 外面的大循环：
		preSubHead = curSubHead # preSubHead 记录前一个子链表的表头
		curSubHead = cur # curSubHead 记录当前子链表的表头
		for x in range(K):		# 内循环：将K个节点的子链表逆转（将next的值改为前一个节点的位置）
			temp = List[cur].next # temp 指向当前节点的下一个节点
			List[cur].next = pre
			pre = cur
			cur = temp
		if y == 0:
			head = pre # 将原链表表的第K个元素记为新表头
		else:
			List[preSubHead].next = pre # 将前一个子链表的尾巴（原表头）接到新逆转完成的子链表的表头（pre）
		List[curSubHead].next = cur # 如果N%K!=0，把尾巴接上
	return head

def printlist(head):
	'''
	打印链表
	要求地址是五位数，但是-1不能是-0001
	'''
	cur = head
	while List[cur].next != -1:
		print('%05d %d %05d'% (cur, List[cur].data, List[cur].next))
		cur = List[cur].next
	print('%05d %d -1'% (cur, List[cur].data))


List =[LNode(0) for i in range(100000)]

s1 = input().split(' ') # 读head, N, K
head = int(s1[0])
N = int(s1[1])
K = int(s1[2])

for i in range(N): # 读表，并按地址放入数组。s2[0]: address, s2[1]: data, s2[2]: next
	s2 = [int(i) for i in input().split(' ')] # input()读进来的是字符串，得用空格分开，然后转成整数
	List[s2[0]].data = s2[1]
	List[s2[0]].next = s2[2]

printlist(reverse_K(head, N, K))
~~~

[1]: http://blog.csdn.net/ice_camel/article/details/45156245
[2]: http://www.cnblogs.com/kevin-lwb/p/4283456.html
[3]: http://www.patest.cn/contests/mooc-ds/02-%E7%BA%BF%E6%80%A7%E7%BB%93%E6%9E%841