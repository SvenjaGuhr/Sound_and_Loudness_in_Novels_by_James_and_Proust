# Sound and Loudness in Novels by Henry James and Marcel Proust (Engl. Translation)

Repository accompanying the talk in the COMLIT 202C 001 - LEC 001 class at UC Berkeley,
**"Approaches to Genre: The Novel. Points of View and/on Sound in Novels"** (Fall 2026).
[Course page](https://classes.berkeley.edu/content/2026-fall-comlit-202c-001-lec-001)

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/REPOSITORY/blob/main/Sound_in_James_and_Proust.ipynb)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/USERNAME/REPOSITORY/main?labpath=Sound_in_James_and_Proust.ipynb)

> **Never worked with code before?** You're who this guide is written for. You don't need to install anything or know any programming to explore the material. Start with [Step 1](#step-1-look-at-the-results-no-installation), which only needs a web browser.

---

## Contents

- [What is this?](#what-is-this)
- [The novels and the data](#the-novels-and-the-data)
- [Step 1: Look at the results (no installation)](#step-1-look-at-the-results-no-installation)
- [Step 2: Run the notebook in your browser](#step-2-run-the-notebook-in-your-browser)
- [A two-minute introduction to notebooks](#a-two-minute-introduction-to-notebooks)
- [Step 3: Play with the data](#step-3-play-with-the-data)
- [What the notebook measures](#what-the-notebook-measures)
- [Questions to take into the discussion](#questions-to-take-into-the-discussion)
- [What the numbers cannot tell you](#what-the-numbers-cannot-tell-you)
- [Glossary](#glossary)
- [Running the notebook on your own computer](#running-the-notebook-on-your-own-computer)
- [Troubleshooting](#troubleshooting)
- [What is in this repository](#what-is-in-this-repository)

---

## What is this?

In this repository, three novels have been marked up so that a computer can find every passage where a sound occurs. Each passage was also given a loudness value between 1 (very quiet) and 5 (very loud). The **Jupyter notebook** (a document that mixes explanatory text, small programs and their results) counts and compares these sounds across the three books:

- How much sound does each novel contain, chapter by chapter?
- How loud are these sounds, and how widely does the loudness vary?
- Who makes the sound: speaking characters, or the world around them?
- Where does **music** appear, and is it written as a sound event or as something heard, remembered and thought about?
- How often does the narration dwell on the act of **hearing** (*hear, listen, overhear, ear*)?

These questions connect to the seminar's theme of point of view. James builds his novels around a single consciousness: in *What Maisie Knew*, a child who learns what she knows by overhearing adults. Proust's narration attends to what it means to hear from a particular place, with a particular ear. Counting does not answer these questions. It gives you a map of the three novels that you can set against your own reading, and that may point you to passages you would otherwise pass over.

---

## The novels and the data

| Novel | Author | First published | Words | Chapters |
|---|---|---|---|---|
| *What Maisie Knew* | Henry James | 1897 | 98,361 | 32 (an opening section + I–XXXI) |
| *The Golden Bowl* (complete) | Henry James | 1904 | 212,368 | 42 (two books, six parts) |
| *Swann in Love* (English translation) | Marcel Proust | 1913 | 91,562 | none: divided into 27 segments of about 3,000 words |

The texts are stored in the folder `data/` as **XML files**. XML is plain text with labels, called *tags*, in angle brackets. Here is a sentence from *Swann in Love* as it appears in the file:

```xml
What had happened was that <ambient_sound>the violin had risen to a series of high notes</ambient_sound>,
on which it rested as though expectant ...
```

And a sentence from *The Golden Bowl*:

```xml
If it was a question of an Imperium, <character_sound loudness="3.0">he said to himself</character_sound>, ...
```

There are two kinds of sound tags:

- **`<character_sound>`**: a sound made by a character, most often speech (*he said*, *she cried*), but also laughter, sighs, footsteps.
- **`<ambient_sound>`**: a sound in the surroundings: music, bells, the sea, the noise of a street, silence.

The **`loudness`** attribute holds a value from 1 to 5. These values were assigned by a dictionary-based method: a list of sound words, each with a loudness value (*whisper* is quiet, *thunder* is loud). Each tagged passage receives the average value of the sound words it contains. About a third of the passages contain no word from the dictionary and therefore have no loudness value.

The sound passages were found automatically by a computer model trained to recognize sound events, then partly revised by hand. **The tagging contains errors**, and spotting them is part of the exercise (see [What the numbers cannot tell you](#what-the-numbers-cannot-tell-you)).

You can open any XML file directly in your browser or in a text editor to read the novel with its tags.

---

## Step 1: Look at the results (no installation)

The quickest way in is the **report**: one web page with all charts, a short reading guide for each, and a searchable table of every music passage.

1. Click on `Sound_in_James_and_Proust_report.html` in the file list above.
2. Click the **download** button (the arrow icon at the top right of the file view). GitHub shows HTML files as code, not as pages, so you need to download it.
3. Double-click the downloaded file. It opens in your web browser and works offline.

Each chart in the report is interactive:

- **Hover** over a bar, point or line to see the exact values. In the loudness chart over narrative time, hovering shows the sound passage itself.
- **Click** a name in a legend to hide or show that novel.
- **Drag** across a chart to zoom in; **double-click** to zoom out again.

At the bottom of the report, **Music in context** lists every music word in the three novels with the sentence around it. Use the menus and the search box to filter it, for example by searching for *Vinteuil*, *phrase* or *harmony*.

The folder `html_visualizations/` contains the same charts one by one, for use in slides. Download the whole folder, since the charts need the file `plotly.min.js` that sits next to them.

---

## Step 2: Run the notebook in your browser

Reading the report is like reading a finished essay. Running the notebook is like having the author's notes and being able to redo every step, with your own questions. You can do this in your browser, without installing anything.

### Option A: Google Colab (recommended; needs a Google account)

1. Click the **Open in Colab** badge at the top of this page.
2. If Colab says the notebook was not authored by Google, click **Run anyway**. This warning appears for every notebook from GitHub.
3. In the menu, choose **Runtime → Run all**.
4. Wait about a minute. One of the first code cells downloads the novels from this repository; then the cells run one after another, and the charts appear under them.

Your changes in Colab are not saved to this repository. If you want to keep your version, choose **File → Save a copy in Drive**.

### Option B: Binder (no account needed)

1. Click the **Binder** badge at the top of this page.
2. Wait. Binder prepares a temporary computer for you, which can take a few minutes the first time.
3. When JupyterLab opens, choose **Run → Run All Cells**.

Binder sessions are temporary. They close after about ten minutes without activity, and your changes are lost. To keep a changed notebook, use **File → Download** before you leave.

---

## A two-minute introduction to notebooks

A notebook is a sequence of **cells**:

- **Text cells** contain explanations like this one.
- **Code cells** contain short instructions in the programming language Python. They have a grey background and a ▶ symbol or a `[ ]` next to them.

To run a code cell, click into it and press **Shift + Enter**. The result (a number, a table or a chart) appears below the cell, and the cursor moves to the next cell.

Four things worth knowing:

1. **Order matters.** Later cells use results from earlier ones. If you see an error like `NameError: name 'events' is not defined`, an earlier cell has not been run. Use **Run all** and the problem disappears.
2. **You cannot break anything.** The novels in `data/` are only read, never changed. If something goes wrong, use **Runtime → Restart and run all** (Colab) or **Kernel → Restart Kernel and Run All Cells** (Jupyter) to start fresh.
3. **Lines starting with `#` are comments.** They are notes for the reader, and the computer ignores them.
4. **Text in quotation marks is data, not code.** In `concordance("little phrase")`, you can replace `little phrase` with any word or phrase you like. Keep the quotation marks.

You do not need to understand every line of code to use the notebook. Read the text cells, run the code cells, and look at what comes out.

---

## Step 3: Play with the data

The last part of the notebook, **"10. Try it yourself"**, is a playground with four ready-made tools. Each takes words as input. Change the words in quotation marks, press Shift + Enter, and look at the result.

### Read every occurrence of a word in context

```python
concordance("little phrase")
concordance("silence")
concordance("ear", text="What Maisie Knew")
```

This works like a printed concordance: every passage where the word or phrase occurs, with the words to its left and right, and its position in the novel as a percentage (0 % is the first page, 100 % the last).

### Count words across the three novels

```python
word_table(["heard", "listened", "overheard", "silence", "noise"])
```

The table gives the count in each novel and the count **per 10,000 words**. Use the second column for comparisons, because *The Golden Bowl* is more than twice as long as the other two books.

### See where in each novel words appear

```python
compare_words(["silence", "silent", "hush", "stillness"], label="silence").show()
compare_words(["piano", "violin", "sonata", "music"], label="music").show()
compare_words(["whisper", "whispered", "murmur", "murmured"], label="quiet voices").show()
```

The chart divides each novel into twenty equal slices of 5 % and shows how often the words occur in each slice. Because all three novels run from 0 % to 100 %, you can compare, for example, the opening of *Maisie* with the opening of *The Golden Bowl*, even though one is twice as long as the other.

### Browse the tagged sound events

```python
sound_events("The Golden Bowl", min_loudness=4)      # the loudest sounds in The Golden Bowl
sound_events(contains="violin")                      # every tagged sound that mentions a violin
sound_events("What Maisie Knew", kind="ambient")     # sounds of the world around Maisie
sound_events("Swann in Love", max_loudness=2)        # the quietest sounds in Swann in Love
```

### Change the settings and run everything again

Near the top of the notebook, in the **Configuration** cell, are a few settings you can change before choosing **Run all** again:

| Setting | What it does | Default |
|---|---|---|
| `PROUST_SEGMENT_WORDS` | Length of the segments into which *Swann in Love* is divided, since it has no chapters | `3000` |
| `N_BINS` | Number of slices of narrative time (20 slices = 5 % each) | `20` |
| `ROLLING_EVENTS` | How many sound events are averaged in the loudness-over-time curve. Smaller numbers give a more jagged curve. | `60` |
| `MUSIC_WINDOW` | How many words around an unambiguous music word make an ambiguous one (*note*, *air*, *play*) count as music | `25` |

In section 5 of the notebook you will find the **word lists** that define "music" (`MUSIC_STRICT`, `MUSIC_CONTEXT`, `MUSIC_FIGURATIVE`), and in section 6 the list of hearing words (`HEARING`). They are plain lists of words. Add a word (for example `cello`), remove one you disagree with, then run all cells again and see how the music charts change. Every analytical category in this notebook is a decision someone made, and you can make a different one.

---

## What the notebook measures

All measures are **normalized by length**. Raw counts would mostly tell you that long novels have more of everything.

| Measure | In plain words |
|---|---|
| **Normalized length** | Each novel's word count as a share of the longest one (*The Golden Bowl* = 1.00), and each position in a novel as a percentage of the whole. |
| **Sound event density** | Number of tagged sound passages per 1,000 words, per chapter and per novel. A second version (SED) gives the share of all words that fall inside sound passages. |
| **Speech versus other sounds** | The share of tagged sounds that are verbs of speaking (*said, asked, replied*), other sounds made by characters, and sounds of the surroundings. |
| **Loudness mean** | The average loudness value (1–5) of the tagged sounds. |
| **Loudness standard deviation** | How far the loudness values spread around the average. A small value means most sounds are equally loud (usually the level of ordinary speech, 3). A larger value means the novel moves between whispers and noise. |
| **Music** | Music words in the full text, in three layers: unambiguous (*piano, sonata, Vinteuil*), ambiguous words in a musical context (*phrase, note, air*), and musical vocabulary outside any musical scene (*harmony, pitch, tune*), which may be metaphors. |
| **Hearing** | Words that name the act of hearing (*hear, heard, listen, overheard, ear*), per 1,000 words. |

### Some first findings

These are starting points for discussion, not conclusions:

- *What Maisie Knew* is the densest of the three novels, with 16.9 sound passages per 1,000 words, compared with 9.5 in *The Golden Bowl* and 10.3 in *Swann in Love*.
- In *The Golden Bowl*, 58 % of the tagged sounds are speech.
- The loudness of all three novels clusters at the level of speech (about 3). Within each novel, sounds of the surroundings vary much more in loudness than the characters' sounds.
- *Swann in Love* contains about 22 times as many music words as either James novel. They cluster in two places: the Verdurin evenings (10–25 % of the text) and the soirée at Mme de Saint-Euverte's (70–85 %).
- Only 14 % of the music words in *Swann in Love* fall inside a tagged sound passage. Most of Proust's music is written as perception, memory and thought, which the sound tagging does not capture.
- In James, musical words used *outside* any musical scene (*harmony*, *pitch*, *tune*) outnumber literal music.

---

## Questions to take into the discussion

- **Point of view.** Maisie is the densest text and the one whose heroine knows the world by overhearing. Does the density of sound follow her position in the household? Look at the chapters with the most and the fewest sound passages, and read them.
- **The social world in conversation.** In *The Golden Bowl*, most of the sound is speech. What does it mean for a novel's model of society that its soundscape is almost entirely people talking?
- **Music as metaphor versus music as experience.** James uses *harmony* and *pitch* for relations between people; Proust describes the sound of a violin. Use `concordance("harmony")` and `concordance("phrase")` and compare.
- **What the method cannot see.** If 86 % of Proust's music falls outside the sound tags, what kind of sound is the tagging built to recognize? What kind of listening would a better model need to recognize?
- **Located hearing.** Use `compare_words(["heard", "hear", "listened", "listening"])`. Where in each novel does the narration dwell on the listener rather than on the sound?

---

## What the numbers cannot tell you

Computational results depend on decisions and on imperfect data. Read them with the same skepticism you bring to any edition or translation.

- **The sound tags were produced automatically and contain errors.** Some tags mark words that are not sounds at all. *The Golden Bowl*, for example, contains `<ambient_sound>was somehow</ambient_sound>`. Other sounds were missed. Use `sound_events(...)` to look for errors yourself.
- **One tagging error is corrected in the notebook.** In *What Maisie Knew*, a stray opening tag in chapter XX and a stray closing tag in chapter XXVI made the computer read 26,000 words as a single "sound". The notebook fixes this before counting; see the section "Annotation repair".
- **The loudness values come from a word list**, not from a reader's judgment. Most passages receive the value 3, the level of ordinary speech, and about a third of the passages have no value.
- **Swann in Love is read in English translation.** Every count reflects the translator's word choices as well as Proust's.
- ***Swann in Love* has no chapters in this file.** Its 27 segments are cut mechanically every ~3,000 words, so they do not match any division Proust made.
- **The word lists for music and hearing are short and deliberately simple.** *Air* can be a melody or the atmosphere; *note* can be a musical note or a letter. The notebook only counts such words as music when an unambiguous music word is nearby, and that rule still makes mistakes. The keyword-in-context table lets you check every case.

---

## Glossary

| Term | Meaning |
|---|---|
| **Annotation / tag** | A label added to a text, here `<character_sound>` or `<ambient_sound>` around a passage. |
| **TEI XML** | A widespread standard for encoding literary and historical texts with tags (Text Encoding Initiative). |
| **Token / word** | One word as counted by the computer. Here a word is any run of letters or digits, so *don't* counts as two words (*don* and *t*). |
| **Sound event** | One tagged passage, such as *the violin had risen to a series of high notes*. |
| **Normalization** | Dividing a count by a length, so that texts of different sizes can be compared ("per 1,000 words"). |
| **Narrative time** | A position in the text as a percentage of its length, from 0 % (first word) to 100 % (last word). |
| **Mean** | The average. |
| **Standard deviation** | A measure of spread: roughly, how far a typical value lies from the average. |
| **Rolling mean** | An average over a window that moves through the text, here over 60 consecutive sound events. It shows trends without the noise of single values. |
| **Concordance / KWIC** | "Keyword in context": every occurrence of a word, shown with the words around it. |
| **Lexicon** | Here, a hand-made list of words that defines a category such as music. |
| **Python** | The programming language used in the notebook. |
| **Jupyter notebook** | A document (file ending `.ipynb`) that combines text, code and results. |
| **Cell** | One block of a notebook, either text or code. |
| **Kernel** | The program that runs the code cells in the background. "Restart the kernel" means: forget everything and start again. |
| **Library / package** | Ready-made code that others have written. The notebook uses *pandas* (tables), *lxml* (reading XML), *plotly* (interactive charts) and *scipy* (statistics). |

---

## Running the notebook on your own computer

This is only necessary if you want to work offline or keep your changes permanently.

1. Install **Anaconda** from [anaconda.com/download](https://www.anaconda.com/download). It includes Python, Jupyter and most of the libraries needed.
2. Download this repository: on the GitHub page, click the green **Code** button, then **Download ZIP**, and unzip the file.
3. Open **Anaconda Navigator** and launch **JupyterLab**.
4. In JupyterLab's file browser on the left, navigate to the unzipped folder and double-click `Sound_in_James_and_Proust.ipynb`.
5. The first time only, install the remaining libraries: create a new code cell at the top, type `%pip install -r requirements.txt`, and press Shift + Enter. Then delete that cell.
6. Choose **Run → Run All Cells**.

The notebook rewrites `Sound_in_James_and_Proust_report.html` and the charts in `html_visualizations/` every time it runs, so the report always reflects your current settings and word lists.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `NameError: name '...' is not defined` | An earlier cell has not run. Choose **Run all**. |
| `FileNotFoundError` for an XML file | The notebook cannot find the `data/` folder. On your own computer, make sure the notebook is in the same folder as `data/`. In Colab, run the first code cell, which downloads the data. |
| `ModuleNotFoundError: No module named 'plotly'` (or another name) | A library is missing. Run `%pip install -r requirements.txt` in a cell, then restart the kernel. |
| Charts do not appear | Run the cell again. In JupyterLab on your own computer, make sure you opened the notebook in JupyterLab or Jupyter Notebook, not in a plain text editor. |
| A concordance finds nothing | Check spelling, and remember that the translation of Proust is in British English (*colour*, *honour*). |
| Everything is slow or frozen | Restart: **Runtime → Restart and run all** (Colab) or **Kernel → Restart Kernel and Run All Cells** (Jupyter). |

---

## What is in this repository

```
├── README.md                                  this guide
├── Sound_in_James_and_Proust.ipynb            the notebook: analysis + playground
├── Sound_in_James_and_Proust_report.html      all results as one web page (download and open)
├── html_visualizations/                       the charts one by one, plus tables as CSV files
│   ├── 01_text_length.html … 14_hearing_narrative_time.html
│   ├── chapter_metrics.csv                    every measure for every chapter (opens in Excel)
│   ├── text_summary.csv, loudness_summary.csv, length_summary.csv
│   ├── music_kwic.csv                         every music word with its context
│   └── plotly.min.js                          needed by the chart files
├── data/
│   ├── James_Henry_What_Maisie_Knew.xml       sound-annotated novels (TEI XML)
│   ├── James_Henry_The_Golden_Bowl.xml
│   ├── Proust_Swann_in_Love.xml
│   └── English_texts_LL_predicted.csv         list of all sound passages per novel (used as a cross-check)
└── requirements.txt                           list of Python libraries (used by Binder and for local installs)
```

The CSV files in `html_visualizations/` open in Excel, Numbers or Google Sheets, if you prefer to explore the numbers in a spreadsheet.
