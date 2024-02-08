# Bugfix for Hindi text generation

### bug 1: No Hindi text rendering in official trdg pypi package 1.8.0
reproduce results with:

```bash
trdg -l hi -c 10 -w 5
```
#### image
![गरमटयए जतवन टकटकत फफकर बरत_0](https://github.com/prathameshza/prac/assets/46810093/0b3ebd6b-3bad-46de-8113-e84971cf452d)

#### text
गरमटयए जतवन टकटकत फफकर बरत

## Using official repository
### bug 2: Hindi text don't have matras and matras in image are seperated! 
reproduce results with:

```bash
git clone https://github.com/Belval/TextRecognitionDataGenerator.git

cd TextRecognitionDataGenerator/trdg/

python3 run.py -l hi -c 10 -w 5
```

## Before bug fix
#### image
![एकशरयत ठठकन ललत-षषठ बखन तर_0](https://github.com/prathameshza/prac/assets/46810093/5b3cb744-9d97-411c-a128-661e1498aeb5)

### text
एकशरयत ठठकन ललत-षषठ बखन तर

## After bug fix
#### image
![कलपाओ घिघियाता हँसोहीं मकी डंडा-डोलिओं_0](https://github.com/prathameshza/prac/assets/46810093/75e94a6f-a75f-4f70-8dfd-561bdea96a12)

#### text
कलपाओ घिघियाता हँसोहीं मकी डंडा-डोलिओं

## Changes made
- Modified make_filename_valid function in utils.py for OSError 22
- Modified save the image with try catch block in data_generator.py for OSError 22
- Replaced Hindi font Lohit-Devanagari with Gargi to seperate Hindi Matras

> Note: Changing the font also changes the images created per second
### Below is the tested font and their speeds for Hindi image generation
| Font            | Speed     |
|----------------:|-----------|
|Lohit-Devanagari | 15-16 it/s|
|Gargi            | 17-18 it/s|
|Sura unicode     | 11-12 it/s|
|akshra unicode   | 4-5 it/s  |
|Kurti dev 010    | 50-55 it/s|
|aakar regular    | 50-55 it/s|
|freesansbold     | 9-10 it/s |
|Nakula           | 8-9 it/s  |

***I am using Linux Mint 21.3 "Virginia" Cinnamon Edition for testing***
- python version 3.10.12
- pillow version 9.5.0

> I have also tested other languages with the modified changes, they work fine

