# Chinese HealthWSD Corpus
Chinese Healthcare Word Sense Disambiguation (HealthWSD) Corpus is collected and annotated by NYCU NLP Lab ([https://ainlp.tw/](https://ainlp.tw/)).

We first selected named entities in the [Chinese HealthNER corpus](https://github.com/NCUEE-NLPLab/Chinese-HealthNER-Corpus) (Lee and Lu, 2021) with coverage across 10 entity types (body, symptom, instrument, examinations, chemical, disease, drug, supplement, treatment and time) as seed entities to search the BabelNet version 5.0, a multilingual encyclopedic lexicon that contains named entities in a large network of semantic relations. A total of 735 distinct named entities contains at least two semantically different glosses in BabelNet. After manual checking, we selected 40 nouns as target biomedical entities that do not contain unclear or specific glosses such as names for creative works, author names and so on.

We use these 40 distinct words as seed query terms to search and retrieve results containing sentences with target named entities. To efficiently and accurately crawl sentences consisting of ambiguous target words with different glosses, we manually allocated gloss-related keywords along with target words as queries which were automatically input into the Google search engine to obtain appropriate search results. We then crawled the corresponding web pages, removed all HTML tags, images, videos and embedded web advertisements, split the remaining texts into sentences, and retained sentences containing at least one target entity word for manual annotation.

Three graduate students majoring in the electrical engineering system and biomedical group were trained in word sense tagging. Each sentence was annotated by three annotators to select an appropriate gloss of the target entity. All annotators were asked to discuss differences and seek consensus. If no consensus could be reached after discussion, those sentences were excluded in our constructed data. 

Through this process, we created the Chinese HealthWSD corpus that can be used for entity linking research in the biomedical domain. The most common entities have 2 glosses (29 target words or 72.5% of the total), followed by 3 glosses (7 words/17.5%) and 4 glosses (4 words/10%). We have a total of 10,218 sentences containing biomedical named entities with annotated glosses in BabelNet 5.0. Each sentence contains an average of 52.49 tokens (characters and punctuations).

|    Type   | Target Entities                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | #Gloss | #Sent  | #Token  |
|:---------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|--------|---------|
| 2 glosses | 前臂  (forearm)、皮毛 (coat)、*部位 (component)、黏液 (mucus)、心臟病 (heart disease) 、乳管 (lactiferous duct)、薄膜 (Biological membrane)、鼓膜 (eardrum)、胚囊 (gestational sec)、分泌物(exudate)、組織 (tissue)、手足 (hands and feet)、多巴胺 (dopamine)、卵巢 (ovary)、超音波 (ultrasound)、顯影劑 (contrast medium)、息肉 (polyp)、炭疽病 (anthrax)、白斑 (vitiligo)、*緊身衣 (skin-tight garment)、*檢測(assay)、*鏡頭(camera lens)、呼吸管(snorkel)、牙套(gumshield)、神經衰弱(neurasthenia)、閉鎖 (atresia)、過敏反應(allergy)、脂肪(adipose tissue)、石膏 (gypsum) | 58     | 7,409   | 393,726 |
| 3 glosses | 眨眼 (blink)、結節 (nodule)、黑眼圈 (black eye)、乳房 (udder)、*香料 (spice)、穿刺 (centesis)、*手套 (glove)                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 21     | 1,780  | 92,676  |
| 4 glosses | 隔膜  (diaphragm)、眼睛 (eye)、導管 (catheter)、眼罩 (blindfold)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 16     | 1,029  | 49,931  |
| Total     | 40 distinct entities                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | 95     | 10,218 | 536,333 |


## Data Format
* lexical
  * item: target word
* instance
  * id: a sentence identifier
* answer
  * instance: a target word identifier in sentence
  * synsetid: word sense id in BabelNet version 5.0
* context: a sentence contains the target word
## Example
```
<lexical item="心臟病">
  <instance id="心臟病.1">
    <answer instance="心臟病.1.0" synsetid="03227690n" />
    <context>首先呢，先訂好舞步，當喊到的數字跟掀開一樣的時候，所有人必須離開位置，到旁邊自己找一個空廣的地方，把原先訂好的舞步跳完才能去拍，這個玩法原先是出至於有一家人的桌子長期玩<head>心臟病</head>結果被拍壞，為了提高之後桌子的長期使用性而想出的玩法。</context>
  </instance>
</lexical>
<lexical item="前臂">
  <instance id="前臂.187">
    <answer instance="前臂.187.0" synsetid="00035801n" />
    <answer instance="前臂.187.1" synsetid="00035801n" />
    <context>而且關於<head>前臂</head>的訓練切記不要總想著短期內就能讓你的<head>前臂</head>出效果，而是在不斷堅持中尋求進步！一定不要因為出效果慢而放棄。</context>
  </instance>
</lexical>
```
## Statistics
|  Datasets  | #Sent  | #Token  |
|:----------:|--------|---------|
|  Training  | 7,109  | 373,152 |
| Validation | 979    | 50,320  |
|    Test    | 2,130  | 112,861 |
| All        | 10,218 | 536,333 |

## Citation

For more information please refer to our ACM TALLIP Paper: https://doi.org/10.1145/3638555

Tzu-Mi Lin, Man-Chen Hung, and Lung-Hao Lee (2024). Leveraging Daul Gloss Encoders in Chinese Biomedical Entity Linking. *ACM Transactions on Asian and Low-Resource Language Information Processing*. (accepted for publication).[https://doi.org/10.1145/3638555](https://doi.org/10.1145/3638555)

@ARTICLE{Lin-ACMTALLIP-2024,<br>
&emsp;&emsp;&emsp;&emsp;author  = {Tzu-Mi Lin, Man-Chen Hung, and Lung-Hao Lee},<br>
&emsp;&emsp;&emsp;&emsp;title   = {Leveraging Daul Gloss Encoders in Chinese Biomedical Entity Linking},<br>
&emsp;&emsp;&emsp;&emsp;journal = {ACM Transactions on Asian and Low-Resource Language Information Processing},<br>
&emsp;&emsp;&emsp;&emsp;volume  = ,<br>
&emsp;&emsp;&emsp;&emsp;number  = ,<br>
&emsp;&emsp;&emsp;&emsp;pages   = {},<br>
&emsp;&emsp;&emsp;&emsp;month   = ,<br>
&emsp;&emsp;&emsp;&emsp;year    = 2024,<br>
&emsp;&emsp;&emsp;&emsp;url     = { https://doi.org/10.1145/3638555 }<br>
}   

## Reference

Lung-Hao Lee and Yi Lu (2021). Multiple Embeddings Enhanced Multi-Graph Neural Networks for Chinese Healthcare Named Entity Recognition. *IEEE Journal of Biomedical and Health Informatics*, 25(7), pp. 2801-2810. [https://doi.org/10.1109/JBHI.2020.3048700](https://doi.org/10.1109/JBHI.2020.3048700)
