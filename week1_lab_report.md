# Week 1 Lab Report
## Remote Access and FileSystem

### Basic Commands
Command `cd`
- `cd` with _no_ arguments
    - _Absolute path_: `/Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports`
    - ```
        (base) jessica@Jessicas-Air-3 cse15l-lab-reports % cd
        (base) jessica@Jessicas-Air-3 ~ % 
        ```
    - _Explanation_: Since `cd` is executed without argument, this returns back to the user's home directory by default, and no error occurred.
- `cd` with path to a _directory_ as an argument
    - _Absolute path_: `/Users/jessica`
    -  ```
        (base) jessica@Jessicas-Air-3 ~ % cd Desktop
        (base) jessica@Jessicas-Air-3 Desktop % 
        ```
    - _Explanation_: Since `Desktop` is an existing directory in the working directory, `cd Desktop` changes directory to `Desktop` without error.
- `cd` with path to a _file_ as an argument
    - _Absolute path_: `/Users/jessica/Desktop`
    - ```
        (base) jessica@Jessicas-Air-3 Desktop % cd Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
        cd: not a directory: Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
        (base) jessica@Jessicas-Air-3 Desktop % 
        ```
    - _Explanation_: `cd` is used when one wants to change into a directory. In this case where we pass in a _file_ as an argument, although the relative file path is valid, an error occurred indicating that the file is not a directory.

Command `ls`
- `ls` with _no_ arguments
    - _Absolute path_: `/Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports`
    - ```
        (base) jessica@Jessicas-Air-3 cse15l-lab-reports % ls
        _config.yml		random.md
        index.md		week1_lab_report.md
        ```
    - _Explanation_: `ls` without arguments is used to list all the existing files and folders in the working directory, hence the observable output are the files in this directory and no error occurred.
- `ls` with path to a _directory_ as an argument
    - _Absolute path_: `/Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports`
    - ```
        (base) jessica@Jessicas-Air-3 cse15l-lab-reports % ls ~/Desktop/Academics/2023-2024/SP24/CSE15L
        1861712254246_.pic.jpg		cse15l-lab-reports
        1871712254249_.pic.jpg		week1_wed_lecture_wsh.pdf
        ```
    - _Explanation_: Given a valid relative file path, `ls <filepath>` lists the files and folders in the given directory and executes without error.
- `ls` with path to a _file_ as an argument
    - _Absolute path_: `/Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports`
    - ```
        (base) jessica@Jessicas-Air-3 cse15l-lab-reports % ls ~/Desktop/Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
        /Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
        ```
    - _Explanation_: As mentioned above, `ls` is essentially used to list existing files in a directory, since this file does not exist in the current working but in the parent directory, it returns the absolute file path instead and no error occurs.

Command `cat`
- `cat` with _no_ arguments
    - _Absolute path_: `/Users/jessica/Desktop`
    - ```
        (base) jessica@Jessicas-Air-3 Desktop % cat
        ^C
        (base) jessica@Jessicas-Air-3 Desktop % 
        ```
    - _Explanation_: `cat` is used for multiple reasons, however when its not given an argument, it does not know which file it should look at hence the terminal fails to return an output as it continues to run, forcing control C to be applied to end the execution. This is an error, requiring keyboard interruption.
- `cat` with path to a _directory_ as an argument
    - _Absolute path_: `/Users/jessica/Desktop`
    - ```
        (base) jessica@Jessicas-Air-3 Desktop % cat Academics
        cat: Academics: Is a directory
        ```
    - _Explanation_: Since `cat` is to be used with a path to a _file_ instead of _directory_, giving it a directory path would result in error indicating that the directory is not a file.
- `cat` with path to a _file_ as an argument
    - _Absolute path_: `/Users/jessica/Desktop`
    - ```
        (base) jessica@Jessicas-Air-3 Desktop % cat Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports/random.txt
        random words
        ```
    - _Explanation_: When given a valid path to a file, `cat` would display the content of the file in the terminal with no error.