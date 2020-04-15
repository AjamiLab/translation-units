# translation-units

Python scripts to manipulate digitized texts

Use `to-md.py` to convert a tabular text format (a tsv file) exported from Tropy into a plain text prose format (a txt or markdown file) that can be used for a critical edition style text for publication.

Use `to-tsv.py` to convert a critical edition style text written using markdown (following a few standards laid out below) into a tabular format (a tsv file) with all formatting and footnotes removed.

## `to-md.py`
A python script to convert a tab-separated value (tsv) file of an aligned parallel text to a markdown text file in a prose-like format.

### Instructions

- Download the python script `to-md.py`

- Place it in the folder along with the TSV file that you would like to convert to a markdown file.

- Open your terminal and navigate to the folder where the script and your file are

- Run the script by typing in `python to-md.py` PLUS the name of your file.

  All together, this means you type something like this, for example:

  `python to_md.py manuscript.tsv`

### Formatting specifications

Input file notes:

- The input file must be a tab-separated value file
- The first row must be a series of headers (e.g., _ID --> Arabic --> Soninke --> English_)
- The first column must be **identifiers** for the segments
- The TSV can have as many columns as you want

Output file notes:

- **Identifiers** become level three markdown headers via three hashtag marks (`###`)
- Language segments become markdown paragraphs (that is, with an empty line between them)

### Ajami Lab Use

This script was designed in the context of the [Ajami Lab](https://ajami.hypotheses.org/) to facilitate the conversion of [Ajami annotation data extracted from a Tropy project](https://ajami.hypotheses.org/598) into a format conducive to prose-like publication (as a critical edition style chapter, appendix, etc).

Once a TSV is put into markdown format, it can easily be edited further using [pandoc](https://pandoc.org/) flavored markdown that allows for footnotes, etc., and then easily exported as a static html page or common word-processing file for Word, LibreOffice, etc.

From this perspective, the Tropy project is the single or master "source code" for export to other formats (tabular or text) designed for further analysis or publication.

### Screenshots

Go from something like this:

<img width="598" alt="tabbed" src="https://user-images.githubusercontent.com/28364193/79261297-ea076e00-7e8f-11ea-9c36-1303c93b467b.png">o 

To this:

<img width="272" alt="prose" src="https://user-images.githubusercontent.com/28364193/79261247-d65c0780-7e8f-11ea-97bf-000339f0421a.png">

## `md-to-tsv`

A python program to convert a critical edition translation text (that is, a source text with translation into one or multiple languages plus annotations/commentary in the form of footnotes) from a plain-text file written using [pandoc](https://pandoc.org/) flavored markdown into an un-annotated tsv useful for further analysis with other software.

### How to use

- Download the python script `to-tsv.py`

- Place it in the folder along with the annotated text markdown file that you would like to convert to an un-annotated TSV

- Open your terminal and navigate to the folder where the script and your file are

- Run the script by typing in `python to-tsv.py` PLUS a list of the languages (e.g., `Jula English Arabic`) with each language separated by a space PLUS the name of your file.

  All together, this means you type something like this, for example:
  
  `python to_tsv.py Jula English Arabic text.md`

### Markdown formatting specifications

- Each translation unit must start with `###`. 

- Source language and target language segments are separated by new lines. You can have as many target languages as you want. 

- Each translation unit must be have the same number of segments (that is, one for each language) in the same order.

- Footnotes can be placed at the end of a segment or within a segment (BUT see below for a note on RTL scripts)

- You can place translation segments within underscores (e.g., `_bonjour_`; you may want this markup/formatting for other outputs such Word/LibreOffice docs or HTML files). They will be stripped from the TSV output.

Here's an example of a single translation unit of a text using Jula, English and Arabic:

```
### 4.2.2
   
ka na ele[^862c] ma
   
_and came to you_
   
إِلَيْكَ
   
[^862c]: This refers to Muhammad.
```

### Special Notes for Ajami documents and right-to-left scripts such as Arabic

- Do not place footnotes on any lines written in Arabic script (or a right-to-left script segment, in general) since the mixing of LTR and RTL doesn't work nicely

### Ajami Lab Use

This program was originally written to facilitate an Ajami Lab research workflow where I digitized a hand-written notebook from lessons in Jula-language Quranic exegesis that I took. It could be useful for others working from a similar context of handwritten notes.

For working from digital manuscripts, it is likely better to start with [Tropy](https://tropy.org/) in the worfklow discussed here and then use [tsv-to-md](https://github.com/donaldsoncd/tsv-to-md) instead of this program.

### Screenshots

Go from this:

<img width="791" alt="markdown input" src="https://user-images.githubusercontent.com/6858318/78091543-61b2a480-738a-11ea-90eb-0b6323ae83ae.png">

To this:

<img width="698" alt="tsv output" src="https://user-images.githubusercontent.com/6858318/78091554-68411c00-738a-11ea-8e4a-d81fb4b29e1c.png">

