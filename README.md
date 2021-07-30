# psql
 
A quick start guide to `psql`, the terminal-based front-end to PostgreSQL.

### Set Alias

Once you've downloaded PostgreSQL, open a terminal. If connecting to an existing database, run the following command.

`alias psql='PGPASSWORD=$PASSWORD /$PATH/psql -h $SERVER -p $PORT -U $USERNAME $DATABASE'`

If creating a database from scratch, run the following command instead.

`alias psql='PGPASSWORD=$PASSWORD /$PATH/psql -U postgres'`

Setting this alias will allow you to just type `psql` in the terminal to automatically perform the connection process. To always have access to this alias, add it to your `~/.zshrc` file.

### Set Formatting

The `\x auto` command informs psql to display the result set in expanded view (as a list of document key-value pairs) when the result set is too wide to fit the terminal width, and in the normal table format otherwise.

Also cool, you can change the prompt text with `\set PROMPT1 'stephmod %/=#'`, where `%/` means the name of the database. See documentation for more customization options.

Another nice to have, you can set `\timing` to print how long a query takes to run.

To set these as a default, add them to your `~/.psqlrc` file.

### Set Syntax

When writing more complex queries, it's best to use the editor, invoked with the `\e` command. To turn on color syntax, add the following to your `~/.vimrc` file.

```
syntax on
au BufRead $TMP_PATH/psql.edit.* set syntax=sql
```

### Basic Commands

- List tables: `\dt $SCHEMA.*`
- List views: `\dv $SCHEMA.*`
- See view definition: `\d+ $SCHEMA.$VIEW`
- Editor mode: `\e`
- Export as csv: `\copy (SELECT * FROM $TABLE) TO '$PATH/$FILE.csv' CSV HEADER`
- Import as csv: `\copy $TABLE FROM '$PATH/$FILE.csv' DELIMITER ',' CSV HEADER`
- Run query from file: `\i $PATH/$FILE.sql`
- Clear console: `\! clear`
- Quit results: `q`
- Quit psql: `control d`

### Upgrade to pgcli

`pip install pgcli` for built in auto-completion and better syntax highlighting. Write and save sql queries in VSCode, then run them with the `\i $PATH/$FILE.sql` command. This allows you to save sql files alongside other files on a per project basis.

### Resources

https://www.postgresql.org/docs/9.3/app-psql.html#APP-PSQL-PROMPTING

https://unencumberedbyfacts.com/2016/01/04/psql-vim-happy-face/

https://gist.github.com/Kartones/dd3ff5ec5ea238d4c546

https://www.pgcli.com
