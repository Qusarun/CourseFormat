# Notes for making courses
1. It is recommended to have small notes in word meanings when the translation isn't specific enough. For example, the German word "du" can't be directly translated to modern English, so it would make sense to put its meaning as "du (sing./inf.)" or something similar.
2. Text or audio explanations for grammar would be appreciated. I haven't seen much of that in other language learning apps, so it would be nice to have it here.
3. Word card lessons WILL be broken if you don't have 4+ words when you are calling them.
4. Words and lessons go in the order that you put them in.
5. Word card lessons will use any newly added words before the old ones.
6. Please, test your courses before publishing them. Also, if you find any bugs, please contact me directly, and I'll try to fix them as soon as possible.

# Course files
The course file should be stored in the "LangApp/{LANGUAGE}" directory and have the locale (the language that the course is written in) as its file name. So, for example, a course for Toki Pona written in English would be in the "LangApp/Toki Pona" directory and have the name "English".

# Audio files
All audio files should be stored in the "LangApp/Audio" directory and have unique names that will not overlap with other courses. I recommend something like "{LANGUAGE}-{LOCALE}-{AUDIO_NAME}.mp3".

# Syntax of course files
## Lessons
- AUDIO_EXPLANATION {AUDIO_FILE_NAME} (plays an audio that explains some part of the language or introduces the learner to the course)
- IPA_CARDS (prompts the learner to select the card with the correct IPA transcription of a specific word)
- LISTENING_TEST {AUDIO_FILE_NAME} {QUESTION_BLOCK_1} {QUESTION_BLOCK_2} ... (plays an audio and then prompts the learner to answer multi-choice questions about it)
- READING_TEST {TEXT_BLOCK} {QUESTION_BLOCK_1} {QUESTION_BLOCK_2} ... (displays a text and prompts the learner to answer multi-choice questions about it)
- REV_WORD_CARDS (prompts the learner to select the card with the correct translation of a specific word (from their native language to the language they're learning))
- TEXT_EXPLANATION {TEXT_BLOCK} (displays a text that explains some part of the language or introduces the learner to the course)
- TRANSCRIBE_IPA {TEXT}::{TRANSCRIPTION} (prompts the learner to transcribe a sentence with IPA symbols)
- TRANSLATE_FROM {TEXT}::{TRANSLATION} (prompts the learner to translate a text written in the language they're learning to their native language)
- TRANSLATE_TO {TEXT}::{TRANSLATION} (prompts the learner to translate a text written in their native language to the language they're learning)
- WORD_CARDS (prompts the learner to select the correct translation of a specific word (from the language they're learning to their native language))

## Actions
There is also a single action that you can use to have it executed after lessons: "ADD_WORD {WORD}::{MEANING}::{IPA}". This action adds the specified word to the dictionary. The dictionary is used to generate words for word card lessons.

## Blocks
Any block starts with "BLOCK" and ends with "BLOCK". Both the start and closing keywords have to be on their own lines.
### Formatting
- %t for titles
- %b for bold text
- %n for normal text (reset the formatting)
- %r for red text
- %g for green text
- PARAGRAPH to separate paragraphs (this needs to be on its own line)
### Text blocks
Here is an example of a valid text explanation lesson:
```
TEXT_EXPLANATION

BLOCK
%tTitle
%nSome text
PARAGRAPH
%tAnother title
%nSome other text
BLOCK
```
### Question blocks
Here is an example of a valid reading test lesson:
```
READING_TEST

BLOCK
This text contains some information to answer the questions that follow.
BLOCK

# Choice question format: {QUESTION}::choice::{CHOICE 1}/{CHOICE 2}/...::{CORRECT_CHOICE_NUMBER}

BLOCK
QUESTION
Choice question?::choice::choice 1/choice 2/choice 3::2
BLOCK

# Truth question format: {QUESTION}::truth::{CORRECT_CHOICE}
# Avaialable choices: true, false, not stated

BLOCK
QUESTION
Truth question?::truth::true
BLOCK
```
### Note
Only a few of the lessons use blocks for their parameters. Other lessons such as AUDIO_EXPLANATION and TRANSLATE_TO are fully on one line:
```
AUDIO_EXPLANATION Welsh-English-Introduction.mp3
TRANSLATE_TO Good morning!::Bore da!
```
