# Classification Category of PubMed Articles
## Introduction
PubMed is a free digital full-text database of specialized scientific papers in the natural and biomedical sciences developed by the US National Library of Medicine (NLM). Not all articles contain abstracts, making it difficult for researchers to find the intended article. In this middle project, the predictions of the accuracy will be conducted in five labels target of PubMed articles using two features extraction (count vectorizer and n-grams) and two features weighting (Term Frequency(TF) and Term Frequency-Inverse Document Frequency(TFIDF)) with three experimental scenarios. Classification uses two machine learning methods, logistic regression and linear support vector machine (Linear SVM). The results show that the level of accuracy is quite high. However, the number of articles that do not contain abstracts is an obstacle that affects the accuracy of the results in the classification.

## Method
In general, the system that will make in this study is a system that can predict the accuracy of keywords in five types of articles as covid-19 articles, cancer articles, article genomes, article viruses, and article vaccines. This system uses Naive Bayer multinomial in predicting accuracy. The general overview of the system to be made in this study is as follows.
<p align="center">
  <img src="https://github.com/raniavirdas/Text-Mining-First-Project/assets/91519107/a019f735-9239-4737-924b-8c418e6e3396" alt="Method Middle Project Asia University">
</p>

Scenario whole system is as follows:
- Five data types are taken from the PubMed website, https://pubmed.ncbi.nlm.nih.gov/, namely data on covid-19, cancer, viruses, vaccines, and genomes. The five data are taken in txt format. Then pre-processing is carried out to extract the five txt files into five excel format files; after that, combine the five extracted excel files into one excel file, combine the title and abstract, put it in a new column, and define the target name and target label.
- Perform pre-processing again on the data that the needs of the classification have compiled. This pre-processing consists of stopword removal, normalization, and lemmatization. The results will be saved in CSV format for classification at a later stage.
- The classification process will be run after going through the feature selection process. Feature selection plays an essential role in classifier implementation. The feature models that will be used are bow features and n-gram features.
- Feature extraction from BoW into vector uses Count-Vectorizer and TF-IDF-Vectorizer algorithms to perform feature weighting. Count-Vectorizer converts BoW to vector. The way it works is to extract the sentences in the document into a single word that composes them and count how often each word is present in each document. Each document is represented by a vector whose size is equal to the number of vocabulary words, and the entries in the vector for a given document indicate the number of words in that document. Meanwhile, term frequency (TF) is the ratio of the number of words in the document, and IDF is the occurrence of words in the entire database(Khomsah & Aribowo, 2020). Thus, Term Frequency Inverse Document Frequency(TFIDF) is a weighting method that combines the TF and IDF methods. This definition follows Salton’s, IDF represents term specificity, it is expected to improve the precision. Salton proposed combining term frequency and IDF to weight terms and showed that their product gave better performance(Tokunaga & Iwayama, 1994).
- The data is then divided into training and testing data using k-folds cross-validation, classified using logistic regression and SVM. Performance classification accuracy was assessed using a confusion matrix.

## Result and Discussion 
### 3.1	Dataset
The data used was obtained from the website https://pubmed.ncbi.nlm.nih.gov/; the five critical data were searched by entering related keywords such as covid-19, vaccine virus, genome, and cancer. Each of the five data contains 10000 citations and is taken in txt format. The total number of citations is 50000 citations. Each data contains keywords such as PMID, title, and abstract. In order to make writing more manageable, the title is shortened to TI, and the abstract is shortened to AB. In the five data, not all data contains abstracts; some data in each keyword does not have abstracts and will be stated as NaN information. Then, the data is given an additional column containing keyword labels (covid-19, cancer, genome, vaccine, and virus). Then the five data are extracted into excel format, which will later be merged to be converted into CSV format.
### 3.2	Experiment

In achieving the goal, an experiment will be designed; an experiment will be designed. The experimental scenario is as follows:
- Experiments using logistic regression and linear SVM classification methods with Count Vectorizer feature extraction and features weighting Term Frequency(TF)
This experiment was carried out by dividing the dataset by differentiating the composition of the data training parameters and data testing. The training data used is 67% and the testing data used is 33%. Then perform features extraction with BoW features using the count vectorizer library. Then, the features extraction is used in linear logistic regression and linear SVM models with features weighting Term frequency (TF). In the first and second classifications, logistic regression and support vector machine (SVM), the penalty parameter is l2 with a C of 0.1. Count vectorizer uses K-Folds with k = 5. It aims to determine the mean count vectorizer accuracy and mean test accuracy, shown as follows.

<p align="center">
  <img src="https://github.com/raniavirdas/Text-Mining-First-Project/assets/91519107/a8bb4946-fb9a-452d-8ddc-86e36ee529e2" alt="results of 1st scenarios">
</p>

The results above show that using the count vectorizer feature extraction in the logistic regression classification produces greater accuracy than the linear SVM classification. Even so, the average accuracy of the two is not much different, only 0.1% adrift.
- Experiments using logistic regression and linear SVM classification methods with Count Vectorizer feature extraction and features weighting Term Frequency-Inverse Document Frequency(TFIDF)
This experiment was also carried out by dividing the dataset by distinguishing between training data parameters and test data configurations. The training data used is 67%. 33% of the data used is used for data testing. Then use the count vectorizer library to perform feature extraction on the BoW feature. Slightly different from the above classification, feature extraction will be used in linear logistic regression and linear SVM models with feature weighting Term Frequency-Inverse Document Frequency(TFIDF). The parameters used for classification using TFIDF are the same as the parameters used for classification using TF. Likewise, the value of K is used in K-Folds. It aims to determine the average accuracy and the average test accuracy of the count vector. The results are shown below.

