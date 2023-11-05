### LAB 3 
# Part 1

![Image](Lab3Failure.png) 

The image above shows a failure-inducing input for the buggy program of ArrayExamples through testing in ArrayTests. The JUNIT test displays the failure of this input.

~~~
@Test
  public void testReverseInPlace2(){
    int[] input1 = { 3 , 6 , 9};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 9 , 6 , 3 }, input1);
  }

  @Test
  public void testReversed2() {
    int[] input1 = { 5, 6 , 7};
    assertArrayEquals(new int[]{ 7, 6 , 5}, ArrayExamples.reversed(input1));
  }
~~~

The code block above shows the test that fails to the buggy program.

![Image](Lab3Pass.png) 

The image above shows an input that doesn't induce failure to the buggy program. The JUNIT test shows that these tests pass the methods.

~~~
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
~~~
The code block above shows the test that passed to the buggy program. 

~~~
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }

  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  
~~~

The code block above shows the buggy method of reverseInPlace and reversed that is used for testing the inputs.

~~~
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
       int temp = arr[i];
       arr[i] = arr[arr.length - i - 1];
       arr[arr.length - i - 1] = temp;
      
    }

static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
~~~

The code block above shows the fixed version of methods reverseInPlace and reversed.

The bug in reverseInPlace method was that it reverses the array but all the elements are the last element and the array does not have the correct elements. To fix this, I created a temporary array that stores the original element before overwriting it by reversing it. In addition, the iteration is changed to half the array length as the middle elements usually stay the same, and only the first few elements and last few elements are switched. The bug in the reversed method is that instead of copying the original array to the new array, it is copying the new array to the original array. To fix this, I changed the order of the code to ensure that the original array is copied to the new array.

# Part 2
