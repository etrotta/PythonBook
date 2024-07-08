### Exercise 1 - Tables and statements

### Exercise 2 - Relationships

### Challenge - Pokémon Cards
%% Honestly, this could be a project on its own %%

Building on top of [[Chapters/Excercises/Set Operations 1|Set Operations 1]],

- Create a table for `Pokemon`, a table for `Card`, a table for `Pack`, and a table for the many-to-many relationship between cards and packs
Creates tables for:
- Pokémon, including their name and generation
- Cards, with a foreign key to the Pokémon table
- Packs, including a name for the pack and a timestamp for when it was first made available for sale
- The relationship between Cards and Packs (`many:many`)

You must also include unique identifiers for each table, and you may add other columns beyond the ones listed here, such as evolutions, types or rarity

You can import data from online sources you can find, or insert some records manually to test. You can pick arbitrary values for mocked data if inserting manually.

Try to answer the questions from the Set Operations exercise using this database, but some additional questions you can try to answer:
- When was each Card first made available for sale?
- When was each Pokémon first made available for sale?
- How many cards each Pokémon has?
- How many packs is each Pokémon part of?
