# **Report: Analysis of Spotify Songs using Clustering and Dimensionality Reduction**

---

## **1. Objective**

The purpose of this analysis is to explore and cluster Spotify song data based on their features, including popularity, danceability, tempo, and genre. The project utilizes dimensionality reduction through Principal Component Analysis (PCA) and clustering through K-Means to uncover hidden patterns and insights about the songs.

---

## **2. Data Overview**

### **2.1 Data Description**
The dataset consists of two files: `high_popularity_spotify_data.csv` and `low_popularity_spotify_data.csv`. These datasets were combined to form a unified dataset containing various features of Spotify tracks.

### **2.2 Key Columns**
The dataset includes features such as:
- **Numerical Features**: `danceability`, `energy`, `tempo`, `valence`, `loudness`, `track_popularity`, etc.
- **Categorical Features**: `track_artist`, `playlist_genre`, etc.

### **2.3 Preprocessing Steps**
1. **Handling Missing Values**:
   - Columns with NA values were identified and filled with the mean for numerical features.
   - Unnecessary columns like `track_id`, `playlist_id`, and metadata columns were dropped.

2. **Feature Cleaning**:
   - Artist names were cleaned to remove special characters.
   - Categorical features (e.g., `track_artist`, `playlist_genre`) were label-encoded for numerical processing.

3. **Dimensionality Reduction**:
   - Features were scaled using the `RobustScaler` to handle outliers.
   - PCA was applied to reduce dimensionality while retaining maximum variance.

---

## **3. Exploratory Data Analysis (EDA)**

### **3.1 Missing Values**
- Total NA values were successfully addressed, leaving no missing data in the final dataset.

### **3.2 Genre and Danceability**
- The **average danceability score** was calculated for each genre. A bar chart highlighted how different genres vary in terms of danceability, revealing trends in listener preferences.

### **3.3 Genre and Popularity**
- A similar analysis of **average popularity by genre** was performed. Results indicated which genres tend to contain the most popular tracks, providing insight into audience trends.

### **3.4 Top Artists and Tracks**
- **Top 10 Artists**: The artists with the highest average track popularity were identified.
- **Top 10 Tracks**: The tracks with the highest average popularity were listed.

---

## **4. Dimensionality Reduction**

### **4.1 Principal Component Analysis (PCA)**
- The `RobustScaler` was applied to scale all features, ensuring outliers had minimal influence on the PCA process.
- PCA was used to reduce the dataset to **3 principal components**. The first three components explained a significant portion of the variance, summarizing the dataset efficiently.

---

## **5. Clustering**

### **5.1 Optimal Number of Clusters**
The **Silhouette Method** was used to determine the optimal number of clusters for K-Means:
- Silhouette scores were calculated for `k` values ranging from 2 to 10.
- The **highest silhouette score** was observed at `k=2`, suggesting two distinct clusters.

### **5.2 K-Means Clustering**
- K-Means clustering was performed with `k=2` on the PCA-transformed data.
- Each song was assigned a cluster label, and the centroids of the clusters were computed.

---

## **6. Results**

### **6.1 PCA Visualization**
- A scatter plot of the first two principal components (PC1 and PC2) was created, with colors representing the two clusters. The plot revealed clear distinctions between the clusters in the reduced feature space.

### **6.2 Cluster Characteristics**
The centroids of the clusters were transformed back into the original feature space to interpret their characteristics:

#### **Cluster 0**:
- Higher average **energy** and **danceability**, suggesting more upbeat tracks.
- Moderate **track popularity**, indicating this cluster might consist of moderately popular songs with engaging rhythms.

#### **Cluster 1**:
- Lower average **energy** and **danceability**, possibly consisting of slower or less intense tracks.
- Lower **track popularity**, indicating less mainstream appeal.

### **6.3 Feature Insights**
Using the centroids in the original feature space:
- **Danceability and Valence**: Cluster 0 had higher average scores, indicating "feel-good" tracks.
- **Tempo and Loudness**: Cluster 0 had slightly higher values, supporting the upbeat nature of these tracks.

---

## **7. Key Takeaways**

1. **Two Distinct Clusters**:
   - Cluster 0: More danceable, energetic, and moderately popular songs.
   - Cluster 1: Less energetic and less popular tracks.

2. **Genre Trends**:
   - Some genres consistently have higher danceability and popularity, making them strong candidates for marketing campaigns or playlist curation.

3. **Artist and Track Analysis**:
   - Insights into top-performing artists and tracks can inform strategies for partnerships, promotion, or playlist prioritization.

---

## **8. Recommendations**

1. **Playlist Curation**:
   - Use the clustering results to curate playlists that cater to distinct listener preferences, e.g., "Upbeat Dance Hits" for Cluster 0.

2. **Marketing Strategies**:
   - Focus marketing efforts on genres and artists associated with Cluster 0 to maximize engagement.

3. **Product Development**:
   - For music platforms, create recommendation engines that emphasize Cluster 0 for users seeking high-energy tracks.

4. **Further Analysis**:
   - Investigate additional features (e.g., lyrical content or user preferences) to refine clustering further.

---

## **9. Limitations**
- Clustering depends on the selected features. Including additional audio or user metadata could yield deeper insights.
- The use of `k=2` might oversimplify the segmentation. Future experiments with higher `k` values could uncover more nuanced clusters.

---

## **10. Conclusion**
The analysis successfully segmented Spotify tracks into two distinct clusters based on their features, highlighting trends in energy, danceability, and popularity. These insights can be leveraged for playlist curation, marketing, and user experience enhancement.
