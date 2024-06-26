# Lab Report 5
## Putting It All Together

### Part 1
- Original Post
    - I am trying to finish a grader bash script that grades all the java test files in the current directory. The script should print out the test outcome for each test file. However, I can't seem to get the number of tests passed / failed when there is a test that did not work out. I think there might be some issue with how I parsed and extracted the information from the default ouput after running the tests. The below is the symptom from my terminal.
    - ![Image](assets/lab5_01.png)
- TA Response
    - Hi, I would suggest that you add some echo statements in the case that deals with test files with failing test cases. You can echo the variables that store the number of failed test and number of total tests to see if you have the correct numbers that you are expecting.
- Student Followup
    - Hi, I tried your suggestions and here is the output I got.
    - ![Image](assets/lab5_02.png)
    - I think the bug is from how I assigned the wrong number to the variables I'm using.
- The file and directory structure
    - ```
        .
        ├── ArrayExamples.class
        ├── ArrayExamples.java
        ├── ArrayTests.class
        ├── ArrayTests.java
        ├── ContainsCharacterChecker.class
        ├── FileExample.class
        ├── FileExample.java
        ├── LinkedList.class
        ├── LinkedListExample.java
        ├── ListExamples.class
        ├── ListExamples.java
        ├── ListTests.class
        ├── ListTests.java
        ├── Node.class
        ├── StringChecker.class
        ├── StringLength.class
        ├── grader.sh
        └── lib
            ├── hamcrest-core-1.3.jar
            └── junit-4.13.2.jar
        ```
    - Content in `ArrayTests.java`
        - ```
            import static org.junit.Assert.*;
            import org.junit.*;

            public class ArrayTests {
                @Test 
                public void testReverseInPlace() {
                int[] input1 = { 3 };
                ArrayExamples.reverseInPlace(input1);
                assertArrayEquals(new int[]{ 3 }, input1);
                }


            @Test
            public void testReversed() {
                int[] input1 = { };
                assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
            }

            @Test
            public void testReverseInPlace2() {
                int[] input2 = {1, 2};
                ArrayExamples.reverseInPlace(input2);
                assertArrayEquals(new int[]{2, 1}, input2);
            }

            @Test
            public void testReversed2() {
                int[] input2 = {1};
                assertArrayEquals(new int[]{1}, ArrayExamples.reversed(input2));
            }
            }
            ```
    - Content in `ListTests.java`
        - ```
            import static org.junit.Assert.*;
            import org.junit.*;
            import java.util.*;

            public class ListTests {
                @Test
                public void testFilterWithStringLengthFail() {
                    List<String> input = Arrays.asList("hello", "world", 
                        "example", "javaisthebest", "code");
                    StringChecker checker = new StringLength("hello");

                    List<String> expected = Arrays.asList("example", 
                        "javaisthebest");
                    List<String> actual = ListExamples.filter(input, checker);

                    assertEquals(expected, actual);
                }
                @Test
                public void testFilterWithStringLengthPass() {
                    List<String> input = Arrays.asList("hello", "world", 
                        "example", "javaisthebest", "code");
                    StringChecker checker = new StringLength("JavaIsBest!");

                    List<String> expected = Arrays.asList("javaisthebest");
                    List<String> actual = ListExamples.filter(input, checker);

                    assertEquals(expected, actual);
                }
            }
            ```
    - Content in `grader.sh`
        - ```
            CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

            run_tests() {
            local test_file=$1
            local test_class=${test_file%.java}

            javac -cp $CPATH $test_file

            if [ $? -ne 0 ]; then
                echo "Compilation failed for $test_file"
                return
            fi

            local test_output=$(java -cp "$CPATH" org.junit.runner.JUnitCore 
                "$test_class")

            echo "Raw JUnit test output for $test_class:"

            local test_summary=$(echo "$test_output" | grep -E "OK|Failures")

            local num_tests=0
            local num_failures=0
            local num_passed=0

            if [[ "$test_summary" == *"OK"* ]]; then
                num_tests=$(echo "$test_summary" | awk -F '[()]' '{print $2}' 
                    | awk '{print $1}')
                num_passed=$num_tests
            else
                echo "SUMMARY: $test_summary"
                num_failures=$(echo "$test_summary" | grep -oE "[0-9]+" 
                    | head -n 1)
                num_tests=$(echo "$test_summary" | grep -oE "[0-9]+" 
                    | tail -n 1)

                if [[ -z "$num_failures" ]]; then
                num_failures=0
                fi

                if [[ -z "$num_tests" ]]; then
                num_tests=0
                fi

                echo $num_failures
                echo $num_tests
                num_passed=$((num_tests - num_failures))
            fi

            echo "Results for $test_class:"
            echo "Total tests run: $num_tests"
            echo "$num_passed tests passed, $num_failures tests failed."
            echo
            }

            for test_file in *.java; do
            if [[ $test_file == *Tests.java ]]; then
                run_tests "$test_file"
            fi
            done
            ```
    - I have to switch the `head` to `tail` and `tail` to `head` when extracting the number of tests in the condition dealing with having failed cases.

### Part 2
Something cool that I learned in the second half of the quarter is to write my own grading script in bash. I have always wonders how the programming assignments are graded automatically by running the grading scripts against the test files for some of my classes. I learned how to store the information using echo and the specific syntax bash has in the grading script and I think it's very cool and useful.