# MISC

DESKTOP Store system built with RUST(TAURI) & VUE

```bash
# run in web browser
npm run dev
```

To run in desktop environment, make sure you have followed these instructions [tauri#getting-started/prerequisites](https://tauri.app/v1/guides/getting-started/prerequisites)

```bash
# run in desktop environment
cargo tauri dev
```

## Thoughts about infrastructure

### Backend

Looking for alternatives...
There are 2 main alternatives, basically it could work with a free tier platform, I found 2 possible options:

1. https://supabase.com/database
2. https://planetscale.com/pricing

Both options look good and fit with the solution I want to create.

One impediment might be the network bandwidth, it could fail sometimes, thus I need to create a mechanism to sync the database every night, mechanism algorithm could be something like.

1. Record every record locally.
2. Upload the bunch of records to the main database every night.
3. Once records are uploaded, clear cache data.
4. should sync local database with the new fresh data.

### Backend TO-DO

- I need to create 1 store, each table should have a column to identify if the row is synced up.
- I need to create a hashmap in memory to identify which tables have been modified therefore these tables need to be updated.
- I need to create a backend API REST with domain driven design.

Initially I tought of create a redis store locally but now I think I could not work as expected since local database would be a replica for the cloud one, so I need to implement a real database locally too, for compatibily and management purposes.
