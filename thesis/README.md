# Multilingual Neural Machine Translation for Low Resource Languages


[Abstract](#Abstract) 

[Chapter-I](#Chapter-I) 
[Chapter-II](#Chapter-II)
[Chapter-III](#Chapter-III)
[Chapter-IV](#Chapter-IV)
[Chapter-V](#Chapter-V)
[Chapter-VI](#Chapter-VI)
[Chapter-VII](#Chapter-VII)
[Chapter-VIII](#Chapter-VIII)





## Abstract

---


Machine Translation (MT) is the task of mapping a source language to a target language. The recent introduction of neural MT (NMT) has shown promising results for high-resource language, however, poorly performing for low-resource language (LRL) settings. Furthermore, the vast majority of the +7,000 languages around the world do not have parallel data, creating a zero-resource language (ZRL) scenario. 

In this thesis, we present our approach to improving NMT for LRL and ZRL, leveraging a multilingual NMT modeling  (M-NMT), an approach that allows building a single NMT to translate across multiple source and target languages. 

This thesis is organized in the following topics:

- analyzing the effectiveness of M-NMT for LRL and ZRL translation tasks, spanning two NMT modeling architectures (Recurrent and Transformer)

- presents a self-learning approach for improving the zero-shot translation directions of ZRLs, 

- proposes a dynamic transfer-learning approach from a pre-trained (parent) model to a LRL (child) model by tailoring to the vocabulary entries of the latter, 

- extends M-NMT to translate from a source language to specific language varieties (e.g. dialects), and finally, 

- proposes an approach that can control the verbosity of an NMT model output. 

Our experimental findings show the effectiveness of the proposed approaches in improving NMT of LRLs and ZRLs.


Below you can find a summarized introduction for each of the thesis chapters.



## Chapters

---

### Chapter I

#### Introduction


This thesis, focuses on the limitations of NMT due to the amount of available training data when addressing NMT into *low- or zero-resource languages, language varieties and styles*. To tackle the lack of parallel training examples, our work is heavily based on MNMT. In particular, *modeling multiple translation tasks within a single model, leveraging better data augmentation techniques and maximizing positive transfer learning* in order to incrementally improve low-resource and zero-resource MT represents the main theme of this thesis.



### Chapter II

#### Background: Sequence-to-Sequence Model for Multilingual Translation

"... begin with an overview of machine translation (MT), followed by
a discussion of artificial neural networks (NNs) and the basic building blocks used for implementing MT models. 
First, we introduce the simplest form of NNs, called feed forward NN. Then, while discussing the necessary ingredients and algorithm for training a NN, we introduce a more powerful NN variant, called recurrent NN. Hence, we discuss sequence-to-sequence (seq2seq) modeling − a NN connecting two distinct NNs referred to as encoder and decoder. We further elaborate on seq2seq modeling focusing on how and why a new module called attention is integrated with the encoder-decoder networks. This will lead us to discuss on a more recent variant called Transformer, a NN solely built on the notion of attention mechanism.
In the rest of the chapter, we focus on neural MT (NMT), by describing the required procedures to build a translation model, the training and inference stages, data preparation and model evaluation. We then look at the different NMT training variants, supervised, semi-supervised and unsupervised training. We conclude by relating motivations and hypotheses, discussed in Chapter 1, with low-resource and zero-resource NMT."



## Chapter III 
#### Multilingual NMT for Low-Resource Languages

In this chapter, we first investigate the effectiveness of a single encoder and decoder-based
multilingual modeling approach for improving low-resource language translation. Covering up to six language directions, we show how a low-resource multilingual setting can
achieve large improvements over training language pair specific models. Then, by scaling
the number of translation directions we explore the impact on zero-shot translation performance. Moreover, we probe pivoting translation as an alternative approach for achieving
a zero-resource translation task. Finally, we focus on an empirical comparison of recurrence and transformer based seq2seq architectures on multilingual NMT (M-NMT). We
provide quantitative analysis on bilingual, multilingual and zero-shot translation outputs.
By leveraging multiple post-edits of automatic translations we demonstrate how language
relatedness influences zero-shot translation.
This [work](https://arxiv.org/abs/1806.06957) can be an interesting read.

<!--
In the rest of the chapter, we begin in Sec. 3.1 with a summary of the problem
statement and the motivation for improving low-resource language translation with a
multilingual modeling approach. In Sec. 3.2, we expand our discussion of M-NMT focusing
on zero-shot translation. Following the experimental results, we analyze the performance
of the zero-shot and pivoting translation mechanisms against single language pair models.
Finally, Sec. 3.3 is dedicated to a systematic comparison of recurrent and transformer
models. We discuss related work, summarize evaluation criteria, and provide an in-depth
analysis of the translation outputs from a supervised, zero-shot and multilingual systems.
-->



## Chapter IV

#### Zero-Shot Neural Machine Translation


In this chapter, we present a novel zero-shot self-learning approach using multilingual
NMT. We demonstrate how zero-shot translation for language pairs without parallel training data can be attend by exploring a multilingual model or a pivoting-based approach. In
the next section (4.1), we begin by introducing our approach to improve zero-shot translation. In (4.2), we cover previous work on multilingual model for zero-shot translation,
pivoting-based approaches and semi-supervised learning for a scenario in which parallel
data are not available for model training, which leads us to motivate the adoption of our
self-learning approach. Then (4.3), we discuss our zero-shot NMT modeling approach,
which leverages semi-supervised learning to progressively improve zero-shot translation
directions via incremental learning.
The experimental settings (4.4), cover two zero-shot directions (Italian → Romanian
and Romanian → Italian) for which we compare the proposed approach against supervised NMT, zero-shot multilingual NMT, and pivot-based translation. We analyze the
results and sample translations to show the effect of our incremental learning approach.
Our experimental results are organized into two parts: first, we apply our approach by
leveraging N language directions, then, we probe a more difficult zero-shot translation
model, by simply reducing the number of language directions in the multilingual model.
Our final results (4.5), confirm that our zero-shot NMT model outperforms conventional
pivoting methods, up to matching the performance of a fully-trained bilingual system.


Resources: https://github.com/surafelml/improving-zeroshot-nmt



## Chapter V

#### Transfer Learning for Low-Resource NMT


In the previous chapter we saw that the zero-shot translation of zero-resource languages
can be improved using our incremental learning approach (train-infer-train). A problem
that remains open is improving the translation task of languages with small parallel data
(low-resource). Hence, in this chapter, we present our transfer-learning method across
NMT models employing a dynamic vocabulary. Our approach allows extending a pretrained model to new languages by adapting its vocabulary as long as new data becomes
available (i.e., introducing new vocabulary items that are not included in the pre-trained
model).
Based on the languages considered in the parent and child models, our approach is
examined in two settings. In the first setting the parent model is pre-trained using a
high-resource language pair (HRL). The parameter transfer mechanism is evaluated in
two scenarios: i) simply adapt the parent model to the new language pair and ii) continuously add new language data to progressively grow to an M-NMT system. Our experiments spanning five low-resource languages (LRL) with constrained data sizes (5k and
50k parallel segments) for the child model show a significant performance gain, ranging
from +3.85 up to +13.63 BLEU scores. In the second setting, the parent model is trained
on multilingual data, and the adaptation to the child model is done either using data of
a new language pair or by using more relevant data from other language pairs, based on
a language relatedness data selection criterion. 

Experiments show significant performance gains with the dynamic adaptation of a pre-trained M-NMT system over baseline
models; up to +17.0 BLEU with relevant data selection to the LRL, and +13.0 BLEU
even with zero LRL data. We show how our method outperforms current approaches,
such as massively multilingual models and data-augmentation on four LRL pairs.
In line with our motivation for the proposed approach, in the following sections, we
begin by discussing related work on transfer-learning, pre-trained model adaptation, dataselection, and data-augmentation. Then, we discuss our dynamic transfer learning approach for LRL in two sections, respectively describing the method and discussing our experimental results. 


Resource: https://github.com/surafelml/adapt-mnmt







## Chapter VI

#### NMT into Language Varieties

In this section, we investigate the problem of training NMT to translate into language varieties, assuming both labeled and unlabeled parallel texts. Both research and commercial
machine translation have so far neglected the importance of properly handling the spelling,
lexical and grammar divergences occurring among language varieties. Notable cases are
standard national varieties such as Brazilian and European Portuguese, and Canadian
and European French, which popular online machine translation services are not keeping
distinct. We show that an evident side effect of modeling such varieties as unique class
is the generation of inconsistent translations. We compare language variety-specific and
generic NMT baselines against multilingual NMT systems, exploiting manual as well as
automatic language variety labels. We show significant BLEU score improvements over
baseline systems when translation into language varieties is learned as a multilingual task
with shared representations.


We present systematic ways to approach NMT from English into four pairs of language varieties: Portuguese European (pt-EU) - Portuguese Brazilian (pt-BR), European
French (fr-EU) - Canadian French (fr-CA), Serbian (sr) - Croatian (hr), and Indonesian
(id) - Malay (ms)1
. For each couple of varieties, we assume to have both parallel text
labeled with the corresponding couple member, and parallel text without such information. Moreover, the considered target pairs, while all being mutually intelligible, present    
different levels of linguistic similarity and also different proportions of available training
data. For our tasks we rely on the TED Talks collection2
, used for the International
Workshop of Spoken Language Translation, and OpenSubtitles2018, a corpus of subtitles
available from the OPUS collection

Paper: [Neural Machine Translation into Language Varieties
](https://arxiv.org/abs/1811.01064) 




## Chapter VII

#### Controlling the Verbosity of NMT


In this section, we present two approaches to control the verbosity (output length) of a
NMT model. In the first approach, we augment the source side with a token representing a
specific length-ratio class, i.e. short, normal, and long, which at training time corresponds
to the observed ratio and at inference time to the desired ratio. In the second approach,
inspired by recent work in text summarization [146], we enrich the position encoding used
by the transformer model with information representing the position of words with respect
to the end of the target string.
We investigate both methods, either in isolation or combined, on two translation
directions (En→It and En→De) for which the length of the target is on average longer
than the length of the source. We report MT performance results under two training
data conditions, small and large, which show limited degradation in BLEU score and
n-gram precision as we vary the target length ratio of our models. We also run a manual
evaluation which shows for the En→It task a slight quality degradation in exchange of a
statistically significant reduction in the average length ratio, from 1.05 to 1.01.


Paper: [Controlling the Output Length of Neural Machine Translation
](https://arxiv.org/abs/1910.10408)




<!--

## Chapter VIII

### Conclusion and Future Works


### References
TODO
-->


