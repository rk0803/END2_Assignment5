# END2_Assignment5
### Before anything else, a note on file names
*5_1* series of note books are on original data (no augmentation), 5_1b series on original data bidirectional model. 
*5_2* series was suppposed to be with augmented data. But looking at the results from the previous models, I decided to go only with LSTM bidirectional. 
So, *5_2b_finalb* is the only one (with augmented data) in 5_2 series.
*dataset_gen* is the notebook which collects the SST data, augments it, and stores it by pickling
*trainset_new.pkl, testset.pkl, valset.pkl* are the files which are used in 5_2 series.
*test_sent.pkl* is the file which has the test set of sentences out of which 10 are randomly chosen to get the sentiments.

## next
 highest validation accuracy achieved. 
Although it is much below the expected level, it is the maximum I could achieve under the given time constraints and my first time experiments with text data.
