# Lab Report 3
## Servers & SSH Keys

### Part 1
Suppose the `StringChecker` interface is implemented as follows:
```
class StringLength implements StringChecker {
    private String stringToCheck;

    public StringLength(String inputString) {
        this.stringToCheck = inputString;
    }

    @Override
    public boolean checkString(String s) {
        return this.stringToCheck.length() < s.length();
    }
}
```
- failure-inducing input:
```
@Test
public void testFilterWithStringLength() {
    List<String> input = Arrays.asList("hello", "world", "example", "javaisthebest", "code");
    StringChecker checker = new StringLength("hello");

    List<String> expected = Arrays.asList("example", "javaisthebest");
    List<String> actual = ListExamples.filter(input, checker);

    assertEquals(expected, actual);
}
```
- no-failure input:
```
@Test
public void testFilterWithStringLengthPass() {
    List<String> input = Arrays.asList("hello", "world", "example", "javaisthebest", "code");
    StringChecker checker = new StringLength("JavaIsBest!");

    List<String> expected = Arrays.asList("javaisthebest");
    List<String> actual = ListExamples.filter(input, checker);

    assertEquals(expected, actual);
}
```
- ![Image](assets/lab03.png)
- Fix Bugs
    - Before: 
        - ```
        static List<String> filter(List<String> list, StringChecker sc) {
            List<String> result = new ArrayList<>();
            for(String s: list) {
                if(sc.checkString(s)) {
                    result.add(0, s);
                }
            }
            return result;
        }
        ```
    - After: 
        - ```
        static List<String> filter(List<String> list, StringChecker sc) {
            List<String> result = new ArrayList<>();
            for(String s: list) {
                if(sc.checkString(s)) {
                    result.add(s);
                }
            }
            return result;
        }
        ```
- This fixed the bug as originally the `0` in the method argument asks the method to add the second argument to the first position of the arraylist. By removing the optional index argument, `.add()` adds to the end of the arraylist by default, hence preserving the order as desired.

### Part 2
I choose to look further into the command `grep`. Here are 4 different and interesting ways to work with the `grep` command:
1. `grep -r --exclude-dir='excluded_dir' 'pattern' /path/to/directory`
    - ```
        (base) jessica@Jessicas-Air-3 technical % grep -r --include='*.txt' --exclude-dir='biomed' '' . | head -n 5
        ./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt:
        ./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt:
        ./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt:
        ./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt:
        ./government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt:SUPREME COURT OF THE UNITED STATES
        ```
    - ```
        (base) jessica@Jessicas-Air-3 technical % grep -r --include='*.txt' --exclude-dir='biomed' --exclude-dir='government' '' . | tail -n 5
        ./911report/chapter-11.txt:                Back-page notices told of tightened security at embassies and military installations
        ./911report/chapter-11.txt:                abroad and government cautions against travel to the Arabian Peninsula. All the rest
        ./911report/chapter-11.txt:                was secret.
        ./911report/chapter-11.txt:        
        ./911report/chapter-11.txt:    
        ```
    - This command tries to find the pattern in given directory, exluding the subdirectory that is provided as an argument. This can be helpful when you only want to look into specific subdirectories, as you can specify more than one subdirectory to *not* look into.