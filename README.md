# Item-based-RecSys
Item-based recommendation system based on user movie ratings

The program is a movie recommendation system based on the collaborative filtering method using the k-nearest neighbors (k-NN) algorithm. It analyzes movie ratings to suggest movies that the user might like based on the preferences of other users.

Stages of the algorithm operation:

**Uploading data**:

The program reads movie data from the movies.csv file, which contains information about movie titles, and ratings data from the ratings.csv file, which contains information about which movies users rated and what ratings they gave them.

Unnecessary columns that do not affect the recommendation process are removed from this data, such as genres from movie data and timestamp from ratings data.

**Creating a preference matrix**:

Based on the ratings data, a user-movie matrix is formed, where the rows correspond to movies, the columns correspond to users, and the values in the cells are user ratings of movies.

Empty values in the matrix (where the user did not rate the movie) are filled with zeros.

**Data filtering**:

To improve the accuracy of recommendations and reduce the computational load, users who have left few ratings and films that have received few ratings are eliminated. Only active users who have rated more than 50 movies and popular movies that have been rated by more than 10 users remain.

**Data preparation for the model**:

The user-movie matrix is converted to a sparse format for more efficient operation of the model.

The matrix is transposed so that the rows correspond to users and the columns correspond to movies.

**Learning the k-NN model**:

A k-nearest neighbors (k-NN) model is being built and trained.

The model uses cosine distance as a measure of similarity between users, a full search algorithm to find neighbors, takes into account the 20 nearest neighbors, and uses all available processor cores.

**Selecting a user for a recommendation**:

The program selects the user for whom it is necessary to make recommendations.

**Preparing user data**:

Gets a list of movies that the user has rated.

Gets the ID of the movies that the user has rated.

Calculates the average vector of user preferences by averaging all their ratings.

**Search for similar movies**:

Using the k-NN model, for the average vector of user preferences, the n most similar movies are found by cosine distance, where n is the number of recommendations.

The first “neighbor" is excluded, which will always be the same movie as the average vector of the user.

**Creating a list of recommendations**:

The program generates a list of recommended movies by comparing the found movie IDs with their titles, and writing them down as a dictionary list with the movie name and cosine distance.

**Output of results**:

The results are displayed as a table showing the names of the recommended films and the cosine distances to them.

The program implements collaborative filtering based on k-NN to recommend movies. It processes ratings data, generates a preference matrix, trains the k-NN model, and finally provides a list of recommended movies for a specific user. The basic idea is that similar users can rate movies in a similar way, and therefore you can recommend movies that similar users liked.
