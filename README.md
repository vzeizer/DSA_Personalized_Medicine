# Dataset Description

In this competition you will develop algorithms to classify genetic mutations based on clinical evidence (text).

There are nine different classes a genetic mutation can be classified on.

This is not a trivial task since interpreting clinical evidence is very challenging even for human specialists. Therefore, modeling the clinical evidence (text) will be critical for the success of your approach.

Both, training and test, data sets are provided via two different files. One (training/test_variants) provides the information about the genetic mutations, whereas the other (training/test_text) provides the clinical evidence (text) that our human experts used to classify the genetic mutations. **Both are linked via the ID field.**

Therefore the genetic mutation (row) with ID=15 in the file training_variants, was classified using the clinical evidence (text) from the row with ID=15 in the file training_text

Finally, to make it more exciting!! Some of the test data is machine-generated to prevent hand labeling. You will submit all the results of your classification algorithm, and we will ignore the machine-generated samples. 

File descriptions
- training_variants - a comma separated file containing the description of the genetic mutations used for training. Fields are ID (the id of the row used to link the mutation to the clinical evidence), Gene (the gene where this genetic mutation is located), Variation (the aminoacid change for this mutations), Class (1-9 the class this genetic mutation has been classified on)
- training_text - **a double pipe (||) delimited file** that contains the clinical evidence (text) used to classify genetic mutations. Fields are ID (the id of the row used to link the clinical evidence to the genetic mutation), Text (the clinical evidence used to classify the genetic mutation)
test_variants - a comma separated file containing the description of the genetic mutations used for training. Fields are ID (the id of the row used to link the mutation to the clinical evidence), Gene (the gene where this genetic mutation is located), Variation (the aminoacid change for this mutations)
test_text - **a double pipe (||) delimited file that contains the clinical evidence (text) used to classify genetic mutations**. Fields are ID (the id of the row used to link the clinical evidence to the genetic mutation), Text (the clinical evidence used to classify the genetic mutation)
submissionSample - a sample submission file in the correct format

## Results

First of all, 'Genes' descriptions having more than 10 instances are filtered, because these must have significant, yet small, instances. 

### Bar plot of class's instances

In the next figure, it is shown the distribution of instances for each class in the dataset, from which one can notice that the classes *3,9 and 8* have a relatively small number of instances. Therefore, it is expected that the model does not classify such classes, because it did not have many instances in training.

Here, there has been selected the classes having more than 300 instances, which are *1,2,4,6,7*.

![logo](images/1_class_counts.png)

### Histogram of words

The following figure shows a histogram of words present in the dataset's instances, from which there has been selected sentences instances having more than 1000 words and less than 2000, in order to reduce computational power.

The "Text" column was also the last 200 characters. This approach was also performed because the computational power to analyze this data was optimized.

Furthermore, stopwords and punctuations were removed, the text was lemmatized, which means...
And the stemming procedure was performed in order to...

Moreover, in order to perform useful feature engineering, two variables related to the length of sentences were created for the features "Gene" and "Variation".


![logo](images/2_wordcount_hist.png)

### Variation feature words distribution

The following figure shows a histogram of the number of words in "Variation" attribute, and it can be clearly seen that the majority of the sentences has 1 word, much less has 2 words, and a very small proportion can reach up to 6 words in a sentence instance. In order to dela with the dataset containing the "Variation" attribute, this data was simplified in order to contain only sentences having 1 word.


![logo](images/3_variationlen.png)


### Machine Learning Modeling

The two datasets containing "Genes" and "Variations" were merged on "ID", and a machine learning modeling was developed. The TF-IDF Vectorizer was applied and the data was split on training and testing sets, and a Random Forest Classifier was fitted and tested. An overall accuracy of 0.6 on the testing set point out that a reasonable modeling result was obtained, despite the small number of instances for many classes in the dataset and, as well, a lot of simplifications were performed in order to improve usage of computational resources available. 


![logo](images/4_modelresults.png)

