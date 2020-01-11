

# 1. Preprocessing :

First, the html tags and special characters in the
collected documents are removed. And then, the
contents of the documents are segmented into
sentences. 


# 2. Creating training sentence sets :

Because the proposed system does not have
training documents, training sentence sets for
each category corresponding to the training
documents have to be created. We define
keywords for each category by hand, which
contain special features of each category
sufficiently. To choose these keywords, we first
regard category names and their synonyms as
keywords. And we include several words that
have a definite meaning of each category. The
average number of keywords for each category
is 3 (example : Total 141 keywords for 47 categories)

Next, the sentences which contain pre-defined
keywords of each category in their content
words are chosen as the initial representative
sentences. The remaining sentences are called
unclassified sentences. We scale up the
representative sentence sets by assigning the
unclassified sentences to their related category.
This assignment has been done through
measuring similarities of the unclassified
sentences to the representative sentences. 

# 3. Extracting and verifying representative
sentences :

We define the representative sentence as what
contains pre-defined keywords of the category in
its content words. But there exist error sentences
in the representative sentences. They do not
have special features of a category even though
they contain the keywords of the category. To
remove such error sentences, we can rank the
representative sentences by computing the
weight of each sentence as follows:

>  Word weights are computed using Term
Frequency (TF) and Inverse Category Frequency
(ICF) 

    >>  (1) The within-category word frequency(TFij),
        TFij = the number of times words occurs in the jth category 
    >> (2) In Information Retrival, Inverse Document
        Frequency (IDF) are used generally. But a
        sentence is a processing unit in the
        proposed method. Therefore, the document
        frequency cannot be counted. Also, since
        ICF was defined by Cho K. et al. (1997)
        and its efficiency was verified, we use it in
        the proposed method. ICF is computed as follows:
        ICFi = log(M) - log(CFi) , where CFi
        is the number of categories that contain ti
        , and M is the total number of categories.

    >> The combination (TFICF) of the above ①
        and ②, i.e., weight wij of word ti in jth
        category is computed as follows:
         (3)
       $Wij = TFij * ICFi$
           $= TFij *  (log(M) - log(CFi))$


> Using word weights (wij) computed in 1), a
sentence weight (Wij) in jth category are
computed as follows:
wij = w1j + w2j + .... wij / N
where N is the total number of words in a
sentence.

> The representative sentences of each category
are sorted in the decreasing order of weight,
which was computed in 2). And then, the top
70% of the representative sentences are selected
and used in our experiment. It is decided
empirically.
