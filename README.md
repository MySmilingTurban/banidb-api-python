# [BaniDB.py](https://pypi.org/project/banidb/)
A Python wrapper for [BaniDB API](https://github.com/KhalisFoundation/banidb-api)

[![](bdb.svg)](http://banidb.com)

# Installation
- Run ```pip install banidb```

# Vision Statement

BaniDB's vision is to create a single, universally accessible Gurbani Database for Sikh websites and applications. BaniDB is, and will continue to be, the most accurate and complete Gurbani database ever created for use by Sikhs around the world.

In order to make this vision possible, members of this collaborative effort work to ensure that the platform is self-sustaining, tested, and secure.

# Usage

## Search Types
```python
# Get searchtype indices to be used for custom search
search_types = banidb.search_type()
print(search_types)
```

**All available Search Types**
| Index   | Search Type                                             |
|:-------:|:--------------------------------------------------------|
|    0    |First letter each word from start (Gurmukhi)|
|    1    |First letter each word anywhere (Gurmukhi) **[Default]** |
|    2    |Full Word (Gurmukhi)                                     |
|    3    |Full Word Translation (English)                          |
|    4    |Romanized Gurmukhi (English)                             |
|    5    |Ang                                                      |
|    6    |Main Letter (Gurmukhi)                                   |
|    7    |Romanized first letter anywhere (English)                |

## **Sources**
```python
# Get all sources with ids
sources_data = banidb.sources()
print(sources_data)
```
**All available Sources**
| Source ID | Source                      |Source Unicode|
|:---------:|:----------------------------|:---- |
|A          |Amrit Keertan                |ਅੰਮ੍ਰਿਤ ਕੀਰਤਨ|
|B          |Bhai Gurdas Ji Vaaran        |ਭਾਈ ਗੁਰਦਾਸ ਜੀ ਵਾਰਾਂ|
|D          |Dasam Bani                   |ਦਸਮ ਬਾਣੀ|
|G          |Sri Guru Granth Sahib Ji     |ਸ੍ਰੀ ਗੁਰੂ ਗ੍ਰੰਥ ਸਾਹਿਬ ਜੀ|
|N          |Bhai Nand Lal Ji Vaaran      |ਭਾਈ ਨੰਦ ਲਾਲ ਜੀ ਵਾਰਾਂ|
|R          |Codes of Conduct and Other Panthic Sources |ਰਹਿਤਨਾਮੇ ਅਤੇ ਪੰਥਕ ਲਿਖ਼ਤਾਂ|
|S          |Bhai Gurdas Singh Ji Vaaran  |ਭਾਈ ਗੁਰਦਾਸ ਸਿੰਘ ਜੀ ਵਾਰਾਂ|

## Search

banidb.search (query, [searchtype](https://github.com/MySmilingTurban/banidb-api-python/blob/docs/README.md#search-types)=1, [source](https://github.com/MySmilingTurban/banidb-api-python/blob/docs/README.md#sources)='all', [larivaar](https://github.com/MySmilingTurban/banidb-api-python/blob/docs/README.md#larivaar)=False, [ang](https://github.com/MySmilingTurban/banidb-api-python/blob/docs/README.md#angs)=None, [raag](https://github.com/MySmilingTurban/banidb-api-python/blob/docs/README.md#raags)=None, [writer](https://github.com/MySmilingTurban/banidb-api-python/blob/docs/README.md#writers)='all', page=1, results=None)


**Example**
```python
# Searching Bandhana Har Bandhana Gun Gaavo Gopal Rai....
shabad_data = banidb.search("bhbgggr")

# Output
shabad_data = {
                'total_results': 1,
                'total_pages': 1,
                'pages_data': 
                    {'page_1': 
                      [{
                        'shabad_id': 2610,
                        'verse': 'ਬੰਦਨਾ ਹਰਿ ਬੰਦਨਾ ਗੁਣ ਗਾਵਹੁ ਗੋਪਾਲ ਰਾਇ ॥ ਰਹਾਉ ॥',
                        'steek': {
                            'en': 'I bow in reverence to the Lord, I bow in reverence. I sing the Glorious Praises of the Lord, my King. ||Pause||',
                            'pu': 'ਹੇ ਭਾਈ! ਪਰਮਾਤਮਾ ਨੂੰ ਸਦਾ ਨਮਸਕਾਰ ਕਰਿਆ ਕਰੋ, ਪ੍ਰਭੂ ਪਾਤਿਸ਼ਾਹ ਦੇ ਗੁਣ ਗਾਂਦੇ ਰਹੋ ।ਰਹਾਉ।'
                        }, 
                        'source': {
                            'pu': 'ਸ੍ਰੀ ਗੁਰੂ ਗ੍ਰੰਥ ਸਾਹਿਬ ਜੀ',
                            'en': 'Sri Guru Granth Sahib Ji', 
                            'ang': 683, 'raagpu': 'ਰਾਗੁ ਧਨਾਸਰੀ', 
                            'raagen': 'Raag Dhanaasree', 
                            'writer': 'Guru Arjan Dev Ji'
                        }
                      }]
                    }
            }
```

## **Shabad**
```python
# Get shabad from shabad_id
shabad_data = banidb.shabad(shabad_id, larivaar=False)
print(shabad_data)
```

## **Random**
```python
# Get random shabad
shabad = banidb.random(source_id='G')
print(shabad)
```

## **Hukamnama**
When no parameters are provided it automatically gives the Hukamnama of current date, according to the availability and Time Zone.
```python
# Get Hukamnama for a specific date 
data = hukamnama(year=y, month=m, day=d)
print(data)
```

## **Writers**
```python
# Get all writers with ids
writers_data = banidb.writers()
print(writers_data)
```

## **Raags**
```python
# Get all raags with ids
raags_data = banidb.raags()
print(raags_data)
```

## **Raag**
```python
# Get all available details using raag_id
raag_data = banidb.raag(raag_id)
print(raag_data)
```

## **Angs**

```python
# Get the banis on a specific Ang (Page)
gurbani = banidb.angs(ang_no, source_id='G', larivaar=False, steek=False, translit=False)
print(gurbani)
```
---
## Release
### Checkout the main branch
``` 
git checkout main
git pull
```

#### Increment the version 

Pick one of the `major|minor|patch` to update 
For example, let's release the version to 0.4.0

```
bump2version --allow-dirty --verbose --commit --tag --new-version 0.4.0 patch setup.py
```

For minor
``` 
bump2version --allow-dirty --verbose --commit --tag --new-version 0.4.0 minor setup.py

```

For major
```  
bump2version --allow-dirty --verbose --commit --tag --new-version 1.0.0 major setup.py

```

Note: its always good to start with the `--dry run` first

### Push to remote
```
git push

```
Push the tag to remote too
in our case 0.4.0 `git push origin 0.4.0`
```
git push origin <tag-name>
```

#### Run the github release action

#### From UI
This will upload the bits to pypi.org
It can be done from the UI. Select the tag we just created and pushed

#### From CLI (untested)
`gh` has a new feature to trigger workflow from the CLI. 
Note: at the time of writing this doc, this feature was not working on MacOS 
``` 
gh workflow run python-publish.yml
```
