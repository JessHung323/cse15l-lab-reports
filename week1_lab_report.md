# Week 1 Lab Report
## Remote Access and FileSystem

### Basic Commands
Command `cd`
- `cd` with _no_ arguments
    - Absolute path: `/Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports`
    - ```
        (base) jessica@Jessicas-Air-3 cse15l-lab-reports % cd
        (base) jessica@Jessicas-Air-3 ~ % 
        ```
    - Explanation: Since `cd` is executed without argument, this returns back to the user's home directory by default, and no error occurred.
- `cd` with path to a _directory_ as an argument
    - Absolute path: `/Users/jessica`
    -  ```
        (base) jessica@Jessicas-Air-3 ~ % cd Desktop
        (base) jessica@Jessicas-Air-3 Desktop % 
        ```
    - Explanation: Since `Desktop` is an existing directory in the working directory, `cd Desktop` changes directory to `Desktop` without error.
- `cd` with path to a _file_ as an argument
```
(base) jessica@Jessicas-Air-3 Desktop % cd Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
cd: not a directory: Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
(base) jessica@Jessicas-Air-3 Desktop % 
```

Command *ls*
- `ls` with _no_ arguments
```
(base) jessica@Jessicas-Air-3 cse15l-lab-reports % ls
_config.yml		random.md
index.md		week1_lab_report.md
```
- `ls` with path to a _directory_ as an argument
```
(base) jessica@Jessicas-Air-3 cse15l-lab-reports % ls ~/Desktop/Academics/2023-2024/SP24/CSE15L
1861712254246_.pic.jpg		cse15l-lab-reports
1871712254249_.pic.jpg		week1_wed_lecture_wsh.pdf
```
- `ls` with path to a _file_ as an argument
```
(base) jessica@Jessicas-Air-3 cse15l-lab-reports % ls ~/Desktop/Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
/Users/jessica/Desktop/Academics/2023-2024/SP24/CSE15L/1861712254246_.pic.jpg
```

Command `cat`
- `cat` with _no_ arguments
```
(base) jessica@Jessicas-Air-3 Desktop % cat
^C
(base) jessica@Jessicas-Air-3 Desktop % 
```
- `cat` with path to a _directory_ as an argument
```
(base) jessica@Jessicas-Air-3 Desktop % cat Academics
cat: Academics: Is a directory
```
- `cat` with path to a _file_ as an argument
```
(base) jessica@Jessicas-Air-3 Desktop % cat Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports/random.txt
random words
```