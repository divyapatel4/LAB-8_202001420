# IT314-Lab8

## **Name - Divya Kirtikumar Patel**

## **ID - 202001420**

**1. Create a new Eclipse project, and within the project create a package.**
<img width="1440" alt="Untitled" src="https://user-images.githubusercontent.com/82770981/233616450-741613b9-57b3-4c63-903c-cf84b7c8001a.png">


**2. Create a class for a Boa.**

<img width="1437" alt="Untitled 1" src="https://user-images.githubusercontent.com/82770981/233616477-91bbc9a2-02e1-49c8-81ce-5863f9881045.png">


**3. Test method to test the behaviour of the Boa class** 

```java
import org.junit.Assert;
import org.junit.Test;

public class BoaTest {

  @Test
  public void testIsHealthy() {
    // Test a healthy Boa
    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
    Assert.assertTrue(healthyBoa.isHealthy());

    // Test an unhealthy Boa
    Boa sickBoa = new Boa("Sneaky", 6, "mice");
    Assert.assertFalse(sickBoa.isHealthy());

    // Test a Boa with no favorite food
    Boa noFavoriteFoodBoa = new Boa("No favorite food", 10, "");
    Assert.assertFalse(noFavoriteFoodBoa.isHealthy());
  }

  @Test
  public void testFitsInCage() {
    // Test a small Boa that fits in the cage
    Boa smallBoa = new Boa("Tiny", 2, "rats");
    Assert.assertTrue(smallBoa.fitsInCage(5));
    // Test a small Boa that does not fit in the cage
    Assert.assertFalse(smallBoa.fitsInCage(1));

    // Test a large Boa that fits in the cage
    Boa largeBoa = new Boa("Goliath", 20, "chicken");
    Assert.assertTrue(largeBoa.fitsInCage(25));
    // Test a large Boa that does not fit in the cage
    Assert.assertFalse(largeBoa.fitsInCage(10));

    // Test a Boa that has the exact same length as the cage
    Boa exactLengthBoa = new Boa("Exact Length", 10, "mice");
    Assert.assertTrue(exactLengthBoa.fitsInCage(10));
    // Test a Boa that is slightly longer than the cage
    Assert.assertFalse(exactLengthBoa.fitsInCage(9));
  }
}

```

This test class contains two test methods, `testIsHealthy()` and `testFitsInCage()`, and a total of six test cases.

The `testIsHealthy()` method tests the `isHealthy()` method with three different `Boa` instances:

- `healthyBoa`: a `Boa` that is healthy because its favorite food is "granola bars"
- `sickBoa`: a `Boa` that is not healthy because its favorite food is "mice"
- `noFavoriteFoodBoa`: a `Boa` that has no favorite food and therefore should not be healthy

The `testFitsInCage()` method tests the `fitsInCage(int cageLength)` method with three different `Boa` instances:

- `smallBoa`: a `Boa` that has a length of 2 feet and should fit in a cage that is 5 feet long
- `largeBoa`: a `Boa` that has a length of 20 feet and should fit in a cage that is 25 feet long
- `exactLengthBoa`: a `Boa` that has a length of 10 feet and should be able to fit in a cage that is exactly 10 feet long, but should not fit in a cage that is slightly smaller (9 feet long)

**4. Now it’s time to write some unit tests. Notice that the BoaTest class that JUnit created
for you contains stubs for several methods. Modified setUp() method in the BoaTest class** 

```java
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {

    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa ("Kenneth", 3, "granola bars");
    }  

    @Test
    public void testIsHealthy() {
        Assert.assertFalse(jen.isHealthy());
        Assert.assertFalse(ken.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        Assert.assertTrue(jen.fitsInCage(3));
        Assert.assertFalse(jen.fitsInCage(1));
        Assert.assertTrue(ken.fitsInCage(5));
        Assert.assertFalse(ken.fitsInCage(2));
    }
}
```

In this version, we have created two instances of the **`Boa`** class named **`jen`** and **`ken`** with fixed attributes in the **`setUp`** method using the **`new`** operator. We then perform two tests on these instances in the **`testIsHealthy`** and **`testFitsInCage`** methods using the **`Assert`** class methods **`assertTrue`** and **`assertFalse`** to check if the instances meet certain criteria.

**5. Modified testIsHealthy() method in the BoaTest class :**

