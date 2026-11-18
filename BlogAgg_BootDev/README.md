# Gator

Gator is a multi-user RSS reader for the command line. Gator collects posts from the feeds you follow and helps organize the data.

## Installation

Bring two great tools: the latest [Go
toolchain](https://golang.org/dl/) and a running PostgreSQL database.

From the project directory, build Gator with:

```sh
go build -o gator .
```

You now have a `gator` executable ready for action. If you have Go's bin
directory in your `PATH`, you can install it for use from anywhere with:

```sh
go install .
```

## Configuration

Gator expects a `.gatorconfig.json` file in your home directory. Think of it as
Gator's tiny credential card:

```json
{
  "db_url": "postgres://username:@localhost:5432/database?sslmode=disable"
}
```

Replace the example values with your PostgreSQL connection string. The database
must already exist and must use the schema expected by Gator.

## Usage

### Register and log in

First, introduce Gator to a new user:

```sh
gator register <name>
```

Then set that user as the active account:

```sh
gator login <name>
```

### Add and follow feeds

Add a feed to Gator's collection:

```sh
gator addfeed <url>
```

Already have a feed in the database? Follow it just as easily:

```sh
gator follow <url>
```

When you want to stop following a feed:

```sh
gator unfollow <url>
```

### Collect and browse posts

Start the aggregator, giving it the interval at which to fetch feeds. This
example checks every 30 seconds:

```sh
gator agg 30s
```

Take a look at the posts, optionally limiting how many Gator brings back:

```sh
gator browse [limit]
```

### Helpful commands

- `gator users` - List every registered user.
- `gator feeds` - List every feed known to Gator.
- `gator following` - List the feeds followed by the active user.
- `gator reset` - Reset Gator's database; use this command only when you intend
  to clear its data.

Now go experiment!