### Cloud of Words

The following figure shows a cloud of words containing the "most useful" words in this dataset


![logo](images/5_wordscloud.png)

## Summary of Key Findings

1. Dataset Characteristics and Preprocessing:

Classification Task: The goal is to classify genetic mutations into 9 classes based on clinical text evidence.

- **Data Structure**:

Two datasets: training_variants (genetic mutation information) and training_text (clinical text).
Linked via the ID field.
training_text and test_text files are double pipe (||) delimited.

- **Class Imbalance**:

Classes 3, 8, and 9 have significantly fewer instances than other classes, which likely impacts model performance for those classes.
Analysis focused on classes 1, 2, 4, 6, and 7, which have more than 300 instances.

2. **Text Preprocessing**:

Text length was limited to sentences between 1000 and 2000 words.
The last 200 characters of the "Text" column were selected, likely for computational efficiency.
Stopwords and punctuation were removed.
Lemmatization and stemming were performed.
Feature engineering produced sentence length variables for "Gene" and "Variation".

3. **Variation Simplification**:

The "Variation" feature primarily consists of single-word entries.
Data was simplified to include only single-word variations.
Gene filtering:
Genes with more than 10 instances were filtered.

4. **Modeling and Results**:

Model: Random Forest Classifier.
Feature Extraction: TF-IDF Vectorizer.
Data Splitting: Training and testing sets were used.
Performance: Achieved an overall accuracy of 0.6 on the testing set.

5. **Limitations**:

Class imbalance negatively impacted performance.
Computational resource limitations led to significant data simplification.
Visualizations:

6. **Class Distribution Bar Plot**: 

Shows the imbalance in class representation.
Word Count Histogram: Illustrates the distribution of word counts in the text data.
Variation Length Histogram: Shows that most "Variation" entries are single words.
Model Results Chart: Displays the performance of the Random Forest Classifier.
Word Cloud: Highlights the most frequent and "useful" words in the dataset.


## Real-world usage scenario

The analysis of genetic mutations and their classification based on clinical text evidence has significant real-world applications, particularly in the fields of medicine and biotechnology. Here are some key usages:

1. Personalized Medicine and Cancer Treatment:

- **Targeted Therapies**:

Identifying specific genetic mutations allows doctors to tailor treatments to individual patients. For example, knowing the exact mutation in a cancer tumor helps select the most effective drugs.
This approach, known as personalized or precision medicine, improves treatment outcomes and reduces side effects.

- **Risk Assessment**:

Classifying mutations can help assess a patient's risk of developing certain diseases, particularly cancers.
This allows for earlier detection and preventive measures.

- **Drug Development**:

Understanding the relationship between genetic mutations and disease helps researchers develop new drugs that target specific mutations.

2. Genetic Disease Diagnosis and Management:

- **Rare Disease Diagnosis**:

Many rare genetic diseases are caused by specific mutations. Analyzing genetic data and clinical text helps diagnose these conditions.
This is crucial for providing appropriate care and support to patients.

- **Genetic Counseling**:

Classifying mutations helps genetic counselors assess the risk of inherited diseases in families.
This allows them to provide informed advice to individuals and families.

3. Research and Development:

- **Understanding Disease Mechanisms**:

Analyzing genetic mutations helps researchers understand the underlying mechanisms of diseases.
This knowledge is essential for developing new treatments and preventive strategies.

- **Biotechnology Applications**:

Genetic mutation analysis is used in various biotechnology applications, such as gene editing and gene therapy.
It helps ensure the accuracy and safety of these technologies.

4. Clinical Decision Support:

- **Automated Interpretation of Clinical Data**:

Machine learning models can help automate the interpretation of complex clinical data, including genetic information.
This supports clinicians in making informed decisions.

- **Improving Efficiency**:

Automating the classification of genetic mutations can save time and resources in clinical settings.


## MIT License

Copyright (c) [2025] [Dr. Vagner Zeizer Carvalho Paes]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.



