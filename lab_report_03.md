# Lab Report 3
## Servers & SSH Keys

### Part 1
The bug I chose from the previous lab is from the following code snippet:
```
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

This code aims to *returns a new list that has all the elements of the input list for which the StringChecker returns true, and not the elements that return false, in the same order they appeared in the input list*

The bug is from how the elements are added to the front of the list, hence not preserving the original order.

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

- failure-inducing input
    - ```
    @Test
    public void testFilterWithStringLength() {
        List<String> input = Arrays.asList("hello", "world", "example", "javaisthebest", "code");
        StringChecker checker = new StringLength("hello");

        List<String> expected = Arrays.asList("example", "javaisthebest");
        List<String> actual = ListExamples.filter(input, checker);

        assertEquals("The filtered list should only contain elements in 'hello'.", expected, actual);
    }
```