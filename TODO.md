# Structure of program

1. Read a store a config file: the config file will have base directory for podcasts, list of RSS feeds, and location of database file.
2. Once that's read, we read and load the database: see the section for database fields to see what's in there. 
3. Iterate throught the list of `Podcast`s in the database, and find out if any of them have been updated.
4. If so, use `youtube-dlp` to download the new episodes.

## Database fields

Database will just be a list of `Podcast` entries, where each `Podcast` entry has info about RSS feed link, base directory for the podcast, as well as the last podcast episode downloaded so that only new episodes are downloaded.

# Wishlist

1. Would be nice to have a clean way of adding and removing podcasts that we track.
2. More generally, a nice CLI for the app should be good: something with good error logging.
3. Informative messages, i.e. how many episodes are being downloaded, messages about download success/failure, etc.
4. Graceful recovery from failed downloads, i.e. don't update the database if some download failed. However, if a download keeps failing, have a way of bypassing that.

# Crates to possibly use

- [ ] `youtube-dl`
- [ ] `clap` (for good CLI)
- [ ] `sled` or `sqlite` (or something else, that's a simple KV store)
- [ ] Something to read a config nicely: maybe serialize the `Config` struct to JSON.