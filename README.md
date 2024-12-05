# SpotifyWrappedAnalysis

Statistical analysis of my friends spotify wrapped.

It has become tradition for people to upload thier Spotify wrapped summaries to instagram, for the most part no one pays attention to these publications, except for a friend or two. But I have decided to make use of all that free data and have some fun analyzing it, and maybe learning somethig in the process.

## Data structure

The information in the spotify wrapped is of a strange form, each person has several heterogeneous data blocks, the top songs, top authors and minutes listened to. The fact that two of the blocks are lists almost instantly rules outh any type of relational database, you can include lists either using postgres, or creating an intermediate table for the n to n relationship but the scope of this project is a fast and fun to be done in a weekend, there is no need fot that shenanigans.

Said that I am going to use JSON to store the data. It may not be the best option, but dumping the data is straigh forward and it can be easily interpreted and transfomed into any other type afterwards. Also take into account that the publications with the data only last 24h (an instagram story for the most part) so a fast and easy implementation is necesary, despite the additional process of interpreting the data.

The overall structure of the database is a JSON with a list of objects, each object is a wrapped summary with all the data in its corresponding strcture. Yes im including the genre, if feel that some interesting results can be extracted from that.

```JSON
[

    {
        "top_artists": ["artist1", "artist2", "artist3", "artist4", "artist5"],
        "top_song": ["song1", "song2", "song3", "song4", "song5"],
        "minutes_listened": 1234,
        "genre": "male"
    },
    {
        "top_artists": ["artist1", "artist2", "artist3", "artist4", "artist5"],
        "top_song": ["song1", "song2", "song3", "song4", "song5"],
        "minutes_listened": 1234,
        "genre": "male"
    }
]

```
