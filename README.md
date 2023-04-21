# Lab-8_202001433
## Name : Deep Modiya
### Date: 21-04-23
## 1. Creating a new Eclipse project, package and the class as mentioned.
![image](https://user-images.githubusercontent.com/99895157/233593831-b1486bb7-c94c-438f-a612-ece7d53dd104.png)
## 2. Test method for the Boa class :
import org.junit.Assert;
import org.junit.Test;
public class BoaTest {

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


![image](https://user-images.githubusercontent.com/99895157/233594566-fb054c16-f462-47bf-8054-c75af65269f0.png)
## 3. Modified setUp() method in the BoaTest class :
public class BoaTest {
    private Boa jen;
    private Boa ken;
    
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
    
    // write test methods here
}

![image](https://user-images.githubusercontent.com/99895157/233596466-5d83e8c9-cbee-4c5a-ad8f-03fa187980da.png)

## 4. Modified testIsHealthy() method in the BoaTest class :
@Test
public void testIsHealthy() {
    // check that jen is not healthy
    assertFalse(jen.isHealthy());
    
    // check that ken is healthy
    assertTrue(ken.isHealthy());
}

## 5. Modified testFitsInCage() method in the BoaTest class :
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

## 6. Running all the test cases
![image](https://user-images.githubusercontent.com/99895157/233600793-8d08cf08-2429-4b35-ab07-82d44e1e6482.png)

## 7. modifying the Boa class with the new lengthInInches() method:
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

## Here's an example of a new test case in the BoaTest class that tests the lengthInInches() method:

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
### The testcase we added will check that the lengthInInches() method returns the expected value when called on each of the Boa objects. The assertEquals() method is  called here for comparing the expected values. The Junit indication is done with @Tsst annotation.
