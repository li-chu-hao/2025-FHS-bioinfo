# 2025-FHS-bioinfo
Small phylogenetic tree contruction

目标：构建感兴趣的物种的系统发育树。

## 确定物种

五种哺乳类动物 + 一种非哺乳类（外类群）。加入外类群，可以确定系统发育树的根。

哺乳类动物：

- 人（human）：Homo sapiens（COX1 Entry: P00395）
- 猫（cat）：Felis catus（COX1 Entry: P48888）
- 狗（dog）：Canis lupus（COX1 Entry: Q9ZZ64）
- 鼠（mouse）：Mus musculus（COX1 Entry: P00397）
- 猪（pig）：Sus scrofa（COX1 Entry: O79876）

外类群：

- 鸡（chicken）：Gallus gallus（COX1 Entry: P18943）

可以根据的喜好增减物种。请保证最少有4个物种。

## 获取每个物种的COX1蛋白序列

**序列选择**。需要在目标物种间保守的序列。COX1是细胞色素c氧化酶亚基1，是一个线粒体基因，脊椎动物都有这个基因，因此可以用于推断脊椎动物之间的系统发育关系。

**获取序列：根据uniprot Entry**

如果知道蛋白对应的uniprot Entry，可以直接在浏览器地址栏输入：

`https://rest.uniprot.org/uniprotkb/[COX1 Entry].fasta`

**获取序列：根据物种名**

1. 进入uniprot网站：[https://www.uniprot.org]([https://www.uniprot.org])

2. 在搜索框输入“COX1”。

3. 点击左边的“Filter by taxonomy”，输入感兴趣的物种名。如果是常见物种，可以直接输入俗名。否则应该输入物种的拉丁名。输入后，点击右下角的“search”

4. 从搜索结果页面找到目标蛋白，点进去，找到“Download”按钮并点击。

5. “Format”处选择“FASTA(canonical)”，点击“Download”。

6. 把序列存放到一个文本文件中。

## 利用在线工具构建系统发育树

1. 进入

## 和参考系统发育树比较
