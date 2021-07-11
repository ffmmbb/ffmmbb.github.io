# Title



### Introduction

The spotify API contains numerous features are music; the two we're going to focus on for this excercise are **valence** (basically how happy a song is) and **danceability** (err... how danceable a song is).

### Importing the data

Using [spotipy](https://spotipy.readthedocs.io/en/2.18.0/#getting-started) we access Spotify and pull in the audio features for every song in my custom playlists.

Here's an example of how it looks for tracks (filtering for just the features we're interested in.


```python
playlist_r_features = playlist_features[['playlist_name', 'track_name', 'artist_name', 'valence', 'danceability']]
playlist_r_features.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>playlist_name</th>
      <th>track_name</th>
      <th>artist_name</th>
      <th>valence</th>
      <th>danceability</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>old</td>
      <td>The Likeness Of Being</td>
      <td>Jamie T</td>
      <td>0.349</td>
      <td>0.211</td>
    </tr>
    <tr>
      <th>0</th>
      <td>old</td>
      <td>Francis Forever</td>
      <td>Mitski</td>
      <td>0.320</td>
      <td>0.535</td>
    </tr>
    <tr>
      <th>0</th>
      <td>old</td>
      <td>alt.end</td>
      <td>The Cure</td>
      <td>0.578</td>
      <td>0.625</td>
    </tr>
    <tr>
      <th>0</th>
      <td>old</td>
      <td>Motion Sickness</td>
      <td>Phoebe Bridgers</td>
      <td>0.626</td>
      <td>0.652</td>
    </tr>
    <tr>
      <th>0</th>
      <td>old</td>
      <td>Nobody</td>
      <td>Mitski</td>
      <td>0.494</td>
      <td>0.398</td>
    </tr>
  </tbody>
</table>
</div>



### Aggregating the data

Let's explore the average valence of the playlists. One way to do this could be to take a summary function (mean, median etc.) but it may be more useful to examine the distribution via a boxplot (we'll do this utilising seaborn)

```python
sns.boxplot(y='playlist_name', x='valence', data=playlist_r_features)
```




    <AxesSubplot:xlabel='valence', ylabel='playlist_name'>




![png](images/Spotipy Exploration_files/output_3_1.png)


Generally you can see some trends emerging.

My Radiohead playlist has a much lower valence than all bar a single playlist (which is just guided meditation tracks); and Cindy Approved is the happiest playlist. My two main playlists (old & new) seem very similar. 

Now let's look at Danceability

```python
sns.boxplot(y='playlist_name', x='danceability', data=playlist_r_features)
```




    <AxesSubplot:xlabel='danceability', ylabel='playlist_name'>




![png](images/Spotipy Exploration_files/output_6_1.png)


That meditation can get quite danceable, eh?
