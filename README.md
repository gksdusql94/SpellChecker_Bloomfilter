# 🖥️ Bloom Filter Project for Spell Checking

## 📊 Project Overview
This project demonstrates the usage of Bloom Filters for efficient spell-checking. A Bloom Filter is a space-efficient probabilistic data structure used to test whether an element is a member of a set. It is faster and requires much less space compared to other data structures like lists and sets. However, it comes with the trade-off of possible false positives.

In this project, we compare the performance of a Bloom Filter with a traditional list and set for spell-checking tasks using a large dictionary of words.

## 📁 Dataset
NLTK Words Dataset: A list of English dictionary words is used as the dataset. This dataset contains 236,736 words, and each word is added to the Bloom Filter for membership testing.
Movie Reviews Dataset: The NLTK corpus movie_reviews is used to create a bag of words for positive and negative movie reviews. This data helps simulate real-world scenarios where a spell-checker is needed.

## 🚀 Key Features
- Memory Efficiency: Bloom filters use significantly less memory compared to Python sets and lists, making them ideal for memory-constrained applications.
- Performance Comparison: Benchmarking between Bloom Filter, list, and set for checking if a word exists in the dictionary.
- Time Complexity: Showcases the time efficiency of Bloom Filters for membership tests.

## 📋 Steps to Run the Project
1. Install the bloom_filter Library: Ensure you have the required package installed.
    ```bash
    !pip install bloom_filter
    ```
2. Download NLTK Data: Download necessary datasets from the NLTK corpus.
    ```bash
    import nltk
nltk.download('words')
nltk.download('movie_reviews')
    ```
3. Run the Code: Load the datasets and execute the Bloom Filter and comparison tests.

## 📈 Results
Memory Usage Comparison
- List: 2,055,512 bytes
- Bloom Filter: 48 bytes
- Set: 8,388,824 bytes
This demonstrates that the Bloom Filter uses significantly less memory compared to a list or set while providing efficient membership testing.

### Performance Comparison
Using the timeit command, we compare the time taken to check for the word "California" in a list, Bloom Filter, and set:

- List: 555 µs (average)
- Bloom Filter: 16.1 µs (average)
- Set: 54.9 ns (average)
While a Python set is the fastest for exact membership testing, the Bloom Filter offers a great trade-off between memory usage and performance, especially in large-scale applications.


## 🔑 Important Code
### Creating and Using a Bloom Filter

```python
from bloom_filter import BloomFilter

# Create a Bloom Filter
word_filter = BloomFilter(max_elements=236736)

# Add words to the filter
for word in word_list:
    word_filter.add(word)
```

### Memory Usage
```python
from sys import getsizeof

# Check the memory usage of different structures
print(f'Size of word_list: {getsizeof(word_list)} bytes')
print(f'Size of word_filter: {getsizeof(word_filter)} bytes')
print(f'Size of word_set: {getsizeof(word_set)} bytes')
```
### Performance Comparison
```python
# Time comparison between list, Bloom Filter, and set for membership testing
%timeit "California" in word_list
%timeit "California" in word_filter
%timeit "California" in word_set
```

### Spell Checker Function
This function checks the proportion of words from the movie reviews dataset that are not found in the dictionary (using Bloom Filter).

```python
def spell_check(review_words, dictionary):
    count = 0
    for word in review_words:
        if word not in dictionary:
            count += 1
    return count / len(review_words)

# Example usage:
result_ratio = spell_check(neg_reviews, word_filter)
print(f'Ratio of words not in the dictionary: {result_ratio}')
```

## 🔮 Future Work
- Extend the analysis to other server logs and integrate real-time monitoring.
- Implement machine learning models for predictive log analysis to identify potential issues in advance.
- Incorporate a user interface to provide real-time visual feedback.

