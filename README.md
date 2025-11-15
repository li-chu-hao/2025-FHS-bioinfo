# 2025-FHS-bioinfo

目标：构建6个默认物种 + 1个感兴趣的哺乳类动物的系统发育树。

## 1. 下载所需文件。

<img width="1200" height="498" alt="image" src="https://github.com/user-attachments/assets/1200590f-e52a-4575-9195-1cc8fbd2f310" />

下载好之后，解压备用。后面主要用到以下文件：

- protein_sequence.txt，用于保存各个物种的COX1蛋白序列。
- selected_species.txt，用于保存各个物种的物种拉丁名。
- all_sequenced_species.txt，已经全基因组测序了的哺乳动物列表。

## 2. 选择物种

已经为大家选定了五种哺乳类动物 + 一种非哺乳类（外类群）：

- 人（human）：Homo sapiens
- 猫（cat）：Felis catus
- 狗（dog）：Canis lupus
- 鼠（mouse）：Mus musculus
- 猪（pig）：Sus scrofa
- 鸡（chicken）（外类群）：Gallus gallus

大家需要自己从`all_sequenced_species.txt`中选择一个物种。

## 2. 获取物种的COX1蛋白序列

**基因选择**。需要在目标物种间保守的序列。COX1是细胞色素c氧化酶亚基1，是一个线粒体基因，脊椎动物都有这个基因，因此可以用于推断脊椎动物之间的系统发育关系。因为氨基酸序列比核苷酸序列更保守，因此在进行亲缘关系较远的物种之间的系统发育研究时，一般使用氨基酸序列。

为了节省时间，我们已经为大家准备好默认物种的COX1蛋白序列，存放在了`protein_sequence.txt`文件中。

但是，对于自选物种，需要你自己去数据库中获取，操作步骤如下。

**获取特定物种的COX1序列**

**Step1:** 进入uniprot网站: `https://www.uniprot.org`

**Step2:** 搜索框输入“COX1”。
![image](https://github.com/user-attachments/assets/885d81d3-7743-47a5-a282-2e41f830da60)
  
**Step3:** 点击左边的“Filter by taxonomy”。
![image](https://github.com/user-attachments/assets/35ce6059-18e5-462a-9d7e-56f771d0501c)
  
**Step4:** 输入感兴趣的物种名。如果是常见物种，可以直接输入俗名。否则应该输入物种的拉丁名。输入后，点击右下角的“search”
![image](https://github.com/user-attachments/assets/21ad60f5-a062-41c5-bdf1-679a21f43e5e)
  
**Step5:** 从搜索结果页面找到目标蛋白，点进去。
![image](https://github.com/user-attachments/assets/d4b1c4e6-2e8a-4584-bee5-aeee940e1e2a)

**Step6:** 找到“Download”按钮并点击。
![image](https://github.com/user-attachments/assets/7eec682f-3e9a-499e-a5e4-e42bbb39838e)
  
**Step7:** “Format”处选择“FASTA(canonical)”，点击“Download”。
![image](https://github.com/user-attachments/assets/f44c7766-8143-4680-96b4-0e68d6acf925)
  
得到的目标序列如图所示
![image](https://github.com/user-attachments/assets/04008849-d211-45d7-92b1-53491f16a8cb)

**Step8:** 把得到的序列（包含以“>”为开头的第一行）复制到`protein_sequence.txt`最下方。

## 利用在线工具构建系统发育树

构建系统发育树，包括多序列比对、系统发育树推断、系统发育树可视化三个步骤。ngphylogeny.fr这个网站可以提供“一键式”的服务，只需要输入目标物种的蛋白序列，即可得到最终的系统发育树。

**Step1:** 打开网站：`https://ngphylogeny.fr`

**Step2:** 点击“One Click”
![image](https://github.com/user-attachments/assets/5e5f7e50-80a4-41ff-94b4-54ed7b27a3c8)
  
**Step3:** 在“Pasted text”中粘贴刚刚获取的目标序列，然后点击“Submit”
![image](https://github.com/user-attachments/assets/cdbe998b-2603-4931-ae15-b8c2d74d61a1)
  
**Step4:** 等待结果。当第12步“Output Tree”完成后，即可点击右方的“iTol”，查看系统发育树。
![image](https://github.com/user-attachments/assets/f5a0485f-5d4d-4b09-a184-c041a4c62737)
  
**Step5:** 根据外类群定根：在打开的页面中，找到外类群前面的分支，鼠标左键点击，选择 Tree structure -> Re-root the tree here。
![image](https://github.com/user-attachments/assets/1677db46-46d1-4a68-bc70-e694ec936438)
  
最终结果：
![image](https://github.com/user-attachments/assets/23a96c93-ca2d-4960-b714-e3c965442029)

## 和参考系统发育树比较

**Step1:** 把你选择的物种的拉丁名粘贴到`selected_species.txt`下方。确保每行一个物种。然后保存。

**Step2:** 打开网站`https://timetree.org`

**Step3:** 拉到页面最下方，点击“选择文件”，然后点击“Upload”。
![image](https://github.com/user-attachments/assets/c5d4c700-abfd-4e9e-b3db-3758a42cafdc)
  
**Step4:** 比较该参考系统发育树和你构建的系统发育树之间的差异。
![image](https://github.com/user-attachments/assets/d9941006-f7ea-4153-8c55-85582a63fc69)
