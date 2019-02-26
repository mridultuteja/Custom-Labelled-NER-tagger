# Custom Label Stanford CoreNLP NER

### Stanford NER
Stanford NER is a Java implementation of a Named Entity Recognizer. Named Entity Recognition (NER) labels sequences of words in a text which are the names of things, such as person and company names, or gene and protein names. It comes with well-engineered feature extractors for Named Entity Recognition, and many options for defining feature extractors. Included with the download are good named entity recognizers for English, particularly for the 3 classes (PERSON, ORGANIZATION, LOCATION), and we also make available on this page various other models for different languages and circumstances, including models trained on just the CoNLL 2003 English training data.

See [Stanford NER](https://nlp.stanford.edu/software/CRF-NER.shtml)

Custom Labelling for NER is the process of creating your own Data and using it to train your own trained model with the help of Stanford's Core-NLP.

For Some privacy Reasons I am unable to give all the dataset but only a 100 examples to give the gist of process.

First Execute the preprocessing file "Custom NER Preprocessor.ipynb"

Create a prop.txt file in train folder inside stanford-ner-tagger folder and write code below.

```
trainFile = train/output.tsv
serializeTo = dummy-ner-model-french.ser.gz
map = word=0,answer=1

useClassFeature=true
useWord=true
useNGrams=true
noMidNGrams=true
maxNGramLeng=6
usePrev=true
useNext=true
useSequences=true
usePrevSequences=true
maxLeft=1
useTypeSeqs=true
useTypeSeqs2=true
useTypeySequences=true
wordShape=chris2useLC
useDisjunctive=true
```

then to train on newly created data 

```sh
$ cd stanford-ner-tagger/
$ java -cp "stanford-ner.jar:lib/*" -mx4g edu.stanford.nlp.ie.crf.CRFClassifier -prop train/prop.txt
```

now access the newly trained model using test.ipynb

