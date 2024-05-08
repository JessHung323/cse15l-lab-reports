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
    - ```
    @Test
    public void testFilterWithStringLength() {
        List<String> input = Arrays.asList("hello", "world", "example", "javaisthebest", "code");
        StringChecker checker = new StringLength("hello");

        List<String> expected = Arrays.asList("example", "javaisthebest");
        List<String> actual = ListExamples.filter(input, checker);

        assertEquals(expected, actual);
    }```
- no-failure input:
    - ```
    @Test
    public void testFilterWithStringLengthPass() {
        List<String> input = Arrays.asList("hello", "world", "example", "javaisthebest", "code");
        StringChecker checker = new StringLength("JavaIsBest!");

        List<String> expected = Arrays.asList("javaisthebest");
        List<String> actual = ListExamples.filter(input, checker);

        assertEquals(expected, actual);
    }```
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
        }```
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
        }```
- This fixed the bug as originally the `0` in the method argument asks the method to add the second argument to the first position of the arraylist. By removing the optional index argument, `.add()` adds to the end of the arraylist by default, hence preserving the order as desired.