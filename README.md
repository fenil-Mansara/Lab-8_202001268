# Lab-8_202001268
# Name : Fenil Mansara
# ID : 202001268

## 1. Creating a new Eclipse project, and within the project create a package and defining the class.

![image](https://user-images.githubusercontent.com/84991028/233600221-8c3bda52-dfbf-4133-98bd-0f07d5dcc5bb.png)

## 2. Test method to test the behaviour of the Boa class :
```
package testing;
import static org.junit.jupiter.api.Assertions.*;
import org.junit.*;
import org.junit.jupiter.api.Test;
class BoaTest {
	 @Test
	  public void testIsHealthy() {
	    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
	    Assert.assertTrue(healthyBoa.isHealthy());
	   
	    Boa sickBoa = new Boa("Sneaky", 6, "mice");
	    Assert.assertFalse(sickBoa.isHealthy());
	  }
	  @Test
	  public void testFitsInCage() {
	    Boa smallBoa = new Boa("Tiny", 2, "rats");
	    Assert.assertTrue(smallBoa.fitsInCage(5));
	    Assert.assertFalse(smallBoa.fitsInCage(1));
	    Boa largeBoa = new Boa("Goliath", 20, "chicken");
	    Assert.assertTrue(largeBoa.fitsInCage(25));
	    Assert.assertFalse(largeBoa.fitsInCage(10));
}
}
```
![image](https://user-images.githubusercontent.com/84991028/233600666-23eb1971-b4c0-44ce-8aba-61d83285f89f.png)

## 3. Modified setUp() method in the BoaTest class :
```
public class BoaTest {
	private Boa jen;
   private Boa ken;
  
   @Before
   public void setUp() throws Exception {
       jen = new Boa("Jennifer", 2, "grapes");
       ken = new Boa("Kenneth", 3, "granola bars");
   }
}
```
## 4. Modified testIsHealthy() method in the BoaTest class :
```
@Test
   public void testIsHealthy() {
       // check that jen is not healthy
       assertFalse(jen.isHealthy());
      
       // check that ken is healthy
       assertTrue(ken.isHealthy());
   }

```

## 5. Modified testFitsInCage() method in the BoaTest class :
```
 @Test
   public void testFitsInCage() {
       // Test for jen
       assertFalse(jen.fitsInCage(1)); // cage length is less than length of boa
       assertTrue(jen.fitsInCage(2)); // cage length is equal to length of boa
       assertTrue(jen.fitsInCage(3)); // cage length is greater than length of boa
       // Test for ken
       assertFalse(ken.fitsInCage(2)); // cage length is less than length of boa
       assertTrue(ken.fitsInCage(3)); // cage length is equal to length of boa
       assertTrue(ken.fitsInCage(4)); // cage length is greater than length of boa
   }

```
## 6. Running test cases : 
![image](https://user-images.githubusercontent.com/84991028/233601110-a30b2512-26b9-4898-b275-3f566d33a5f1.png)

## 7. Here's the modified Boa class with the new lengthInInches() method:
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;

    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }

    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }

    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```

## Here's an example of a new test case in the BoaTest class that tests the lengthInInches() method:
```
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
Running test cases : 

![image](https://user-images.githubusercontent.com/84991028/233601361-48aefbff-becd-4723-b207-00a41da246b7.png)

