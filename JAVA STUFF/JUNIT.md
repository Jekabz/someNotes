# JUNIT

* Framework to write repeatable tests

```Java
import org.junit.*;

public class FoobarTest {
    @BeforeClass
    public static void setUpClass() throws Exception {
        // Code executed before the first test method       
    }

    @Before
    public void setUp() throws Exception {
        // Code executed before each test    
    }
 
    @Test
    public void testOneThing() {
        // Code that tests one thing
    }

    @Test
    public void testAnotherThing() {
        // Code that tests another thing
    }

    @Test
    public void testSomethingElse() {
        // Code that tests something else
    }

    @After
    public void tearDown() throws Exception {
        // Code executed after each test   
    }
 
    @AfterClass
    public static void tearDownClass() throws Exception {
        // Code executed after the last test method 
    }
}
```
---------------------

#### ASSERTIONS

* JUnit has assertion methods for all Java Objects and primitive types and arrays of them
* Parameter order:
  * String message shown if assert fails (optional)
  * Expected value (if the assertion knows the expected value (assertNotNull etc.), this is not needed)
  * Actual value (recieved)
```java
  @Test
  public void testAssertNotSame() {
    assertNotSame("should not be same Object", new Object(), new Object());
  }
```
* __assertThat__ :
  * Parameter order:
    * String message shown if assert fails (optional)
    * Actual value (recieved)
    * `Matcher` object


