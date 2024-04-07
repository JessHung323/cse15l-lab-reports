# Week 1 Lab Report
## Remote Access and FileSystem

### Basic Commands
Command `cd`
- `cd` with _no_ arguments
```
(base) jessica@Jessicas-Air-3 cse15l-lab-reports % cd
(base) jessica@Jessicas-Air-3 ~ % 
```
- `cd` with path to a _directory_ as an argument
```
(base) jessica@Jessicas-Air-3 ~ % cd Desktop  
(base) jessica@Jessicas-Air-3 Desktop % 
```
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
(base) jessica@Jessicas-Air-3 Desktop % cat Academics/2023-2024/SP24/CSE15L/cse15l-lab-reports/index.md
# CSE 15L SP24 Lab Reports

## Lab reports
- Week 1 Lab Report:
[Link Text](week1_lab_report.md)


<a href="random.md" title="random.md">Just a random test file -- Please click</a>

**Course assignments**
- Lab reports
- Quizzes
- Skill test
- In-class exercise
---
_Some elements on cheatsheet_
![Image](https://today.ucsd.edu/news_uploads/_social/img-primary-Geisel-UCSanDiego-ErikJepsen-090922.jpg)
---
> What is a blockquote? What is a `Python`
---
## What is this class about
1. manage files and programs from the command line
2. keyboard shortcuts
3. techniques for managing data and programs

More code blocks

```
print('Hello World')
print('This is CSE15L')
```
```