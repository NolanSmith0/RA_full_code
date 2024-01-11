# RA_full_code
This Repo is used as supplementary material for Jiahe Wang's MFE and MQF application
---
## Intro
There are three files in this repo:

- ```EDA.ipynb``` : My code for proproccessing data.

- ```All_In_One.ipynb``` : My code for Reproduction of the paper ```Larsen, Vegard H., and Leif A. Thorsrud. "The value of news for economic developments." Journal of Econometrics 210.1 (2019): 203-218.``` on a chinese news data set. The code does the following things:
- - 1. Reading raw files. Raw files are stored in .json, first task is extract title, content, source and time in the data. Each line in the json file is one news, and is in the form of ```{"headline": "", "author": "", "source": "", "url": "", "pub_type_name": "", "pub_time": "", "content": "", "md5_doc_id": "a08a5d93ae7db893f381c346a4f64483", "index": 23132544}```. This part of work is done using the ```EDA.ipynb```.
    2. Then, chinese is different from English in the sense that there is no space between words in chinese, like the following words: ‘我喜欢吃蛋糕’ (I like to eat cakes.). So I need to split the sentences into words first and that's what the library pyhanlp does. It is mained by a Chinese and is one of the most famous libraries in the filed of Chinese NLP. I used a model called Perceptron Lexical Analyzer in ```EDA.ipynb```.
    3. After splitting the words, I need to filter useless words like stopping words and used a method called Tf_IDF_Selection, which is also the function name that implements it. Larsen and Leif also run an algorithm known as stemming to reduce all words to their respective word stems. But Chinese words don't work in that way. Instead, I remvoed words depending on its type : ```['/介词', '/代词', '/副词', '/助词', '/方位词', '/时间词', '/数词', '/连词', '/量词', '/副形词', '/标点符号', '/名语素']```.
    4. We can now fitt the LDA model. This part is abstracted in the function ```LDA```.
    5. After fitting the model, we need to infer and maybe visulize the data, function ```get_topics_frequency```, ```plot_network_graph```, ```save_topic_percentage_plot``` does some plotting and frequency calculations, I write detailed doc strings in the code, you can check the All_In_One notebook.
  
- ```FreeYourHandv2.1.2.ipynb``` : This is my work for automatically downloading the news in a news archive platform called Proquest. I need to taught other group mebers to use it so markdowns in it are Chinese. This code does a very simple job(while there is more pages, click choose and next page, if selected 5 pages, start downloading.) Below is a picture of website Proquest:
![Proquest web page](https://github.com/NolanSmith0/RA_full_code/blob/main/proquest.png)
