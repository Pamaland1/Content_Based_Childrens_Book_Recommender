# Building a Content-Based Children’s Book Recommender for Parents

This NLP project aims to make a solution to the bed-time story debacle: an application 
called StoryTime powered by topic modelling.  My favorite part of the day is reading picture 
books to my son, Storm, at bedtime. However, as this is a significant part of my free time 
engaged in reading the same books 1,000,000 times, I would love to find books that prioritized 
my interests, in addition to my child’s.

## Objective

Build a recommendation system for children’s picture books, that takes into account parent 
interests as well as children’s interest.

## Data Sources

I used the GoodReads Dataset, an e-book platform. Researchers provided three datasets - 
book, review, and interaction.  I used book data which had a book description and meta-data 
and review data which had user reviews.:

* [USCD Complete Goodreads Dataset Details](https://sites.google.com/eng.ucsd.edu/ucsdbookgraph/home)
* [Children's Books](https://drive.google.com/uc?id=1R3wJPgyzEX9w6EI8_LmqLbpY4cIC9gw4)
* [Children's Books Reviews](https://drive.google.com/uc?id=1908GDMdrhDN7sTaI_FelSHxbwcNM1EzR)

## Methodology: Topic Modelling
I processed the Review Data and Book Data in this way:
Review Data — Count Vectorizer and Standardization
Book Data — TFIDF Vectorizer with Non-negative Matrix Factorization

Using NLP, I applied NMF on the adjectives and nouns of the Book Description separately. 
The nouns provided mostly concrete topics like “farm animal” and “black and white” that 
informed features my son would be more interested in. The adjectives provided more abstract 
terms like “funny” or qualifying terms like “unique” that I would be more interested in. 
Using NMF as well as some more simple statistical methods, I was able to tease out several 
topics that could inform a recommendation system.  

I used a cosine similarity engine to find 
books to recommend that most closely matched topics selected by users.

## Test Cases

I created 3 test cases to see if my recommendation engine worked. My test cases were: 
my son’s preferences (Kid’s), my preferences (Mom’s), and my husband’s preferences (Dad’s). 
We each have our own personal interests and in my opinion, the engine worked remarkably well:

### Test Case 1: Kid

Storm’s primary interest is in animals, he love’s the storyline and is a real jokester, 
so these top 3 books recommended by my system - 
* [XO, OX, a Love Story](https://www.amazon.com/XO-OX-Story-Adam-Rex/dp/1626722889) 
* [Click, Clack, Moo Cows That Type](https://www.amazon.com/Click-Clack-Cows-That-Type/dp/0689832133/ref=sr_1_1?crid=1LMXRGBA4D3ZT&dchild=1&keywords=click+clack+moo+cows+that+type&qid=1586362923&s=books&sprefix=click+clack+moo%2Cstripbooks%2C648&sr=1-1)
* [The Mitten](https://www.amazon.com/Mitten-Jan-Brett/dp/0399231099/ref=sr_1_1?dchild=1&keywords=the+mitten&qid=1586362976&s=books&sr=1-1)  

Based on their covers, these seem to pinpoint Storm's 
topics pretty well — animals, humor, adventure.

### Test Case 2: Mom

I tend to live in a more abstract space in my mind, so my topics were in relation to larger 
themes like family, and exceptional artwork. I also prefer books that are longer so that 
I can determine the stopping point rather than my son insisting we get to the end of shorter books. 
The top 3 books recommended by my system were - 
* [This Is Me: A Story of Who We Are and Where We Came From](https://www.amazon.com/This-Me-Story-Where-Came/dp/0761180117/ref=sr_1_1?dchild=1&keywords=this+is+me+jamie+lee+curtis&qid=1586363197&s=books&sr=1-1)
* [Before Morning](https://www.amazon.com/Before-Morning-Joyce-Sidman/dp/0547979177/ref=sr_1_1?dchild=1&keywords=before+morning&qid=1586363238&s=books&sr=1-1)
* [Butterfly Park](https://www.amazon.com/Butterfly-Park-Elly-MacKay/dp/0762453397/ref=sr_1_1?dchild=1&keywords=Butterfly+Park&qid=1586363327&s=books&sr=1-1)  

At first glance, the recommendations are spot on with fanciful illustrations and whimsical titles. 
However, they are not long books. This had to do with the fact that I limited my dataset to 500 of 
the most popular titles for this proof of concept, and longer books unfortunately did not make the cut.

### Test Case 3: Dad

My husband is concerned about my son’s social skills and ability to navigate school and life. 
He is also interested in the books being short, unique, and adventure driven. 
The top 3 books recommended by my system were - 
* [Mr. Lincoln’s Way](https://www.amazon.com/s?k=Mr.+Lincoln%E2%80%99s+Way&i=stripbooks&ref=nb_sb_noss),
* [If My Moon Was Your Sun](https://www.amazon.com/s?k=if+my+moon+was+your+sun&i=stripbooks&ref=nb_sb_noss_2),
* [Spork](https://www.amazon.com/Spork-Kyo-Maclear/dp/1771388056/ref=sr_1_1?dchild=1&keywords=spork&qid=1586363458&s=books&sr=1-1)  


The recommendations certainly focus on educational themes, the number one match — Mr. Lincoln’s 
Way — is a book about how to navigate bullying in schools and is actually part of many common 
core curriculums. The artwork is ok but not a priority in this first recommendation. The second 
title is about a boy who kidnaps his Grandpa from a nursing home to take him on an adventure. 
The last is about a spork who just wants to be accepted into the cutlery family even though 
he is a bit different.

## Conclusion
This recommendation system works like a charm. I would love to see it folded into a flask 
app and trained on the entire goodreads illustrated book dataset. This will be my task 
post-bootcamp, as I’m sure this engine will be useful to mama’s and dada’s everywhere - 
and could be super useful in the current Covid pandemic we are experiencing.

## Future Considerations
One challenge with content-based recommendation systems is that you can tend to get the 
same responses if you choose the same topics, so eventually, it may make sense to marry 
this with a collaborative recommendation system that learns from user interactions. 
Alternatively, having an encyclopedic amount of topics, and a max choice of three topics 
per query, could result in a varied enough search result.

You can see the complete project, at my medium blog:
* [Building a Content-Based Children’s Book Recommender for Parents](https://medium.com/@anupamagarla/building-a-content-based-childrens-book-recommender-for-parents-680e20013e90?source=friends_link&sk=d7a2153c43e4f47704049ab1dc279285)

## Author

* **Anupama Garla** - [Pamaland1](https://github.com/Pamaland1)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Thank you to my husband, Jesung Park, for supporting me in new endeavors even though its tough
* and [METIS](https://www.thisismetis.com/live-online-data-science-bootcamp) teachers for also supporting, assisting, and teaching me mad data science skills.

