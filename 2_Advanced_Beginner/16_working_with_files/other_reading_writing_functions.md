---
parent: Using Files 
layout: material 
nav_order: 2
title: Other reading and writing functions
topic: "other_reading_writing_functions"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Other file-reading/saving functions

Even though R has a standard low-level interface, most functions do not require more than just a path to a target file.

The exact function that we have to use depends on both the file type, and the kind object that we want to read/write. The interface will be similar for most: 

- Reading: `<RobjectName> <- <readerFunction>( file= <pathToFile> )`
- Writing: `<writerFunction>( <RobjectName>, file = <pathToFile> )` 

The path is given as a single character string, as above. 

Every other file reading/saving function works the same basic way, although you might have to set additional arguments. Such functions are used to read and write files that can be read in by other programs. Here are a couple of examples:

# List of functions

| Package | R data         | File              | Reading         | Writing        | Comment                                   |
|---------|----------------|-------------------|-----------------|----------------|-------------------------------------------|
| *base*  | Any            | R binary (.rds)   | `readRDS()`     | `saveRDS()`    | The **contents** of **one** object.       |
| *base*  | Any (multiple) | R binary (.RData) | `load()`        | `save()`       | Includes object name.                     |
| *base*  | vectors        | text (.txt)       | `scan()`        | `cat()`        |                                           |
| *utils* | data.frame     | text              | `write.table()` | `read.table()` | General for tabular data                  |
| *utils* | data.frame     | text (.csv)       | `write.csv()`   | `read.csv()`   | Arguments default for csv                 |
| *utils* | data.frame     | text (.tab)       | `write.table()` | `read.delim()` | Arguments default for space/tab-delimited |














