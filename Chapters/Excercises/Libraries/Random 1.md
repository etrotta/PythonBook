%% TODO MOVE THIS TO VTUBER/WEEB PATH AND WRITE SOMETHING NORMAL FOR HERE LIKE LOTTERY %%
### Exercise 1 - Gacha

Create a list of VTubers, then assign a rarity to each of them, and lastly assign a relative weight to each rarity.
For example:
```
vtubers = [
	("neuro", "common"),
	("evil", "rare"),
	("anny", "rare"),
	("vedal", "super rare"),
]

# Relative weights, (1/13) super rare, (2/13) rare, (10/13) common
rarities = {
	"common": 10,
	"rare": 2,
	"super rare": 1,
}
```

Then write a function to convert from this to the format accepted by `random` functions.

Given a number of pulls inputted by the user, pick that many VTubers and print of them (allowing duplicates).

Optionally print each of them separately, with a different text for each rarity, and some delay between them.
