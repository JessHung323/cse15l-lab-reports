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