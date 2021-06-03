# END2_Assignment5
### Before anything else, a note on file names
**5_1** series of note books are on original data (no augmentation), 5_1b series on original data bidirectional model. <br/>
**5_2** series was suppposed to be with augmented data. But looking at the results from the previous models, I decided to go only with LSTM bidirectional. <br/>
So, **5_2b_finalb** is the only one (with augmented data) in 5_2 series.<br/>
**dataset_gen** is the notebook which collects the SST data, augments it, and stores it by pickling <br/>
**trainset_new.pkl, testset.pkl, valset.pkl** are the files which are used in 5_2 series. <br/>
**test_sent.pkl** is the file which has the test set of sentences out of which 10 are randomly chosen to get the sentiments.

### Background
In this assignment we were asked to build a sentiment classifier for Stanford Sentiment data and achieve a 60% validation accuracy.
### Approach
The dataset was thoroughly studied, with a lot of confusion about the number of classes ( 5 or 25). Then finally a go ahead was given for 5 classes. A look at the distribution of classes in the training set revealed that it was an imbalanced data set with the distribution as shown below:
![image](https://user-images.githubusercontent.com/82941475/120589588-b2be9c80-c456-11eb-8bc3-cc5d444ae2f5.png)
So it was decided, that should the need to augment the dataset arises, it will be done to make it a balanced data set.
### Initial experiments
Initially RNN, GRU and LSTM models were built and tested with hyperparameters as given in the table below:
|Hyper parameter| Value|
|---------------|------|
|Size of Vocab  | No of words in the text|
|Embedding Dimension| 500|
|No. of Hidden Nodes| 100|
|No. of output Nodes|5|
|No. of Layers| 3|
|Dropout| 0.2|

### Further Refinements
But as the desired accuracy is way above the achieved accuracy, bidirectional RNN, GRU and LSTM were built, keeping other parameters same. 
Still the desired validation was a distant dream. So the dataset was augmented using Back translation, Random Delete and Stopword Removal.
Synonym replacement was not tried as back translation is supposed to do something similar. 
After the dataset was augmented, now there were 10224 training set examples instead of initial 8544.
Looking at the validation scores,achieved earlier, I decided to go ahead with LSTM birectional with augmented dataset.
Also looking at the results of training accuracy, which was going as high as upto 94%, it was decided to use regularisation. I chose L2 regularisation as it is known to give better results. Lambda was kept at 0.001,( after trying out few values like 0.01, 0.02, 0.05, 0.001, 0.002 and 0.005).
### Final results
The various values of validation accuracies achieved were shown below:
![image](https://user-images.githubusercontent.com/82941475/120592608-c6b8cd00-c45b-11eb-941d-eca009f6235f.png)


### Sample 10 Sentences randomly chosen from test set and their sentiments
|Sentence| Sentiment|
|-------- |-------------|
|Well-shot but badly written tale set in a future ravaged by dragons . |  Very Positive|
|Elicits more groans from the audience than Jar Jar Binks , Scrappy Doo and Scooby Dumb , all wrapped up into one . |  Negative|
|The year 's happiest surprise , a movie that deals with a real subject in an always surprising way . |  Positive |
|... ambition is in short supply in the cinema , and Egoyan tackles his themes and explores his characters ' crises with seriousness and compassion . |  Positive|
|What really surprises about Wisegirls is its low-key quality and genuine tenderness . |  Positive|
|A splendid entertainment , young in spirit but accomplished in all aspects with the fullness of spirit and sense of ease that comes only with experience . |  Positive|
|Almost every scene in this film is a gem that could stand alone , a perfectly realized observation of mood , behavior and intent . | Positive|
|Too sincere to exploit its subjects and too honest to manipulate its audience . | Negative |
|At heart the movie is a deftly wrought suspense yarn whose richer shadings work as coloring rather than substance . |  Positive|
|Although based on a real-life person , John , in the movie , is a rather dull person to be stuck with for two hours . | Positive |

### Further Discussion
As can be seen from the graph, highest validation accuracy achieved is 37.25.
Although it is much below the expected level, it is the maximum I could achieve under the given time constraints and my first time experiments with text data.
It can be seen, that even LSTM, bidirectional, (the model with highest accuracy) is highly incapable of capturing the sentiments of longer sentences. So further improvements could be various: <br/>
Choosing a different tokenizer (may be BERT)<br/>, 
doing some preprocessing and removing special characters etc. from whole of dataset,<br/>
or using phrases instead of complete sentences.<br/>
Well so far from my side in this assignment.
### Group Members
Ritambhra Korpal<br/>
Chaitanya Vanapamala <br/>
Pralay Ramteke <br/>
Palavai <br/>

