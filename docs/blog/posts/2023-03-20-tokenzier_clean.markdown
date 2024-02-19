---
layout: post
title:  "visualizing tokenization in jupyter notebook"
excerpt: adding some colors to tokenizer
comments: true
date:   2023-3-20 19:26:37 +0545
categories: NLP 
---


```python
%matplotlib inline
```

```python
#display tokens as boxes in jupyter notebook
def jupyter_display_html(html):
    from IPython.display import display, HTML
    style = '''
        <style>
        .token {
            display: inline-block;
            padding: 5px;
            margin: 5px;
            border-radius: 5px;
            background-color: #eee;
        }
        .token[data-pos="NN"] {
            background-color: #f00;
        }
        .token[data-pos="VB"] {
            background-color: #0e0;
        }
        .token[data-pos="JJ"] {
            background-color: #0096FF;
        }
        </style>
        '''
    display(HTML(style + html))
    
#wrap each word in box and return as html to display in jupyter notebook
def pos_tagged_html(text):
    tokens = nltk.word_tokenize(text)
    pos_tags = nltk.pos_tag(tokens)
    html = ''
    for token, pos_tag in pos_tags:
        html += f'<div class="token" data-pos="{pos_tag}">{token} [{pos_tag}]</div>'
    return html
```

## Now lets add some nice visualization color to it


```python
pos_html = pos_tagged_html(text)
pos_html
```


## This is the HTML output

    '<div class="token" data-pos="WRB">When [WRB]</div><div class="token" data-pos="JJ">Sebastian [JJ]</div><div class="token" data-pos="NNP">Thrun [NNP]</div><div class="token" data-pos="VBD">started [VBD]</div><div class="token" data-pos="VBG">working [VBG]</div><div class="token" data-pos="IN">on [IN]</div><div class="token" data-pos="JJ">self-driving [JJ]</div><div class="token" data-pos="NNS">cars [NNS]</div><div class="token" data-pos="IN">at [IN]</div><div class="token" data-pos="NNP">Google [NNP]</div><div class="token" data-pos="IN">in [IN]</div><div class="token" data-pos="CD">2007 [CD]</div><div class="token" data-pos=",">, [,]</div><div class="token" data-pos="JJ">few [JJ]</div><div class="token" data-pos="NNS">people [NNS]</div><div class="token" data-pos="IN">outside [IN]</div><div class="token" data-pos="IN">of [IN]</div><div class="token" data-pos="DT">the [DT]</div><div class="token" data-pos="NN">company [NN]</div><div class="token" data-pos="VBD">took [VBD]</div><div class="token" data-pos="PRP">him [PRP]</div><div class="token" data-pos="RB">seriously [RB]</div><div class="token" data-pos=".">. [.]</div>'




```python
jupyter_display_html(pos_html)
```



<style>
.token {
    display: inline-block;
    padding: 5px;
    margin: 5px;
    border-radius: 5px;
    background-color: #eee;
}
.token[data-pos="NN"] {
    background-color: #f00;
}
.token[data-pos="VB"] {
    background-color: #0e0;
}
.token[data-pos="JJ"] {
    background-color: #0096FF;
}
</style>
<div class="token" data-pos="WRB">When [WRB]</div><div class="token" data-pos="JJ">Sebastian [JJ]</div><div class="token" data-pos="NNP">Thrun [NNP]</div><div class="token" data-pos="VBD">started [VBD]</div><div class="token" data-pos="VBG">working [VBG]</div><div class="token" data-pos="IN">on [IN]</div><div class="token" data-pos="JJ">self-driving [JJ]</div><div class="token" data-pos="NNS">cars [NNS]</div><div class="token" data-pos="IN">at [IN]</div><div class="token" data-pos="NNP">Google [NNP]</div><div class="token" data-pos="IN">in [IN]</div><div class="token" data-pos="CD">2007 [CD]</div><div class="token" data-pos=",">, [,]</div><div class="token" data-pos="JJ">few [JJ]</div><div class="token" data-pos="NNS">people [NNS]</div><div class="token" data-pos="IN">outside [IN]</div><div class="token" data-pos="IN">of [IN]</div><div class="token" data-pos="DT">the [DT]</div><div class="token" data-pos="NN">company [NN]</div><div class="token" data-pos="VBD">took [VBD]</div><div class="token" data-pos="PRP">him [PRP]</div><div class="token" data-pos="RB">seriously [RB]</div><div class="token" data-pos=".">. [.]</div>



```python

```
