# <pre>                  IT314 - Software Engineering </pre>

#### Name       : Vrund Rajput
#### Student ID  : 202001075
#### Date       : 21/04/2023

----

## Objective:
    The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.
    
----
1. Creating eclipse project named 'Lab8_202001075' and a package named 'myPackage' inside src folder in it.
2. Creating a class for a Boa with the given code snippet in the lab manual.
```
public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	
	//returns true if this Boa constructor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	//returns true if the length of this Boa constructor is
	//less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
}	
```
![2](https://user-images.githubusercontent.com/121281243/233600333-7d85a464-8155-4c75-8639-8dc74454898f.jpg)

3. Creating JUnit test file named 'BoaTest'.  

![3](https://user-images.githubusercontent.com/121281243/233601057-59fe0417-9f1c-4ba1-afc3-ff62df4fd481.jpg)

4. Initializing ken and jen as private Boa's.
```
import static org.junit.Assert.*;
import org.junit.After;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
	
	private Boa jen, ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}
}
```
![4](https://user-images.githubusercontent.com/121281243/233601165-e82dc09f-5869-4c4e-b207-d17434d9ee49.jpg)

5. Implementing test cases for **isHealthy()** and **fitsInCage()** functions.
```
import static org.junit.Assert.*;
import org.junit.After;
import org.junit.Assert;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
	
	private Boa jen, ken;
	
	@Before
	public void setUp() throws Exception {
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa("Kenneth", 3, "granola bars");
	}
	@After
	public void tearDown() throws Exception {
	}
	@Test
	public void testIsHealthy() {
		// IsHealthy testing for jen
		Assert.assertFalse(jen.isHealthy());
		
		// IsHealthy testing for ken
		Assert.assertTrue(ken.isHealthy());
	}
	
	@Test
	public void testFitsInCage() {
		// FitsInCage testing for jen
		Assert.assertFalse(jen.fitsInCage(1));
		Assert.assertFalse(jen.fitsInCage(2));
		Assert.assertTrue(jen.fitsInCage(3));
		
		// FitsInCage testing for ken
		Assert.assertFalse(ken.fitsInCage(2));
		Assert.assertFalse(ken.fitsInCage(3));
		Assert.assertTrue(ken.fitsInCage(4));
	}
}
```
![5](https://user-images.githubusercontent.com/121281243/233601391-698d51c7-7fda-47c5-961b-8698a053ceb8.jpg)

For testing thee fitsInCage() function, there is no need to write tests for both jen and ken objects as the function is same for both and the output of test cases depends only whether the given lenght is greater than,less than or equal to actual length of object.The behaviour will be similar in both cases.

6. Running the tes cases. All test cases are passed and there is no red bars in the output. Both 2 test cases are passed.

![6](https://user-images.githubusercontent.com/121281243/233601448-6414ace1-28dc-4da7-a7e8-4cd2793dbcf2.jpg)

7. Adding a new method to the Boa class with name lenghtInInches() to get the length in inches.
```
//returns the length of the Boa in inches
public int lenghtInInches() {
  return this.length * 12;
}
```
![7](https://user-images.githubusercontent.com/121281243/233601514-1cdc3d23-f8a7-490d-a5f3-7509f9f51256.jpg)

As the length of the Boa is given in feet, to convert it into inches, We simply multiply length with 12 and return the value.

8. Adding another test case and running all 3 test cases together.
```
@Test
public void testLengthInInches() {
  // Length in inches of Boa-Jen should be 2*12=24
  assertEquals(24, jen.lenghtInInches());
        
  // Length in inches of Boa-Ken should be 3*12=36
  assertEquals(36, ken.lenghtInInches());
}
```
![8](https://user-images.githubusercontent.com/121281243/233601578-b1f55a7d-12c2-4fc0-a8ab-461fd4a85595.jpg)

As a result, test cases have been created for the specified Boa class, and the necessary Junit test cases have been used to test all three methods.
