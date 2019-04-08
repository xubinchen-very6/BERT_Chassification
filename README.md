## Introduction
这个项目主要是用BERT进行中文情感分类，后期会更新模型细节及BERT-Chinese的一些tricks

## Dependencies
Tensorflow 1.11  
tqdm

## Dataset

```python
def get_train_examples(data_dir):
    file_path = os.path.join(data_dir, 'train_sentiment.txt')
    f = open(file_path, 'r', encoding='utf-8')
    train_data = []
    index = 0
    for line in f.readlines():
        guid = 'train-%d' % index#参数guid是用来区分每个example的
        line = line.replace("\n", "").split("\t")
        text_a = tokenization.convert_to_unicode(str(line[1]))#要分类的文本
        label = str(line[2])#文本对应的情感类别
        train_data.append(InputExample(guid=guid, text_a=text_a, text_b=None, label=label))#加入到InputExample列表中
        index += 1
    return train_data
```


```python
1	最大的优点也就是价钱比较实惠，另外有免费停车场如果住在古镇里面，白天是不允许把车开进去的。这个宾馆的服务员都说自己的餐厅做的当地小吃好吃，实在不敢苟同，份量少，味道也不地道，价格却不低，建议重视当地美食的朋友不要在宾馆的餐厅就餐，会对山西的小吃产生错误	2

2	华为回应CFO孟晚舟在加拿大被捕不实报道	2

3	这个配置和价位真的很合适，完全够用，而且小黑的质量非常不错。	1

4	待机长，色彩鲜艳，屏幕大，成象效果好，我用了飞利浦535、T628等手机，在价格上比GD88要贵，可是实际效果比上两款手要好很多，真的！或许在时尚的外观上不如，但是最后还是选择了GD88！！	0

5	之前2次是10月中旬的时候住的,记忆不是很深刻了，但是即使我再怎么不满意,我后来还是定了这里，而且一直跟朋友推荐这里，然后这次的经历真的是让我极度不爽!CTRIP预定的房间,大床,以前这样的大床,158还是168,现在的大床就是当初这样的房间,房价200多	0
```

```python
原始文本: ['15362', '记忆最深的是作者说的一句话父母之爱都是深如大海，但有质量差别！这是一本为人师为人父母都值得好好一看的书，对中国传统型教育思想和方式是一个不小的碰撞和冲击。单位里同样有不少同事的孩子在做着留守儿童，也都存在着或多或少的问题，经常听到他们会发出许多无奈的感叹', '0']
样本id: 15362
待分类文本: 记忆最深的是作者说的一句话父母之爱都是深如大海，但有质量差别！这是一本为人师为人父母都值得好好一看的书，对中国传统型教育思想和方式是一个不小的碰撞和冲击。单位里同样有不少同事的孩子在做着留守儿童，也都存在着或多或少的问题，经常听到他们会发出许多无奈的感叹
所属标签: 0
```

## Performance
Classification|Dev F1|Test F1|step
----|----|----|---
TextCNN|||
Bert-Chinese|||

## TODO
- [ ] Update completed README.MD
- [ ] Update Bert-Chinese
- [ ] Update TextCNN
- [ ] Tricks and summary
