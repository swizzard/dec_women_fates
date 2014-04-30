# Fates of Women in Decemberists' Songs
A dataset hand-compiled by [Sam Raker](http://samraker.com/), based on lyrics taken from [A-Z Lyrics Universe](http://www.azlyrics.com/d/decemberists.html),
with additional fact-checking based on listening to the songs.


This is a JSON-formatted dataset of things that happen to women in songs performed by the Decemeberists.

## Explanation of Keys
### `Album`  
Explanation: The name of the album  
Type: `string`

### `Song`
Explanation: The name of the song  
Type: `string` (unique)

### `Women`
Explanation: The female characters in the song  
Type: `array` of `woman` `object`s

### `Notes`
Explanation: General notes for the song  
Type: `string` or `null`

## Explanation of Keys for `woman` objects
### `Name`
Explanation: If capitalized, the woman's name. If uncapitalized, the woman's title or another helpful identifier.  
Type: `string`

### `Fate`
Explanation: What happens to the woman in the song.  
Type: `string` or `null`

### `Code`
Explanation: An integer code corresponding to the severity of the woman's fate  

  * `-1` : something basically positive
  * `0` : null/none/neutral
  * `1` : something unfortunate or harmful, but non-fatal
  * `2` : death from natural causes
  * `4` : murder
  * `8` : rape
  * `12` : rape + murder  

Type: `integer`

### `Notes`
Explanation: Notes on the character  
Type: `string` or `null`


## General Notes
This is very much an alpha dataset. Please comment on/pull-request/fork it to make improvements.

Since the general idea with the `code` values is that they can be added together to represent multiple misfortunes befalling a character, that multiple songs describing the same character in the same position would only have `code` values > 1 the first time, and `code` = 0 subsequently, until something else happens. Thus, Margaret in *The Hazards Of Love* is kidnapped in "The Abduction of Margaret" and remains in captivity until "The Hazards of Love 4 (The Drowned)." There are several intervening songs that describe or reference her captivity, but since it's 'the same' kidnapping event, she gets `fate`: `null` and `code`: 0 for those songs.


## Open Issues
* I decided that characters referenced only as 'you' should be counted as women, absent any countervailing context clues (e.g., "The Soldiering Life"). Is this too hand-wavy?
* I tried to include all female characters referenced at all, including all the wives in "16 Military Wives" and all Margaret's fellow maidens in "The Hazards of Love 1". Should the dataset be restricted solely to 'major' characters?
* Eventually, I should probably go back and do the same thing for male characters in the songs.
