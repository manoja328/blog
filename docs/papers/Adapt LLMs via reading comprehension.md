---
layout: post
title: Adapt LLMs via reading comprehension
comments: true
date: 2025-07-14
links.mdlinks: true
links.convert: true
links.internals: false
links.nonShared: false
tags:
  - ML
  - paper
  - LLM
share: true
---
## Takeaways

- talks about how to adapt LLMs through transformation of raw corpora to series of NLP tasks
- much better than just feeding raw texts 
- Just fine-tuning causes a drop in its prompting ability ?? ( Table 1 ) .. not very conclusive of this experiment personally
- Related to instruction fine-tuning and create IFT data .. older method use more capable LLMs to create such examples ( but has a high cost)

## Example

Here is the first part of an article about biomedicine: Recent reported evidence indicates that vocal cord carcinoma is evolving similarly to oropharyngeal cancer with an increasing number of patients (...) 

- Answer questions based on the article: What is a summary? Glottic Carcinoma in Young Patients.

- Generate a sentence that includes these biomedicine keywords [carcinoma, oropharyngeal, papillomavirus]: Recent reported evidence indicates that vocal cord carcinoma is evolving...

- Premise:... Hypothesis:... Does the premise entail the hypothesis? Yes What is the reason for ”..."? the morphology of the lesions and the patients' young age.

- Compose a sentence that contradicts the meaning of "Historically, glottic carcinoma ... ”.  
- Answer: Recent published evidence ...

- How would you complete the article? This finding further supports...


## Hows
- Use templates to create such task 
	- To identify domain-specific words, they  use the SentencePiece tool (Kudo & Richardson, 2018) to build a vocabulary from the target domain corpora.
	- Then use the domain-specific keywords in the sentence as the input, asking the model to generate a sentence with
	- Generate a sentence that includes these {DOMAIN} keywords.
- For  “Entailment” if they are connected by the verbalizer Therefore, and as “Contradictory” if connected by However.

![Pasted image 20240925103354.png](Pasted%20image%2020240925103354.png)
## Data

- financial news from May 2022 to May 20232 for over 7, 000 stocks, using the FinGPT codebase
- PubMed Abstracts and FreeLaw Opinions from the Pile as pre-training corpora for the biomedicine and law domains
## Models
- MedAlpaca
- BloomBergGPT
- LexGPT

##  Resources

Published as a conference paper at ICLR 2024 , 
ADAPTING LARGE LANGUAGE MODELS VIA READING COMPREHENSION
Daixuan Cheng, Shaohan Huang∗ & Furu Wei Microsoft Research
[https://huggingface.co/AdaptLLM](https://huggingface.co/AdaptLLM)