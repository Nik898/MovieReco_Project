# MovieReco_Project
A movie information and recommendation website
2.1 BACKEND:
2.1.1 RECOMMENDATION MODELS: There 
are two recommendation models:
First model was created on the home page based on 
the movies searched and rated by the user. It was 
constructed using concepts of CountVectorizer and 
Cosine Similarity. A CSV file containing detailed 
information about 90,000 movies was used as a 
dataset. For the CountVectorizer, the director and the 
genre of the movie were considered and 10 similar 
movies were extracted using Cosine Similarity. 
Before putting all the movies in count vectorizer, 
they are filtered on the following parameters: 
1. Same language 
2. Same country
3. Ratings in the range of +-2 from the particular 
movie
4. Year of all the movies considered should not be 
more than 10 years for the particular movie
This is done to reduce the number of movies to be 
compared with. 
Second model was created on the information page 
for a particular movie. It recommends movies based 
on similar ratings. Concepts of pivot table and 
Jaccard similarity were used to generate 
recommendations. A CSV file containing detailed 
information about 90,000 movies was used as a 
dataset. In that CSV file there are ratings out of 10 
given by 23 critic reviewers for each movie. 
Therefore each of the 23 reviewers for a movie were 
taken in an array. So to find the recommendations for 
that movie, we compare its array with the arrays for 
all the movies in the dataset using Jaccard similarity 
and find the five most similar movies. 
2.1.2 SCRAPING: Three tools were used to scrape 
information of a movieBeautifulsoup4:- Beautiful Soup is a Python library 
for pulling data out of HTML and XML files. It 
works with your favorite parser to provide idiomatic 
ways of navigating, searching, and modifying the 
parse tree. This tool was used to scrape the movie 
poster, the cast photos, background poster and 
audience reviews of a movie from the IMDb website.
Requests-html:- The requests-HTML library is an 
HTML parser that lets you use CSS Selectors and 
XPath Selectors to extract the information that you 
want from a web page. This tool was used to scrape 
the trailer and the OTT streaming device option of a 
particular movie from google.
IMDbPY:- This API was used to extract the names 
of all the cast members and directors, the synopsis, 
the genre, the runtime, release year and the IMDb 
rating of a particular movie from the IMDb website.
2.1.3 MONGODB: 
Q)Why NoSQL over SQL.
NoSQL databases are often more scalable and 
provide superior performance. In addition, the 
flexibility and ease of use of their data models can 
speed development in comparison to the relational 
model. Document databases such as MongoDB use 
JSON as a way to turn data into something much 
more like code. This allows the structure of the data 
to be under the control of the developer. 
MongoDB stores data records as documents 
(specifically BSON documents) which are gathered 
together in collections. A database stores one or 
more collections of documents.
We have one database named MovieReco which 
consists of two collections:
INFO: This collection stores all information related 
to users. Each document in this collection is unique 
to a particular user. Each document contains 
following user details:
1. Username
2. Password
3. Email id(unique to every user)
4. MovieList – List of movies user is interested in
5. Like – List of movies user has liked
6. GenreList - List of genres a user prefers
RATINGS: Each document in this collection 
contains the following :
1. Movie Name – Unique movie name identifying 
any particular document
2. Rating map – It is a dictionary object in which 
the key is the unique email id of a user and the value 
is a list containing:
a. Movie rating given by user
b. Movie review given by user
2.2 FRONT END:
2.2.1 COLOUR TRANSFORM: In the movie 
page, the background colour of the page is extracted 
from the poster. The image is drawn in an HTML 
Canvas element from which we can extract the RGB 
value of every pixel in that image. The values are 
rounded to the nearest multiple of 25 and a dictionary 
is made which stores the number of pixels of a 
colour. The colour with the most number of pixels is 
taken and a lighter and a darker colour of the same 
RGB ratio is taken, one of them being the foreground 
and the other being background, depending on how 
light or dark the colour is.
2.2.2 SEARCH ENGINE: Firstly the code fetches 
the link from the IMDb database. It formats the link 
fetched from the IMDb database and then stores the 
data in a .json file. An event listener for keyup has 
been added which will update the search results. 
Each option of the search result has a dedicated 
button which when clicked will redirect to their 
respective movie pages. The result will show the 
name of the movie and its year. 
