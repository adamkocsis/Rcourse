---
parent: Using Files 
layout: material 
nav_order: 3
title: Paths and working directories
topic: "paths_and_working_directories"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Location of exported files

Let's check the example from [earlier]({{site.url}}{{site.baseurl}}/2_Advanced_Beginner/09_working_with_files/reading_and_saving_vectors.html). 

```R
# an example vector
example <- c(1, 2, 3, 4, 5)
saveRDS(example, file="example.rds")
```

We now know how to save data into files and how to read them back into R. But where is our file? 

# Absolute paths

Every file on your computer can be found using the **path** to it. This is a single **character string**, which is an unambiguous way to find data on your hard drive. We usually refer to the complete path as **absolute paths** as they are not dependent on where we are in the file system, when we look at it.  

Paths are pretty straightforward, but they are somewhat different on Windows and UNIX-like computers:

### Windows paths

There are three things that need to be noted about windows paths:

1. The paths on Windows start with a letter-colon combination, that represents the 'drive', where the file is located. For historical reasons, the Windows files themselves are on the `C:` drive.

2. Windows paths do not differentiate between lower and uppercase characters.

3. Windows uses **backslashes** to notate directory hierarchy. For instance

```
C:\direct\myfile.rds
```

path indicates a file `myfile.rds` which is in the `direct` directory (also called a folder on Windows) on the `C:` drive. 

### Unix paths

Practically every other operating system (such as MacOS or GNU/Linux) uses UNIX-style paths, which means that... 

1. the paths start with the file system root `/`

2. The lower and upper case paths are different. You can have both a `export` and `Export` directory in the same directory and they will be different.

3. Most importantly, the hierarchy is indicated by **forward slashes**.  

```
/home/adam/myfile.rds
```

This points to `myfile.rds` file in adam's home directory. 


### Windows Paths in R

R uses the paths that your system uses, with one important thing to note: since R is coming from the GNU ecosystem, it is exclusively using **forward slashes** for the notation of directory hierarchy. This means that **R on Windows is also using forward slashes**. 

Therefore, the Windows path from above:

```
C:\direct\myfile.rds
```

is represented in R as

```
C:/direct/myfile.rds
```


# Writing files with absolute paths

Let's create the file with the path above! **NOTE: this example works only on Windows computers.** However, if you have Mac or Linux you should still be able to figure this out if you follow along. 

### Creating directories

First, let's create a directory where we can export our file. You can create directories from within R using the `dir.create()` function, that requires the absolute path of the newly created directory.

```R
dir.create("C:/direct")
```

which will create the `direct` directory in the root of the `C:` drive.

### Writing file into the directory

Now that we have a directory to write to, we can write our example file into it. Using another example vector, you can accomplish this with:

```R
# an example vector
other <- c(0, 2, 4, 6)
saveRDS(other, file="C:/direct/myfile.rds")
```

The file should now be in the `direct` directory. 

#### Reading the file in

You can also read the file with the absolute path:

```R
# an example vector
other2 <- readRDS(file="C:/direct/myfile.rds")
```

# Relative paths

Providing the entire absolute path to a file as a character string includes system (and user!)-specific details. This variance among the absolute paths makes transferring of code (portability) from one system to another quite problematic - for instance, a Mac does not even have a `C:` drive. 

Also, when we are writing code, we actually have to write out our long paths, even when they are quite long, and if they occurr multipe times.

### Working directories

At any given time, there is an active **working directory**, which is used as a reference point for all file operations.

You can see what the currently active working directory is, if you call to the `getwd()` function.
```R
getwd()
```
```
[1] "C:/Users/Adam/Documents"
```

![img]({{site.url}}{{site.baseurl}}/images/RStudio_getwd.png)

The file you exported at the beginning of this section should be there. Note that the tilde represents the user's home directory. 

```R
newExampleAgain <- readRDS(file="example.rds")
newExampleAgain
```
```
[1] 1 2 3 4 5
```

The working directory helps with simplifying the paths: the working directories are reference points in the paths. When we use a file, such as in the code above, we actually refer to 

```R
# construction of the absolute path
absolutePath <- paste(getwd(), "example.rds", sep="/")
newExample <- readRDS(file=absolutePath)
```

This `paste(getwd(), "example.rds", sep="/")` is actually a programmatic way to represent the absolute path to our file, concatenating the working directory with the relative path: the name of our file. 

# Setting the working directory

We usually organize files that belong to the same project in a single directory. Normally this is set to be the working directory of the project at the beginning of a script with the `setwd()` function.

For instance, if I want to set my working directory to be the `C:/direct` directory that we created earlier, I can do that with this line of code:

```R
setwd("C:/direct")
```

The function will not return anything, indicating that the setting of the working directory happened. If you mess up the path to the working directory, you will get an error message - which indicates that your path is wrong.  

If you have doubts after running this line of code, you can run

```R
getwd()
```
```
[1] "C:/direct"
```

to confirm this. Now you can use the script below to read in the file that we exported with its absolute path.

```R
# an example vector
other3 <- readRDS(file="myfile.rds")
other3
```
```
[1] 0 2 4 6
```












