## USAGE

### Required
- CoNLL skeleton files in which the words are anonymized (one file for each conversation/thread, provided in ``conll_skeleton``)
- files with token differences to re-create the tokenization (one file per tweet, provided in ``diff``)
- text files containing the message of each tweet. The tweets can be found and downloaded via their Tweet ID (all IDs are listed in ``tweet_ids.txt``).

### Make CoNLL-format files

After downloading all the tweets via their Tweet IDs, the text of each tweet should be saved in an individual text file, with the Tweet ID as the name and the .txt extension (e.g. ``0123456789.txt``).

 Example tweet: ``This is just a test. Hi Twitter!``

The texts have to be tokenized on spaces (only spaces, not on punctuation etc.), with one token per line. A file should look like this:

 ```
 This
 is
 just
 a
 test.
 Hi
 Twitter!
 ```

If a tweet is no longer available, no file should be created (not even an empty one); the words from this tweet will stay anonymized.

**Note:** Some tweets contain unusual characters like zero-width spaces, which make the spacing invisible. At those spaces, words should separated just like at visible spaces.
Specifically, in the tweet with ID ``950216535125082112``, the tokenized version of ``*** I can'tJks ***`` should be

```
***
I
can't
Jks
****
```

As a final step, running ``python make_conll.py <PATH TO TWEET TEXT FILES>`` will create the CoNLL files in ``conll``.


### The CoNLL format

The CoNLL format is inspured by the original CoNLL-2012 format with some additional annotations.

```
COLUMN	CONTENT
0 		Thread ID
1 		Thread number
2 		Token number in sentence
3 		Token
4 		POS tag
5 		Parse info
6 		Speaker/User handle
7 		Representative mention
8 		Semnatic class
9 		NP form/reference type
10		Coreference ID
11		Clause boundary
12		lowest-level NP boundary
13		highest-level NP boundary
14		grammatical role
15		genericity
16		[Tweet number in thread]_[sentence number in tweet]_[token number in sentence]
```
