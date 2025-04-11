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

可以根据的喜好增减物种（可以参考本文档最后的[已测序哺乳动物列表](#438个已被全基因测序的哺乳动物列表)）。请保证最少有4个物种。

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

```
Acinonyx jubatus
Acomys cahirinus
Acomys russatus
Aeorestes cinereus
Aepyceros melampus
Ailuropoda melanoleuca
Ailurus fulgens
Alces alces
Alouatta palliata
Ammotragus lervia
Anoura caudifer
Antechinus flavipes
Antechinus stuartii
Antidorcas marsupialis
Antilocapra americana
Antrozous pallidus
Aotus nancymaae
Aplodontia rufa
Apodemus speciosus
Apodemus sylvaticus
Arctocephalus gazella
Artibeus jamaicensis
Arvicanthis niloticus
Arvicola amphibius
Ateles geoffroyi
Axis porcinus
Balaenoptera acutorostrata
Balaenoptera bonaerensis
Balaenoptera musculus
Balaenoptera physalus
Beatragus hunteri
Bison bison
Bos frontalis
Bos gaurus
Bos grunniens
Bos indicus
Bos mutus
Bos taurus
Bradypus variegatus
Bubalus bubalis
Callithrix jacchus
Callorhinus ursinus
Camelus bactrianus
Camelus dromedarius
Camelus ferus
Canis lupus familiaris
Capra aegagrus
Capra hircus
Capra ibex
Capra sibirica
Capreolus capreolus
Capreolus pygargus
Capromys pilorides
Caracal caracal
Carlito syrichta
Carollia perspicillata
Castor canadensis
Catagonus wagneri
Cavia aperea
Cavia porcellus
Cavia tschudii
Cebus albifrons
Cebus imitator
Cephalophus harveyi
Cercocebus atys
Cercopithecus mona
Cercopithecus neglectus
Cervus elaphus
Cervus hanglu
Chaetophractus vellerosus
Cheirogaleus medius
Chinchilla lanigera
Chlorocebus sabaeus
Choloepus didactylus
Choloepus hoffmanni
Chrysochloris asiatica
Colobus angolensis
Condylura cristata
Connochaetes taurinus
Craseonycteris thonglongyai
Cricetomys gambianus
Cricetulus griseus
Crocidura indochinensis
Crocuta crocuta
Cryptoprocta ferox
Ctenodactylus gundi
Ctenomys sociabilis
Cuniculus paca
Cynomys gunnisoni
Cynopterus brachyotis
Damaliscus lunatus
Dasyprocta punctata
Dasypus novemcinctus
Daubentonia madagascariensis
Delphinapterus leucas
Desmodus rotundus
Dicerorhinus sumatrensis
Diceros bicornis
Dinomys branickii
Dipodomys ordii
Dipodomys stephensi
Dolichotis patagonum
Dugong dugon
Echinops telfairi
Eidolon helvum
Elaphurus davidianus
Elephantulus edwardii
Elephas maximus
Ellobius lutescens
Ellobius talpinus
Enhydra lutris (kenyoni)
Eonycteris spelaea
Eptesicus fuscus
Equus asinus
Equus caballus
Equus przewalskii
Erethizon dorsatum
Erinaceus europaeus
Erythrocebus patas
Eschrichtius robustus
Eubalaena japonica
Eudorcas thomsonii
Eulemur flavifrons
Eulemur fulvus
Eulemur macaco
Eumetopias jubatus
Felis catus
Felis nigripes
Fukomys damarensis
Galeopterus variegatus
Giraffa camelopardalis
Giraffa tippelskirchi
Glis glis
Globicephala melas
Gorilla gorilla
Gracilinanus agilis
Grammomys surdaster
Graphiurus murinus
Gulo gulo
Gymnobelideus leadbeateri
Halichoerus grypus
Helogale parvula
Hemitragus hylocrius
Heterocephalus glaber
Heterohyrax brucei
Hippopotamus amphibius
Hipposideros armiger
Hipposideros galeritus
Hippotragus equinus
Hippotragus niger
Homo sapiens
Hyaena hyaena
Hydrochoerus hydrochaeris
Hydrodamalis gigas
Hydropotes inermis
Hylobates moloch
Hystrix brachyura
Hystrix cristata
Ictidomys tridecemlineatus
Indri indri
Inia geoffrensis
Jaculus jaculus
Kobus ellipsiprymnus
Kobus leche
Kogia breviceps
Lagenorhynchus obliquidens
Lama glama
Lama guanicoe
Lasiurus borealis
Lemur catta
Leptonychotes weddellii
Lepus americanus
Lepus timidus
Lipotes vexillifer
Litocranius walleri
Lontra canadensis
Lophiomys imhausi
Loxodonta africana
Lutra lutra
Lycaon pictus
Lynx canadensis
Lynx pardinus
Macaca fascicularis
Macaca fuscata
Macaca mulatta
Macaca nemestrina
Macroglossus sobrinus
Macrotus californicus
Madoqua kirkii
Mandrillus leucophaeus
Mandrillus sphinx
Manis crassicaudata
Manis javanica
Manis pentadactyla
Marmota flaviventris
Marmota himalayana
Marmota marmota
Marmota monax
Marmota vancouverensis
Martes zibellina
Mastomys coucha
Megaderma lyra
Megaptera novaeangliae
Mellivora capensis
Meriones unguiculatus
Mesocricetus auratus
Mesoplodon bidens
Microcebus griseorufus
Microcebus mittermeieri
Microcebus murinus
Microcebus ravelobensis
Microcebus sp. 3 GT-2019
Microcebus tavaratra
Microgale talazaci
Micronycteris hirsuta
Microtus agrestis
Microtus arvalis
Microtus fortis
Microtus ochrogaster
Microtus oeconomus
Microtus oregoni
Miniopterus natalensis
Miniopterus schreibersii
Mirounga angustirostris
Mirounga leonina
Mirza coquereli
Mirza zaza
Molossus molossus
Monodelphis domestica
Monodon monoceros
Mormoops blainvillei
Moschus berezovskii
Moschus chrysogaster
Moschus moschiferus
Mungos mungo
Muntiacus crinifrons
Muntiacus muntjak
Muntiacus reevesi
Murina aurata
Mus caroli
Mus minutoides
Mus musculus
Mus pahari
Mus spicilegus
Mus spretus
Muscardinus avellanarius
Mustela erminea
Mustela putorius
Myocastor coypus
Myodes glareolus
Myotis brandtii
Myotis davidii
Myotis lucifugus
Myotis myotis
Myrmecophaga tridactyla
Nanger granti
Nannospalax galili
Nasalis larvatus
Neomonachus schauinslandi
Neophocaena asiaeorientalis
Neotoma lepida
Neotragus moschatus
Neotragus pygmaeus
Neovison vison
Noctilio leporinus
Nomascus leucogenys
Notamacropus eugenii
Nyctereutes procyonoides
Nycticebus coucang
Nycticeius humeralis
Ochotona curzoniae
Ochotona princeps
Octodon degus
Octomys mimax
Odobenus rosmarus
Odocoileus hemionus
Odocoileus virginianus
Okapia johnstoni
Ondatra zibethicus
Onychomys torridus
Orcinus orca
Oreamnos americanus
Oreotragus oreotragus
Orientallactaga bullata
Ornithorhynchus anatinus
Orycteropus afer
Oryctolagus cuniculus
Oryx dammah
Oryx gazella
Otocyon megalotis megalotis
Otolemur garnettii
Ourebia ourebi
Ovis ammon
Ovis aries
Ovis canadensis
Ovis nivicola
Ovis orientalis
Pan paniscus
Pan troglodytes
Panthera leo
Panthera onca
Panthera pardus
Panthera tigris
Papio anubis
Paradoxurus hermaphroditus
Pedetes capensis
Perognathus longimembris
Peromyscus attwateri
Peromyscus aztecus
Peromyscus californicus
Peromyscus eremicus
Peromyscus leucopus
Peromyscus maniculatus
Peromyscus melanophrys
Peromyscus nudipes
Peromyscus polionotus
Petromus typicus
Phacochoerus africanus
Phascolarctos cinereus
Phataginus tricuspis
Philantomba maxwellii
Phoca vitulina
Phocoena phocoena
Phocoena sinus
Phodopus sungorus
Phyllostomus discolor
Physeter catodon
Piliocolobus tephrosceles
Pipistrellus kuhlii
Pipistrellus pipistrellus
Pithecia pithecia
Platanista gangetica
Platanista minor
Plecturocebus donacophilus
Pongo abelii
Pontoporia blainvillei
Potos flavus
Prionailurus bengalensis
Prionailurus iriomotensis
Prionailurus viverrinus
Procapra przewalskii
Procavia capensis
Procyon lotor
Prolemur simus
Propithecus coquereli
Proteles cristata cristata
Przewalskium albirostris
Psammomys obesus
Pseudois nayaur
Pteronotus parnellii
Pteronura brasiliensis
Pteropus alecto
Pteropus giganteus
Pteropus pselaphon
Pteropus vampyrus
Puma concolor
Puma yagouaroundi
Pygathrix nemaeus
Rangifer tarandus
Raphicerus campestris
Rattus norvegicus
Rattus rattus
Redunca redunca
Rhinoceros unicornis
Rhinolophus ferrumequinum
Rhinopithecus bieti
Rhinopithecus roxellana
Rhizomys pruinosus
Rhombomys opimus
Rousettus aegyptiacus
Saguinus imperator
Saiga tatarica
Saimiri boliviensis
Sapajus apella
Sarcophilus harrisii
Scalopus aquaticus
Sciurus carolinensis
Sciurus vulgaris
Semnopithecus entellus
Sigmodon hispidus
Solenodon paradoxus
Sorex araneus
Sousa chinensis
Spermophilus dauricus
Spilogale gracilis
Sturnira hondurensis
Suricata suricatta
Sus scrofa
Sus scrofa domesticus
Sus scrofa scrofa
Sylvicapra grimmia
Sylvilagus bachmani
Syncerus caffer
Tachyglossus aculeatus
Tadarida brasiliensis
Talpa occidentalis
Tamandua tetradactyla
Tapirus indicus
Tapirus terrestris
Taxidea taxus
Theropithecus gelada
Thryonomys swinderianus
Tolypeutes matacus
Tonatia saurophila
Trachypithecus francoisi
Tragelaphus buxtoni
Tragelaphus eurycerus
Tragelaphus imberbis
Tragelaphus oryx
Tragelaphus scriptus
Tragelaphus spekii
Tragelaphus strepsiceros
Tragulus javanicus
Tragulus kanchil
Tremarctos ornatus
Trichechus manatus
Trichosurus vulpecula
Tupaia belangeri
Tupaia chinensis
Tupaia tana
Tursiops aduncus
Tursiops truncatus
Tympanoctomys barrerae
Urocitellus parryii
Uropsilus gracilis
Ursus americanus
Ursus arctos
Ursus maritimus
Ursus thibetanus
Vicugna pacos
Vicugna vicugna
Vombatus ursinus
Vulpes lagopus
Vulpes vulpes
Xerus inauris
Zalophus californianus
Zapus hudsonius
Ziphius cavirostris
```