<p align="center">
  <img src="https://github.com/raniavirdas/Text-Mining-First-Project/assets/91519107/9cf39df5-764c-460b-ad78-76b7a3c01408" alt="results of 2ndt scenarios">
</p>

The results obtained have better causation than the classification using features weighting TF. According to the literature, TFIDF will provide better performance. the difference in accuracy between logistic regression and linear SVM is not far apart, and the linear SVM model produces better test accuracy than logistic regression.
- Experiments using logistic regression and linear SVM classification methods with n-gram feature extraction and features weighting Term Frequency-Inverse Document Frequency(TFIDF)
This third experiment was also carried out by dividing the dataset by distinguishing between training data parameters and test data configurations. The training data used is 67%. 33% of the data used is used for data testing. Unlike the other two, in performing feature extraction using the count vectorizer library, this experiment uses the n-grams feature. The feature extraction will be used in a linear SVM model with inverse document frequency (TFIDF) feature weighting. In this third experiment, the parameters used to include.

<div align="center">
  
|Confusion Matrix|Support Vector Machine| 
|:-|:-|
|Accuracy|0.8324|
|Precission|0.895|
|Recall|0.8324|
|F1 Score|0.843|
  
</div>

From the table above, the accuracy or correct prediction ratio with the overall data is about 83.24%. The precision or the ratio of correct positive predictions compared to the overall positive predicted outcome is 89.5%. It means 89.5% of each label matches the title and abstract of the total target labels predicted. The recall or the ratio of correct positive predictions compared to the correct positive data is 83.24%. There are 83.24% of each target label that matches the title and abstract of the actual target labels.
Meanwhile, the F1 score or the comparison of the average precision and recall that is weighted is around 84.3%. The evaluation of the obtained matrix does not reach 90%. We assume that this is because only stopword removal, normalization, and lemmatization are performed during the pre-processing, so the classification cannot be maximized. We could not do normalization with the parameters.
In addition, we assume that the evaluation of the obtained matrix does not reach 90% due to the low percentage of precision and recall on vaccine labels, resulting in a low percentage of F1.

<p align="center">
  <img src="https://github.com/raniavirdas/Text-Mining-First-Project/assets/91519107/1fd44663-d1e1-4bc5-9dc6-9542306f2c93" alt="classification report of 3rd scenarios">
</p>

56% of vaccine labels match the title and abstract of all predicted target labels from the picture above. It is due to a large number of articles with vaccine labels that do not have an abstract. The percentage of articles that do not have an abstract on the vaccine label is 35.15% or 3515 articles out of 10000 labeled with vaccines. It is evidenced in the following figure.

<p align="center">
  <img src="https://github.com/raniavirdas/Text-Mining-First-Project/assets/91519107/aff076b9-e4dc-4db4-b209-7d9f8f8d6292" alt="# of no abstract in vaccine articles">
</p>

## Conclusion
the predictions of the accuracy of five labels target of PubMed articles using two features extraction(count vectorizer and n-grams) and two features weighting(Term Frequency(TF) and Term Frequency-Inverse Document Frequency(TFIDF)) with three experimental scenarios.
The first experimental scenario uses the logistic regression method and linear SVM classification with CountVectorizer feature extraction and features weighting term frequency (TF) and produces an accuracy with the logistic regression method of 82.87% and 82.70% with the SVM method.
The second experimental scenario uses logistic regression and linear SVM methods with Count Vectorizer feature extraction and features weighting Term frequency-inverse document frequency (TFIDF) and produces an accuracy with logistic regression method of 83.07% and SVM of 83.10%.
The third experimental scenario uses logistic regression and linear SVM methods with n-gram feature extraction and features weighting Term frequency-inverse document frequency (TFIDF) and produces an accuracy of 83.24%. The accuracy is below 90% due to human error, such as only doing pre-processing in the form of removal of stopwords, normalization, and lemmatization, and as many as 35.15% of the 10000 articles labeled with vaccines do not have abstracts. As a result, the F1 value for vaccine labels is very low compared to other F1 values.

## References
- Khomsah, S., & Aribowo, A. S. (2020). Model Text-Preprocessing Komentar Youtube Dalam Bahasa Indonesia. Jurnal RESTI (Rekayasa Sistem Dan Teknologi Informasi), 4(4), 648–654.
- Prediction in Medicine – The Data Mining Algorithms of Predictive Analytics. (2015). Practical Predictive Analytics and Decisioning Systems for Medicine: Informatics Accuracy and Cost-Effectiveness for Healthcare Administration and Delivery Including Medical Research, 239–259. https://doi.org/10.1016/B978-0-12-411643-6.00015-6
- Tokunaga, T., & Iwayama, M. (1994). Text categorization based on weighted inverse document frequency. Technical Report Tokyo Institute of Technology., 5–31.
- Van Baren, J. (2012). Relating content to the user. In Academic and Professional Publishing. Woodhead Publishing Limited. https://doi.org/10.1016/b978-1-84334-669-2.50011-1
