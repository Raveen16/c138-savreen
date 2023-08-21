A Bag Of Words is a representation of text that shows the occurrence of words in a sentence.

Two things are required for creating BoW. 
A vocabulary of known words. This is given by stem_words 
and array to represent the BoW representation of the sentence.

Start creating Bag Of Words by following these steps:
1. Define an empty list by the name training_data.
2. Define number_of_tags by finding the length of classes list.
3. Define an array of zeros by name labe ls. Labels will store the corresponding tag of the sentence.

# code
training_data = []
number_of_tags = len(classes)
labels = [0]*number_of_tags


To create Bag Of Words apply a for loop to word_tags_list. 
Each element is named as word_tags.
● For each element we’ll create an array of zeros and ones.
● Define an empty array by name bag_of_words.
● Also, define pattern_words as the first index of word_tags.
● Apply a for loop to pattern_words to find their stem words.
● Then if these words are present in the stem words, 1 is appended in bag_of_words else 0 is appended.
● Print bag_of_of words to check the output.


# Create bag od words and labels_encoding
for word_tags in word_tags_list:
        
        bag_of_words = []       
        pattern_words = word_tags[0]
       
        for word in pattern_words:
            index=pattern_words.index(word)
            word=stemmer.stem(word.lower())
            pattern_words[index]=word  

        for word in stem_words:
            if word in pattern_words:
                bag_of_words.append(1)
            else:
                bag_of_words.append(0)
        print(bag_of_words)



Creating label_encoding:
1. label_encoding list will have all labels initially as an array of zeros. 
For four tags it will be initially [ 0 0 0 0 ].

2. The word_tag_list has all the tags at index number 1. 
Extract these tags and save them in the tag variable.

3. The index of these tags is saved in the tag_index variable by using the index function with classes list and passing tag in it. (classes.index(tag) (0 to 3 for four tags)

4. Now, For each label, we will append 1 according to its index.
For e.g. the first label is goodbye so labels_encoding for it will be [ 1 0 0 0 ] and so on.

5. In the training_data append the bag_of_words of patterns with corresponding tags.

6. Print training_data[0] to check the data at first index (i.e. 0).


        labels_encoding = list(labels) #labels all zeroes initially
        tag = word_tags[1] #save tag
        tag_index = classes.index(tag)  #go to index of tag
        labels_encoding[tag_index] = 1  #append 1 at that index
       
        training_data.append([bag_of_words, labels_encoding])

print(training_data[0])



The next step is to create a function for training the chatbot.
Define a function preprocess_train_data.

Here The Bag of words is stored in the NumPy array train_x and 
the corresponding labels are stored in train_y. 
To train the model we need the data in the NumPy array. 
You can print the data at the first index of these arrays.

# Create training data
def preprocess_train_data(training_data):
   
    training_data = np.array(training_data, dtype=object)
    
    train_x = list(training_data[:,0])
    train_y = list(training_data[:,1])

    print(train_x[0])
    print(train_y[0])
  
    return train_x, train_y

train_x, train_y = preprocess_train_data(training_data)