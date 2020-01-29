# 可読性

Good writing encompasses many aspects. Apart from concise content, your texts need a balanced mixture of long and short sentences. Furthermore you should refrain from too many complex and difficult words. Additionally, it is always good to make sure your paragraphs are not too long, use active voice, and structure your paragraphs accordingly.
良い文章というものには様々な側面があります。簡潔な内容だけでなく、長い文と短い文がバランスよく含まれていることも必要です。さらに、複雑で難しい単語を使いすぎないようにする必要もあります。そして、段落が長くなりすぎないこと、能動態を使うこと、各段落を状況に応じて構成することも大切です。

Since the development of text, humanity's creativity has brought forth many tips to good writing. While Zettlr provides you with the perfect environment to write in, thereby making sure the _legibility_ of your text is great, the _readability_ is something you need to take care of as well. Luckily, beginning with `1.4`, Zettlr has a tool for you: The **readability mode**.
文書というものが開発されて以来、人類の創造力により、良い文章を書くコツが生み出されてきました。Zettlrが完璧なライティング環境を提供してくれるので、文章の判別性(legibility)は非常に良いですが、可読性(readability)についても注意を向ける必要があります。幸いにも、Zettlr `1.4`で**可読性モード**が利用できるようになりました。

> Please note that the readability score is only one out of several measurables that can help you determine the ease of reading, but should not be taken to serious. If the readability algorithm highlights a sentence in deep red, this does not necessarily mean that you should rewrite the sentence. Rather, look at the context of the sentence, which the algorithm does not take into account, to determine the quality of a sentence. **We recommend to first write your text without the mode, and then only switching it on for some passages where you have a feeling they might be difficult to understand.**
> 可読性スコアは読みやすさを判断するための指標の一つに過ぎないので、あまり真剣に受け止めないでください。可読性アルゴリズムにより文章が真っ赤にハイライトされたとしても、その文章を書き直す必要はありません。むしろ、アルゴリズムでは考慮されない文のコンテキストを見て、良し悪しを判断してください。**最初は可読性モードをオフにして文章を書くことを推奨します。後から、読みにくいかもしれないと思った部分を確認するときだけオンにしてください。**

## What the Readability Mode does

In its shortest definition, the readability mode is a syntax highlighting mode for CodeMirror that calculates a basic score for each of your sentences, giving you a first impression of the readability of your texts. It highlights each of your sentences with a colour ranging from green to red, where green means that the sentence is easy to understand, while red means that the sentence is hard to understand.

The mode has four different algorithms at its disposal: The [Dale-Chall-formula](https://en.wikipedia.org/wiki/Dale%E2%80%93Chall_readability_formula), the [Gunning-Fog index](https://en.wikipedia.org/wiki/Gunning_fog_index), the [Coleman-Liau-index](https://en.wikipedia.org/wiki/Coleman%E2%80%93Liau_index), and the [Automated Readability index](http://www.readabilityformulas.com/automated-readability-index.php). These differ in what they estimate to be hard to understand writing, and in the "harshness" of the scores they give to sentences. Not all indices are a good choice for every text. You need to make sure to choose the algorithms wisely.

### The Dale-Chall

The Dale-Chall formula was created in the early days of educational research and was authored by Edgar Dale and Jeanne Chall. Its aim was to provide a measurable to determine the readability of texts for school children. It uses a list of 3.000 words that are easy to understand for American fourth-graders and gives a score that approximately ranges from 0 to 10, which roughly translates to the years of education needed to understand a text. That means: If a sentence receives a 10, you'd need a college degree to understand the text, while a sentence with a 1 could be understood by beginners.

**You should use the Dale-Chall index, if** you are writing texts for a broader audience, as the algorithm will give your text credits for short and concise sentences without pushing you to making sentences ridiculously short.

### The Gunning-Fog Index

Gunning-Fog has been created in the early days of tabloid and easy reading. In 1952, Robert Gunning was searching for a way to make the books and newspapers he was publishing measurable. The Gunning-Fog index therefore returns a score that correlates approximately with the years of formal education needed for a reader to understand a text. Still, being a businessman and therefore interested in a high dispersion of his publications, Gunning's algorithm tends to give high scores even to relatively easy to understand texts. If you cycle through the different algorithms, you will note that Gunning-Fog tends to paint everything ~~black~~ red.

**You should use the Gunning-Fog index, if** you want to write short advertisement texts (e.g. for websites) that cannot count on a basic intrinsic motivation to read.

### Coleman/Liau-index

With the plunge of computer prices, computer-aided statistics became a popular option to process huge amounts of data and spit out a meaningful measurable. The Coleman/Liau-index is from this era and is an algorithm that does not rely on syllable counts or lists with "difficult words". Therefore, the Coleman/Liau-index is extremely accurate in its implementation in Zettlr. As do the others, it gives a score that approximates the years of formal education needed to comprehend a sentence. Additionally, Coleman/Liau gives reasonable results and does not push you to writing short sentences necessarily.

**You should use the Coleman/Liau-index, if** you need an accurate measurement of the readability of any text. It does not go well with one-word-sentences, but will give understandable scores even to harder to understand texts.

### Automated Readability Index (ARI)

The Automated Readability Index follows en suite the Coleman/Liau, as it is a newer formula to calculate readability scores based on simple statistical analysis. It is the most "forgiving" of the algorithms and produces results that do not prompt you to re-write half of your text because of a red highlighting colour.

**You should use the Automated Readability Index, if** you are writing more demanding texts such as academic papers, as it will give lower scores even for some difficult sentences.

### A Note on "Difficult Words"

In its own implementation, Zettlr does not ship with a list of easy to comprehend words that the Dale-Chall requires. Instead, it uses a different approach. The list of easy to understand words differs from time to time and, obviously, from language to language. Therefore, Zettlr takes into account another measurable to determine words deemed difficult: Language variance.

Difficult words for Zettlr are defined as being longer than two times the standard deviation of the average word length. As Coleman and Liau have put it in their 1975 paper _A Computer Readability Formula Designed for Machine Scoring_, the length of words is a much better indicator for the difficulty of words than the number of syllables. Therefore, the algorithm can score sentences in any western script language, not only English. You can look up the algorithm explanation [on our readability feature page](https://zettlr.com/readability).

Additionally, Zettlr makes one more change to the algorithms: While all four algorithms were devised to be applied to full texts, the readability mode will take each sentence, one at a time, and therefore leave out their context. In general this approximates the difficulty of the sentence, but obviously may mark some sentences as green that are difficult to understand in their given context, while it will mark some sentences red that still fit into the given context.
