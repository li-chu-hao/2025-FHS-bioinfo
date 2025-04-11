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
即可获得序列。

**获取序列：根据物种名**

进入uniprot网站：[https://www.uniprot.org](https://www.uniprot.org)

搜索框输入“COX1”。

![image](https://github.com/user-attachments/assets/885d81d3-7743-47a5-a282-2e41f830da60)
<br>

点击左边的“Filter by taxonomy”，输入感兴趣的物种名。如果是常见物种，可以直接输入俗名。否则应该输入物种的拉丁名。输入后，点击右下角的“search”

![image](https://github.com/user-attachments/assets/35ce6059-18e5-462a-9d7e-56f771d0501c)
<br>
![image](https://github.com/user-attachments/assets/21ad60f5-a062-41c5-bdf1-679a21f43e5e)
<br>

从搜索结果页面找到目标蛋白，点进去，找到“Download”按钮并点击。

![image](https://github.com/user-attachments/assets/d4b1c4e6-2e8a-4584-bee5-aeee940e1e2a)
<br>
![image](https://github.com/user-attachments/assets/7eec682f-3e9a-499e-a5e4-e42bbb39838e)
<br>

“Format”处选择“FASTA(canonical)”，点击“Download”。
![image](https://github.com/user-attachments/assets/f44c7766-8143-4680-96b4-0e68d6acf925)
<br>
![image](https://github.com/user-attachments/assets/04008849-d211-45d7-92b1-53491f16a8cb)

把序列存放到一个文本文件中。

## 利用在线工具构建系统发育树

打开网站：[https://ngphylogeny.fr](https://ngphylogeny.fr)

点击“One Click”
![image](https://github.com/user-attachments/assets/5e5f7e50-80a4-41ff-94b4-54ed7b27a3c8)
<br>

在“Pasted text”中粘贴刚刚获取的目标序列，然后点击“Submit”
![image](https://github.com/user-attachments/assets/cdbe998b-2603-4931-ae15-b8c2d74d61a1)
<br>

等待结果。当第12步“Output Tree”完成后，即可点击右方的“iTol”，查看系统发育树。
![image](https://github.com/user-attachments/assets/f5a0485f-5d4d-4b09-a184-c041a4c62737)
<br>

根据外类群定根：在打开的页面中，找到外类群前面的分支，鼠标左键点击，选择 Tree structure -> Re-root the tree here。
![image](https://github.com/user-attachments/assets/1677db46-46d1-4a68-bc70-e694ec936438)
<br>

最终结果：
![image](https://github.com/user-attachments/assets/23a96c93-ca2d-4960-b714-e3c965442029)

## 和参考系统发育树比较

1. 把构建系统发育树中用到的物种拉丁名粘贴到一个文本文件，每行一个物种。然后保存。
2. 打开网站[https://timetree.org](https://timetree.org)
3. 拉到页面最下方，点击“选择文件”，然后点击“Upload”。
4. 比较该参考系统发育树和你构建的系统发育树之间的差异。

![image](https://github.com/user-attachments/assets/d9941006-f7ea-4153-8c55-85582a63fc69)