```java
@Test
public void testIsHealthy() {
    // check that jen is not healthy
    assertFalse(jen.isHealthy());
    
    // check that ken is healthy
    assertTrue(ken.isHealthy());
    
    // check that a healthy boa with 0 age is not healthy
    Boa zeroAgeBoa = new Boa("Zero", 0, "mice");
    assertFalse(zeroAgeBoa.isHealthy());

    // check that a sick boa with 10 age is not healthy
    Boa sickBoa = new Boa("Sick", 10, "granola bars");
    assertFalse(sickBoa.isHealthy());

    // check that a healthy boa with 1 age is healthy
    Boa youngBoa = new Boa("Young", 1, "chicken");
    assertTrue(youngBoa.isHealthy());

    // check that a healthy boa with 30 age is healthy
    Boa oldBoa = new Boa("Old", 30, "rats");
    assertTrue(oldBoa.isHealthy());
}
```

// The testIsHealthy() method checks that isHealthy() returns the correct boolean value for each Boa object. In this case, we have two Boa objects created in setUp() with different favorite foods. We test that the healthy Boa returns true and the sick Boa returns false. 

**5. Modified testFitsInCage() method in the BoaTest class :**

```java
@Test
public void testFitsInCage() {
    // check that jen fits in a cage with size 3
    assertTrue(jen.fitsInCage(3));
    
    // check that ken fits in a cage with size 5
    assertTrue(ken.fitsInCage(5));
    
    // check that a small boa does not fit in a cage with size 1
    Boa smallBoa = new Boa("Small", 1, "mice");
    assertFalse(smallBoa.fitsInCage(1));

    // check that a large boa fits in a cage with size 20
    Boa largeBoa = new Boa("Large", 15, "rats");
    assertTrue(largeBoa.fitsInCage(20));

    // check that an extra large boa does not fit in a cage with size 25
    Boa extraLargeBoa = new Boa("Extra Large", 25, "chicken");
    assertFalse(extraLargeBoa.fitsInCage(25));

    // check that a small boa fits in a cage with size 2
    assertTrue(smallBoa.fitsInCage(2));
}
```

In this modified version, we have added four more test cases to check the **`fitsInCage()`**
 method of the **`Boa`**  class with various combinations of boa size and cage size. The first two tests check the cage fit of the instances **`jen`**  and **`ken`** , respectively, to make sure that they fit into a cage with a size that accommodates their body. The next two tests check the cage fit of **`smallBoa`**  and **`largeBoa`** , respectively, to make sure that they do or do not fit in a cage with a certain size. Finally, the last two tests check the cage fit of **`extraLargeBoa`**
 and **`smallBoa`** , respectively, to make sure that they do or do not fit in a cage with a certain size.

6. **Running test cases**

<img width="1049" alt="Untitled 2" src="https://user-images.githubusercontent.com/82770981/233616517-d850163d-7398-4c84-9c2e-a5015e2f745a.png">

**. Test Results **
<img width="570" alt="image" src="https://user-images.githubusercontent.com/82770981/233617498-edb72ab1-3875-4e6b-b0c7-6ebf7bac361e.png">


7.  **Adding a new method to the Boa class**

```java
public class Boa {
    private String name;
    private int lengthInFeet; // the length of the boa, in feet
    private String favoriteFood;

    // Constructor for Boa class
    public Boa(String name, int lengthInFeet, String favoriteFood) {
        this.name = name;
        this.lengthInFeet = lengthInFeet;
        this.favoriteFood = favoriteFood;
    }

    // Returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // Returns true if the length of this boa constrictor is less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.lengthInFeet < cageLength;
    }

    // Produces the length of the Boa in inches
    public int lengthInInches() {
        return this.lengthInFeet * 12;
    }
}
```

**Test Cases for LengthInInches Method:**

```java
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
    private Boa jenniferBoa;
    private Boa kennethBoa;

    // Set up test data before running tests
    @Before
    public void setUp() throws Exception {
        jenniferBoa = new Boa("Jennifer", 2, "grapes");
        kennethBoa = new Boa("Kenneth", 3, "granola bars");
    }

    // Test the lengthInInches method of the Boa class
    @Test
    public void testLengthInInches() {
        assertEquals(24, jenniferBoa.lengthInInches());
        assertEquals(36, kennethBoa.lengthInInches());
    }
}
```

**.  Test Results **
<img width="574" alt="image" src="https://user-images.githubusercontent.com/82770981/233617648-c05fe5e8-0468-433a-88af-a504c9a15acf.png">

