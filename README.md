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

可以根据的喜好增减物种。不一定每个物种在数据库中都有对应的COX1序列，已经被测序的物种，更大概率能找到对应的COX1序列。
为了方便，我们已经整理好已经被测序的哺乳类动物列表供大家选择：（可以参考本文档最后的[已测序哺乳动物列表](#438个已被全基因测序的哺乳动物列表)）。

注意，请保证最少有4个物种用于构建系统发育树。

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
  
点击左边的“Filter by taxonomy”。
![image](https://github.com/user-attachments/assets/35ce6059-18e5-462a-9d7e-56f771d0501c)
  
输入感兴趣的物种名。如果是常见物种，可以直接输入俗名。否则应该输入物种的拉丁名。输入后，点击右下角的“search”
![image](https://github.com/user-attachments/assets/21ad60f5-a062-41c5-bdf1-679a21f43e5e)
  
从搜索结果页面找到目标蛋白，点进去。
![image](https://github.com/user-attachments/assets/d4b1c4e6-2e8a-4584-bee5-aeee940e1e2a)

找到“Download”按钮并点击。
![image](https://github.com/user-attachments/assets/7eec682f-3e9a-499e-a5e4-e42bbb39838e)
  
“Format”处选择“FASTA(canonical)”，点击“Download”。
![image](https://github.com/user-attachments/assets/f44c7766-8143-4680-96b4-0e68d6acf925)
  
得到目标序列，
![image](https://github.com/user-attachments/assets/04008849-d211-45d7-92b1-53491f16a8cb)

把得到的序列全部存放到同一个文本文件中。

```
>human__Homo_sapiens
MFADRWLFSTNHKDIGTLYLLFGAWAGVLGTALSLLIRAELGQPGNLLGNDHIYNVIVTAHAFVMIFFMV
MPIMIGGFGNWLVPLMIGAPDMAFPRMNNMSFWLLPPSLLLLLASAMVEAGAGTGWTVYPPLAGNYSHPG
ASVDLTIFSLHLAGVSSILGAINFITTIINMKPPAMTQYQTPLFVWSVLITAVLLLLSLPVLAAGITMLL
TDRNLNTTFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGMISHIVTYYSGKKEPFGYMGMVWAMMSI
GFLGFIVWAHHMFTVGMDVDTRAYFTSATMIIAIPTGVKVFSWLATLHGSNMKWSAAVLWALGFIFLFTV
GGLTGIVLANSSLDIVLHDTYYVVAHFHYVLSMGAVFAIMGGFIHWFPLFSGYTLDQTYAKIHFTIMFIG
VNLTFFPQHFLGLSGMPRRYSDYPDAYTTWNILSSVGSFISLTAVMLMIFMIWEAFASKRKVLMVEEPSM
NLEWLYGCPPPYHTFEEPVYMKS
>cat__Felis_catus
MFMNRWLFSTNHKDIGTLYLLFGAWAGMVGTALSLLIRAELGQPGTLLGDDQIYNVIVTAHAFVMIFFMV
MPIMIGGFGNWLVPLMIGAPDMAFPRMNNMSFWLLPPSFLLLLASSMVEAGAGTGWTVYPPLAGNLAHAG
ASVDLTIFSLHLAGVSSILGAINFITTIINMKPPAMSQYQTPLFVWSVLITAVLLLLSLPVLAAGITMLL
TDRNLNTTFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGMISHIVTYYSGKKEPFGYMGMVWAMMSI
GFLGFIVWAHHMFTVGMDVDTRAYFTSATMIIAIPTGVKVFSWLATLHGGNIKWSPAMLWALGFIFLFTV
GGLTGIVLANSSLDIVLHDTYYVVAHFHYVLSMGAVFAIMGGFVHWFPLFSGYTLDNTWAKIHFTIMFVG
VNMTFFPQHFLGLSGMPRRYSDYPDAYTTWNTISSMGSFISLTAVMLMVFMVWEAFASKREVAMVELTTT
NLEWLHGCPPPYHTFEEPTYVLLK
>dog__Canis_lupus
MFINRWLFSTNHKDIGTLYLLFGAWAGMVGTALSLLIRAELGQPGTLLGDDQIYNVIVTAHAFVMIFFMV
MPIMIGGFGNWLVPLMIGAPDMAFPRMNNMSFWLLPPSFLLLLASSMVEAGAGTGWTVYPPLAGNLAHAG
ASVDLTIFSLHLAGVSSILGAINFITTIINMKPPAMSQYQTPLFVWSVLITAVLLLLSLPVLAAGITMLL
TDRNLNTTFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGMISHIVTYYSGKKEPFGYMGMVWAMMSI
GFLGFIVWAHHMFTVGMDVDTRAYFTSATMIIAIPTGVKVFSWLATLHGGNIKWSPAMLWALGFIFLFTV
GGLTGIVLANSSLDIVLHDTYYVVAHFHYVLSMGAVFAIMGGFAHWFPLFSGYTLNDTWAKIHFTIMFVG
VNMTFFPQHFLGLSGMPRRYSDYPDAYTTWNTVSSMGSFISLTAVMLMIFMIWEAFASKREVAMVELTTT
NIEWLHGCPPPYHTFEEPTYVIQK
>pig__Sus_scrofa
MFVNRWLYSTNHKDIGTLYLLFGAWAGMVGTALSLLIRAELGQPGTLLGDDQIYNVIVTAHAFVMIFFMV
MPIMIGGFGNWLVPLMIGAPDMAFPRMNNMSFWLLPPSFLLLLASSMVEAGAGTGWTVYPPLAGNLAHAG
ASVDLTIFSLHLAGVSSILGAINFITTIINMKPPAMSQYQTPLFVWSVLITAVLLLLSLPVLAAGITMLL
TDRNLNTTFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGMISHIVTYYSGKKEPFGYMGMVWAMMSI
GFLGFIVWAHHMFTVGMDVDTRAYFTSATMIIAIPTGVKVFSWLATLHGGNIKWSPAMLWALGFIFLFTV
GGLTGIVLANSSLDIVLHDTYYVVAHFHYVLSMGAVFAIMGGFVHWFPLFSGYTLNQAWAKIHFVIMFVG
VNMTFFPQHFLGLSGMPRRYSDYPDAYTAWNTISSMGSFISLTAVMLMIFIIWEAFASKREVSAVELTST
NLEWLHGCPPPYHTFEEPTYINLK
>mouse__Mus_musculus
MFINRWLFSTNHKDIGTLYLLFGAWAGMVGTALSILIRAELGQPGTLLGDDQIYNVIVTAHAFVMIFFMV
MPMMIGGFGNWLVPLMIGAPDMAFPRMNNMSFWLLPPSFLLLLASSMVEAGAGTGWTVYPPLAGNLAHAG
ASVDLTIFSLHLAGVSSILGAINFITTIINMKPPAMTQYQTPLFVWSVLITAVLLLLSLPVLAAGITMLL
TDRNLNTTFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGIISHVVTYYSGKKEPFGYMGMVWAMMSI
GFLGFIVWAHHMFTVGLDVDTRAYFTSATMIIAIPTGVKVFSWLATLHGGNIKWSPAMLWALGFIFLFTV
GGLTGIVLSNSSLDIVLHDTYYVVAHFHYVLSMGAVFAIMAGFVHWFPLFSGFTLDDTWAKAHFAIMFVG
VNMTFFPQHFLGLSGMPRRYSDYPDAYTTWNTVSSMGSFISLTAVLIMIFMIWEAFASKREVMSVSYAST
NLEWLHGCPPPYHTFEEPTYVKVK
>chicken__Gallus_gallus
MTFINRWLFSTNHKDIGTLYLIFGTWAGMAGTALSLLIRAELGQPGTLLGDDQIYNVIVTAHAFVMIFFM
VMPIMIGGFGNWLVPLMIGAPDMAFPRMNNMSFWLLPPSFLLLLASSTVEAGAGTGWTVYPPLAGNLAHA
GASVDLAIFSLHLAGVSSILGAINFITTIINMKPPALSQYQTPLFVWSVLITAILLLLSLPVLAAGITML
LTDRNLNTTFFDPAGGGDPILYQHLFWFFGHPEVYILILPGFGMISHVVAYYAGKKEPFGYMGMVWAMLS
IGFLGFIVWAHHMFTVGMDVDTRAYFTSATMIIAIPTGIKVFSWLATLHGGTIKWDPPMLWALGFIFLFT
IGGLTGIVLANSSLDIALHDTYYVVAHFHYVLSMGAVFAILAGFTHWFPLFTGFTLHPSWTKAHFGVMFT
GVNLTFFPQHFLGLAGMPRRYSDYPDAYTLWNTLSSIGSLISMTAVIMLMFIVWEAFSAKRKVLQPELTA
TNIEWIHGCPPPYHTFEEPAFVQVQE
```

## 利用在线工具构建系统发育树

打开网站：[https://ngphylogeny.fr](https://ngphylogeny.fr)

点击“One Click”
![image](https://github.com/user-attachments/assets/5e5f7e50-80a4-41ff-94b4-54ed7b27a3c8)
  
在“Pasted text”中粘贴刚刚获取的目标序列，然后点击“Submit”
![image](https://github.com/user-attachments/assets/cdbe998b-2603-4931-ae15-b8c2d74d61a1)
  
等待结果。当第12步“Output Tree”完成后，即可点击右方的“iTol”，查看系统发育树。
![image](https://github.com/user-attachments/assets/f5a0485f-5d4d-4b09-a184-c041a4c62737)
  
根据外类群定根：在打开的页面中，找到外类群前面的分支，鼠标左键点击，选择 Tree structure -> Re-root the tree here。
![image](https://github.com/user-attachments/assets/1677db46-46d1-4a68-bc70-e694ec936438)
  
最终结果：
![image](https://github.com/user-attachments/assets/23a96c93-ca2d-4960-b714-e3c965442029)

## 和参考系统发育树比较

把构建系统发育树中用到的物种拉丁名粘贴到一个文本文件，每行一个物种。然后保存。
```
Homo sapiens
Felis catus
Canis lupus
Sus scrofa
Mus musculus
Gallus gallus
```

打开网站[https://timetree.org](https://timetree.org)

拉到页面最下方，点击“选择文件”，然后点击“Upload”。
![image](https://github.com/user-attachments/assets/c5d4c700-abfd-4e9e-b3db-3758a42cafdc)
  
比较该参考系统发育树和你构建的系统发育树之间的差异。
![image](https://github.com/user-attachments/assets/d9941006-f7ea-4153-8c55-85582a63fc69)

## 438个已被全基因测序的哺乳动物列表

| 拉丁名                          | 中文名                     |
|----------------------------------|---------------------------|
| Acinonyx jubatus                | 猎豹                      |
| Acomys cahirinus                | 开罗棘鼠                  |
| Acomys russatus                 | 金棘鼠                    |
| Aeorestes cinereus              | 灰白蝙蝠                  |
| Aepyceros melampus              | 黑斑羚                    |
| Ailuropoda melanoleuca          | 大熊猫                    |
| Ailurus fulgens                 | 小熊猫                    |
| Alces alces                     | 驼鹿                      |
| Alouatta palliata               | 鬃毛吼猴                  |
| Ammotragus lervia               | 鬣羊                      |
| Anoura caudifer                 | 尾长舌蝠                  |
| Antechinus flavipes             | 黄足袋鼬                  |
| Antechinus stuartii             | 斯氏袋鼬                  |
| Antidorcas marsupialis          | 跳羚                      |
| Antilocapra americana           | 叉角羚                    |
| Antrozous pallidus              | 淡色蝠                    |
| Aotus nancymaae                 | 夜猴                      |
| Aplodontia rufa                 | 山河狸                    |
| Apodemus speciosus              | 大林姬鼠                  |
| Apodemus sylvaticus             | 林姬鼠                    |
| Arctocephalus gazella           | 南极毛皮海狮              |
| Artibeus jamaicensis            | 牙买加果蝠                |
| Arvicanthis niloticus           | 尼罗草鼠                  |
| Arvicola amphibius              | 水䶄                      |
| Ateles geoffroyi                | 黑掌蜘蛛猴                |
| Axis porcinus                   | 豚鹿                      |
| Balaenoptera acutorostrata      | 小须鲸                    |
| Balaenoptera bonaerensis        | 南极小须鲸                |
| Balaenoptera musculus           | 蓝鲸                      |
| Balaenoptera physalus           | 长须鲸                    |
| Beatragus hunteri               | 亨氏牛羚                  |
| Bison bison                     | 美洲野牛                  |
| Bos frontalis                   | 大额牛                    |
| Bos gaurus                      | 印度野牛                  |
| Bos grunniens                   | 家牦牛                    |
| Bos indicus                     | 瘤牛                      |
| Bos mutus                       | 野牦牛                    |
| Bos taurus                      | 家牛                      |
| Bradypus variegatus             | 褐喉树懒                  |
| Bubalus bubalis                 | 水牛                      |
| Callithrix jacchus              | 普通狨猴                  |
| Callorhinus ursinus             | 北海狗                    |
| Camelus bactrianus              | 双峰驼                    |
| Camelus dromedarius             | 单峰驼                    |
| Camelus ferus                   | 野骆驼                    |
| Canis lupus familiaris          | 家犬                      |
| Capra aegagrus                  | 野山羊                    |
| Capra hircus                    | 山羊                      |
| Capra ibex                      | 北山羊                    |
| Capra sibirica                  | 西伯利亚北山羊            |
| Capreolus capreolus             | 西方狍                    |
| Capreolus pygargus              | 西伯利亚狍                |
| Capromys pilorides              | 古巴硬毛鼠                |
| Caracal caracal                 | 狞猫                      |
| Carlito syrichta                | 菲律宾眼镜猴              |
| Carollia perspicillata          | 短尾果蝠                  |
| Castor canadensis               | 美洲河狸                  |
| Catagonus wagneri               | 查科野猪                  |
| Cavia aperea                    | 巴西豚鼠                  |
| Cavia porcellus                 | 豚鼠                      |
| Cavia tschudii                  | 查氏豚鼠                  |
| Cebus albifrons                 | 白额卷尾猴                |
| Cebus imitator                  | 白面卷尾猴                |
| Cephalophus harveyi             | 哈氏小羚羊                |
| Cercocebus atys                 | 白颈白眉猴                |
| Cercopithecus mona              | 白臀长尾猴                |
| Cercopithecus neglectus         | 德氏长尾猴                |
| Cervus elaphus                  | 马鹿                      |
| Cervus hanglu                   | 克什米尔马鹿              |
| Chaetophractus vellerosus       | 小犰狳                    |
| Cheirogaleus medius             | 肥尾鼠狐猴                |
| Chinchilla lanigera             | 长尾毛丝鼠                |
| Chlorocebus sabaeus             | 绿猴                      |
| Choloepus didactylus            | 二趾树懒                  |
| Choloepus hoffmanni             | 霍氏树懒                  |
| Chrysochloris asiatica          | 亚洲金毛鼹                |
| Colobus angolensis              | 安哥拉疣猴                |
| Condylura cristata              | 星鼻鼹                    |
| Connochaetes taurinus           | 斑纹角马                  |
| Craseonycteris thonglongyai     | 泰国猪鼻蝙蝠              |
| Cricetomys gambianus            | 非洲巨鼠                  |
| Cricetulus griseus              | 中国仓鼠                  |
| Crocidura indochinensis         | 印支麝鼩                  |
| Crocuta crocuta                 | 斑鬣狗                    |
| Cryptoprocta ferox              | 马岛长尾狸猫              |
| Ctenodactylus gundi             | 梳趾鼠                    |
| Ctenomys sociabilis             | 社会栉鼠                  |
| Cuniculus paca                  | 低地刺豚鼠                |
| Cynomys gunnisoni               | 甘尼森土拨鼠              |
| Cynopterus brachyotis           | 短耳犬蝠                  |
| Damaliscus lunatus              | 黑斑羚                    |
| Dasyprocta punctata             | 斑点刺豚鼠                |
| Dasypus novemcinctus            | 九带犰狳                  |
| Daubentonia madagascariensis    | 指猴                      |
| Delphinapterus leucas           | 白鲸                      |
| Desmodus rotundus               | 普通吸血蝠                |
| Dicerorhinus sumatrensis        | 苏门答腊犀牛              |
| Diceros bicornis                | 黑犀牛                    |
| Dinomys branickii               | 帕卡老鼠                  |
| Dipodomys ordii                 | 奥氏更格卢鼠              |
| Dipodomys stephensi             | 斯蒂芬更格卢鼠            |
| Dolichotis patagonum            | 巴塔哥尼亚豚鼠            |
| Dugong dugon                    | 儒艮                      |
| Echinops telfairi               | 小马岛猬                  |
| Eidolon helvum                  | 非洲棕榈果蝠              |
| Elaphurus davidianus            | 麋鹿（四不像）            |
| Elephantulus edwardii           | 爱德华象鼩                |
| Elephas maximus                 | 亚洲象                    |
| Ellobius lutescens              | 黄齿鼹形田鼠              |
| Ellobius talpinus               | 鼹形田鼠                  |
| Enhydra lutris (kenyoni)        | 海獭                      |
| Eonycteris spelaea              | 洞穴长舌蝠                |
| Eptesicus fuscus                | 大棕蝠                    |
| Equus asinus                    | 非洲野驴                  |
| Equus caballus                  | 马                        |
| Equus przewalskii               | 普氏野马                  |
| Erethizon dorsatum              | 北美豪猪                  |
| Erinaceus europaeus             | 西欧刺猬                  |
| Erythrocebus patas              | 赤猴                      |
| Eschrichtius robustus           | 灰鲸                      |
| Eubalaena japonica              | 北太平洋露脊鲸            |
| Eudorcas thomsonii              | 汤姆森瞪羚                |
| Eulemur flavifrons              | 蓝眼黑狐猴                |
| Eulemur fulvus                  | 褐狐猴                    |
| Eulemur macaco                  | 黑狐猴                    |
| Eumetopias jubatus              | 北海狮                    |
| Felis catus                     | 家猫                      |
| Felis nigripes                  | 黑足猫                    |
| Fukomys damarensis              | 达马拉兰鼹鼠              |
| Galeopterus variegatus          | 马来亚飞狐猴              |
| Giraffa camelopardalis          | 长颈鹿                    |
| Giraffa tippelskirchi           | 马赛长颈鹿                |
| Glis glis                       | 肥睡鼠                    |
| Globicephala melas              | 长肢领航鲸                |
| Gorilla gorilla                 | 西部大猩猩                |
| Gracilinanus agilis             | 敏捷负鼠                  |
| Grammomys surdaster             | 东非灌丛鼠                |
| Graphiurus murinus              | 非洲睡鼠                  |
| Gulo gulo                       | 狼獾                      |
| Gymnobelideus leadbeateri       | 利氏袋鼯                  |
| Halichoerus grypus              | 灰海豹                    |
| Helogale parvula                | 侏獴                      |
| Hemitragus hylocrius           | 塔尔羊                    |
| Heterocephalus glaber           | 裸鼹鼠                    |
| Heterohyrax brucei              | 布鲁斯蹄兔                |
| Hippopotamus amphibius          | 河马                      |
| Hipposideros armiger            | 大蹄蝠                    |
| Hipposideros galeritus          | 冠蹄蝠                    |
| Hippotragus equinus             | 马羚                      |
| Hippotragus niger               | 黑马羚                    |
| Homo sapiens                    | 人类                      |
| Hyaena hyaena                   | 条纹鬣狗                  |
| Hydrochoerus hydrochaeris       | 水豚                      |
| Hydrodamalis gigas              | 斯特拉海牛（已灭绝）      |
| Hydropotes inermis              | 獐                        |
| Hylobates moloch                | 银长臂猿                  |
| Hystrix brachyura               | 马来亚豪猪                |
| Hystrix cristata                | 非洲冠豪猪                |
| Ictidomys tridecemlineatus      | 十三纹地松鼠              |
| Indri indri                     | 大狐猴                    |
| Inia geoffrensis                | 亚马孙河豚                |
| Jaculus jaculus                 | 埃及跳鼠                  |
| Kobus ellipsiprymnus            | 水羚                      |
| Kobus leche                     | 驴羚                      |
| Kogia breviceps                 | 小抹香鲸                  |
| Lagenorhynchus obliquidens      | 太平洋斑纹海豚            |
| Lama glama                      | 大羊驼（美洲驼）          |
| Lama guanicoe                   | 原驼                      |
| Lasiurus borealis               | 红蝙蝠                    |
| Lemur catta                     | 环尾狐猴                  |
| Leptonychotes weddellii         | 威德尔海豹                |
| Lepus americanus                | 美洲雪兔                  |
| Lepus timidus                   | 雪兔                      |
| Lipotes vexillifer              | 白鱀豚（可能已灭绝）      |
| Litocranius walleri             | 长颈羚                    |
| Lontra canadensis               | 北美水獭                  |
| Lophiomys imhausi               | 冠豪猪                    |
| Loxodonta africana              | 非洲象                    |
| Lutra lutra                     | 欧亚水獭                  |
| Lycaon pictus                   | 非洲野犬                  |
| Lynx canadensis                 | 加拿大猞猁                |
| Lynx pardinus                   | 伊比利亚猞猁              |
| Macaca fascicularis             | 食蟹猕猴                  |
| Macaca fuscata                  | 日本猕猴                  |
| Macaca mulatta                  | 恒河猴                    |
| Macaca nemestrina               | 豚尾猕猴                  |
| Macroglossus sobrinus           | 长舌果蝠                  |
| Macrotus californicus           | 加州大耳蝠                |
| Madoqua kirkii                  | 柯氏犬羚                  |
| Mandrillus leucophaeus          | 鬼狒                      |
| Mandrillus sphinx               | 山魈                      |
| Manis crassicaudata             | 印度穿山甲                |
| Manis javanica                  | 马来穿山甲                |
| Manis pentadactyla              | 中华穿山甲                |
| Marmota flaviventris            | 黄腹土拨鼠                |
| Marmota himalayana              | 喜马拉雅旱獭              |
| Marmota marmota                 | 阿尔卑斯旱獭              |
| Marmota monax                   | 美洲旱獭                  |
| Marmota vancouverensis          | 温哥华岛土拨鼠            |
| Martes zibellina                | 紫貂                      |
| Mastomys coucha                 | 南非多乳鼠                |
| Megaderma lyra                  | 大耳假吸血蝠              |
| Megaptera novaeangliae          | 座头鲸                    |
| Mellivora capensis              | 蜜獾                      |
| Meriones unguiculatus           | 长爪沙鼠                  |
| Mesocricetus auratus            | 叙利亚仓鼠（金仓鼠）      |
| Mesoplodon bidens               | 索氏中喙鲸                |
| Microcebus griseorufus          | 灰红小鼠狐猴              |
| Microcebus mittermeieri         | 米氏小鼠狐猴              |
| Microcebus murinus              | 小鼠狐猴                  |
| Microcebus ravelobensis         | 拉维洛小鼠狐猴            |
| Microcebus sp. 3 GT-2019        | 鼠狐猴属未定种3 GT-2019   |
| Microcebus tavaratra            | 塔瓦拉特拉小鼠狐猴        |
| Microgale talazaci              | 塔拉扎克长尾鼩            |
| Micronycteris hirsuta           | 毛耳蝠                    |
| Microtus agrestis               | 田鼠                      |
| Microtus arvalis                | 普通田鼠                  |
| Microtus fortis                 | 东方田鼠                  |
| Microtus ochrogaster            | 草原田鼠                  |
| Microtus oeconomus              | 根田鼠                    |
| Microtus oregoni                | 俄勒冈田鼠                |
| Miniopterus natalensis          | 纳塔尔长翼蝠              |
| Miniopterus schreibersii        | 施氏长翼蝠                |
| Mirounga angustirostris         | 北象海豹                  |
| Mirounga leonina                | 南象海豹                  |
| Mirza coquereli                 | 科氏巨鼠狐猴              |
| Mirza zaza                      | 扎扎巨鼠狐猴              |
| Molossus molossus               | 犬吻蝠                    |
| Monodelphis domestica           | 灰短尾负鼠                |
| Monodon monoceros               | 独角鲸（一角鲸）          |
| Mormoops blainvillei            | 布莱氏裂颜蝠              |
| Moschus berezovskii             | 林麝                      |
| Moschus chrysogaster            | 喜马拉雅麝                |
| Moschus moschiferus             | 原麝                      |
| Mungos mungo                    | 缟獴                      |
| Muntiacus crinifrons           | 黑麂                      |
| Muntiacus muntjak              | 赤麂                      |
| Muntiacus reevesi              | 小麂                      |
| Murina aurata                   | 金背管鼻蝠                |
| Mus caroli                      | 卡罗尔小家鼠              |
| Mus minutoides                  | 非洲侏儒鼠                |
| Mus musculus                    | 家鼠                      |
| Mus pahari                      | 丛林鼠                    |
| Mus spicilegus                  | 堆鼠                      |
| Mus spretus                     | 阿尔及利亚小鼠            |
| Muscardinus avellanarius        | 榛睡鼠                    |
| Mustela erminea                 | 白鼬                      |
| Mustela putorius                | 欧洲鼬（雪貂）            |
| Myocastor coypus                | 河狸鼠                    |
| Myodes glareolus                | 欧岸鼠                    |
| Myotis brandtii                 | 布氏鼠耳蝠                |
| Myotis davidii                  | 大卫鼠耳蝠                |
| Myotis lucifugus                | 小棕蝠                    |
| Myotis myotis                   | 鼠耳蝠                    |
| Myrmecophaga tridactyla         | 大食蚁兽                  |
| Nanger granti                   | 葛氏瞪羚                  |
| Nannospalax galili              | 加利利盲鼠                |
| Nasalis larvatus                | 长鼻猴                    |
| Neomonachus schauinslandi       | 夏威夷僧海豹              |
| Neophocaena asiaeorientalis     | 东亚江豚                  |
| Neotoma lepida                  | 沙漠林鼠                  |
| Neotragus moschatus             | 桑岛新小羚                |
| Neotragus pygmaeus              | 侏羚                      |
| Neovison vison                  | 美洲水鼬（水貂）          |
| Noctilio leporinus              | 美洲兔唇蝠                |
| Nomascus leucogenys             | 白颊长臂猿                |
| Notamacropus eugenii            | 尤金袋鼠                  |
| Nyctereutes procyonoides        | 貉                        |
| Nycticebus coucang              | 懒猴                      |
| Nycticeius humeralis            | 黄昏蝠                    |
| Ochotona curzoniae              | 高原鼠兔                  |
| Ochotona princeps               | 北美鼠兔                  |
| Octodon degus                   | 八齿鼠                    |
| Octomys mimax                   | 山八齿鼠                  |
| Odobenus rosmarus               | 海象                      |
| Odocoileus hemionus             | 黑尾鹿                    |
| Odocoileus virginianus          | 白尾鹿                    |
| Okapia johnstoni                | 㺢㹢狓（霍加狓）          |
| Ondatra zibethicus              | 麝鼠                      |
| Onychomys torridus              | 南方食蝗鼠                |
| Orcinus orca                    | 虎鲸                      |
| Oreamnos americanus             | 雪羊                      |
| Oreotragus oreotragus           | 岩羚                      |
| Orientallactaga bullata         | 泡状五趾跳鼠              |
| Ornithorhynchus anatinus        | 鸭嘴兽                    |
| Orycteropus afer                | 土豚                      |
| Oryctolagus cuniculus           | 穴兔（家兔祖先）          |
| Oryx dammah                     | 弯角大羚羊                |
| Oryx gazella                    | 南非剑羚                  |
| Otocyon megalotis megalotis     | 大耳狐                    |
| Otolemur garnettii              | 加氏婴猴                  |
| Ourebia ourebi                  | 侏羚                      |
| Ovis ammon                      | 盘羊                      |
| Ovis aries                      | 绵羊                      |
| Ovis canadensis                 | 加拿大盘羊                |
| Ovis nivicola                   | 雪羊                      |
| Ovis orientalis                 | 东方盘羊                  |
| Pan paniscus                    | 倭黑猩猩                  |
| Pan troglodytes                 | 黑猩猩                    |
| Panthera leo                    | 狮子                      |
| Panthera onca                   | 美洲豹                    |
| Panthera pardus                 | 花豹                      |
| Panthera tigris                 | 虎                        |
| Papio anubis                    | 阿拉伯狒狒                |
| Paradoxurus hermaphroditus      | 椰子猫（棕榈猫）          |
| Pedetes capensis                | 南非跳兔                  |
| Perognathus longimembris        | 小囊鼠                    |
| Peromyscus attwateri            | 阿特沃特鹿鼠              |
| Peromyscus aztecus              | 阿兹特克鹿鼠              |
| Peromyscus californicus         | 加州鹿鼠                  |
| Peromyscus eremicus             | 沙漠鹿鼠                  |
| Peromyscus leucopus             | 白足鼠                    |
| Peromyscus maniculatus          | 鹿鼠                      |
| Peromyscus melanophrys          | 黑眉鹿鼠                  |
| Peromyscus nudipes              | 裸足鹿鼠                  |
| Peromyscus polionotus           | 旧田野鼠                  |
| Petromus typicus                | 岩鼠                      |
| Phacochoerus africanus          | 非洲疣猪                  |
| Phascolarctos cinereus          | 树袋熊（考拉）            |
| Phataginus tricuspis            | 树穿山甲                  |
| Philantomba maxwellii           | 麦氏小羚羊                |
| Phoca vitulina                  | 港海豹                    |
| Phocoena phocoena               | 鼠海豚                    |
| Phocoena sinus                  | 加湾鼠海豚（小头鼠海豚）  |
| Phodopus sungorus               | 坎贝尔侏儒仓鼠            |
| Phyllostomus discolor           | 叶口蝠                    |
| Physeter catodon                | 抹香鲸                    |
| Piliocolobus tephrosceles       | 乌黑白眉猴                |
| Pipistrellus kuhlii             | 库氏伏翼                  |
| Pipistrellus pipistrellus       | 普通伏翼                  |
| Pithecia pithecia               | 白面僧面猴                |
| Platanista gangetica            | 恒河豚                    |
| Platanista minor                | 印度河豚                  |
| Plecturocebus donacophilus      | 玻利维亚灰伶猴            |
| Pongo abelii                    | 苏门答腊猩猩              |
| Pontoporia blainvillei          | 拉河豚                    |
| Potos flavus                    | 蜜熊                      |
| Prionailurus bengalensis        | 豹猫                      |
| Prionailurus iriomotensis       | 西表山猫                  |
| Prionailurus viverrinus         | 渔猫                      |
| Procapra przewalskii            | 普氏原羚                  |
| Procavia capensis               | 岩蹄兔                    |
| Procyon lotor                   | 浣熊                      |
| Prolemur simus                  | 大竹狐猴                  |
| Propithecus coquereli           | 科氏冕狐猴                |
| Proteles cristata cristata      | 土狼                      |
| Przewalskium albirostris        | 白唇鹿                    |
| Psammomys obesus                | 肥沙鼠                    |
| Pseudois nayaur                 | 岩羊                      |
| Pteronotus parnellii            | 帕氏裸背蝠                |
| Pteronura brasiliensis          | 巨獭                      |
| Pteropus alecto                 | 黑狐蝠                    |
| Pteropus giganteus              | 印度狐蝠                  |
| Pteropus pselaphon              | 琉球狐蝠                  |
| Pteropus vampyrus               | 马来大狐蝠                |
| Puma concolor                   | 美洲狮                    |
| Puma yagouaroundi               | 美洲山猫（细腰猫）        |
| Pygathrix nemaeus               | 白臀叶猴                  |
| Rangifer tarandus               | 驯鹿                      |
| Raphicerus campestris           | 草原小羚羊                |
| Rattus norvegicus               | 褐家鼠                    |
| Rattus rattus                   | 黑家鼠                    |
| Redunca redunca                 | 芦苇羚                    |
| Rhinoceros unicornis            | 印度犀牛                  |
| Rhinolophus ferrumequinum       | 大马蹄蝠                  |
| Rhinopithecus bieti             | 滇金丝猴                  |
| Rhinopithecus roxellana         | 川金丝猴                  |
| Rhizomys pruinosus              | 灰竹鼠                    |
| Rhombomys opimus                | 大沙鼠                    |
| Rousettus aegyptiacus           | 埃及果蝠                  |
| Saguinus imperator              | 皇狨                      |
| Saiga tatarica                  | 赛加羚羊                  |
| Saimiri boliviensis             | 玻利维亚松鼠猴            |
| Sapajus apella                  | 卷尾猴                    |
| Sarcophilus harrisii            | 袋獾                      |
| Scalopus aquaticus              | 美洲鼹鼠                  |
| Sciurus carolinensis            | 东部灰松鼠                |
| Sciurus vulgaris                 | 欧亚红松鼠                |
| Semnopithecus entellus          | 长尾叶猴                  |
| Sigmodon hispidus               | 棉鼠                      |
| Solenodon paradoxus             | 沟齿鼩                    |
| Sorex araneus                   | 普通鼩鼱                  |
| Sousa chinensis                 | 中华白海豚                |
| Spermophilus dauricus           | 达乌尔黄鼠                |
| Spilogale gracilis              | 西部斑臭鼬                |
| Sturnira hondurensis            | 洪都拉斯果蝠              |
| Suricata suricatta              | 猫鼬（狐獴）              |
| Sus scrofa                      | 野猪                      |
| Sus scrofa domesticus           | 家猪                      |
| Sus scrofa scrofa               | 欧洲野猪                  |
| Sylvicapra grimmia              | 普通小羚羊                |
| Sylvilagus bachmani             | 灌丛棉尾兔                |
| Syncerus caffer                 | 非洲水牛                  |
| Tachyglossus aculeatus          | 短吻针鼹                  |
| Tadarida brasiliensis           | 巴西犬吻蝠                |
| Talpa occidentalis              | 欧洲鼹鼠                  |
| Tamandua tetradactyla           | 小食蚁兽                  |
| Tapirus indicus                 | 马来貘                    |
| Tapirus terrestris              | 南美貘                    |
| Taxidea taxus                   | 美洲獾                    |
| Theropithecus gelada            | 狮尾狒                    |
| Thryonomys swinderianus         | 非洲蔗鼠                  |
| Tolypeutes matacus              | 三带犰狳                  |
| Tonatia saurophila              | 蜥蜴蝠                    |
| Trachypithecus francoisi        | 黑叶猴                    |
| Tragelaphus buxtoni             | 山地薮羚                  |
| Tragelaphus eurycerus           | 大羚羊                    |
| Tragelaphus imberbis            | 小旋角羚                  |
| Tragelaphus oryx                | 大羚羊                    |
| Tragelaphus scriptus            | 林羚                      |
| Tragelaphus spekii              | 沼泽林羚                  |
| Tragelaphus strepsiceros        | 捻角羚                    |
| Tragulus javanicus              | 爪哇鼷鹿                  |
| Tragulus kanchil                | 小鼷鹿                    |
| Tremarctos ornatus              | 眼镜熊                    |
| Trichechus manatus              | 美洲海牛                  |
| Trichosurus vulpecula           | 帚尾袋貂                  |
| Tupaia belangeri                | 北树鼩                    |
| Tupaia chinensis                | 中国树鼩                  |
| Tupaia tana                     | 大树鼩                    |
| Tursiops aduncus                | 印太瓶鼻海豚              |
| Tursiops truncatus              | 宽吻海豚                  |
| Tympanoctomys barrerae          | 红沙鼠                    |
| Urocitellus parryii             | 北极地松鼠                |
| Uropsilus gracilis              | 长尾鼩鼹                  |
| Ursus americanus                | 美洲黑熊                  |
| Ursus arctos                    | 棕熊                      |
| Ursus maritimus                 | 北极熊                    |
| Ursus thibetanus                | 亚洲黑熊                  |
| Vicugna pacos                   | 羊驼                      |
| Vicugna vicugna                 | 骆马                      |
| Vombatus ursinus                | 毛鼻袋熊                  |
| Vulpes lagopus                  | 北极狐                    |
| Vulpes vulpes                   | 赤狐                      |
| Xerus inauris                   | 南非地松鼠                |
| Zalophus californianus          | 加州海狮                  |
| Zapus hudsonius                 | 草原跳鼠                  |
| Ziphius cavirostris             | 柯氏喙鲸                  |
