### LAB 3 

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

The code block above shows the fixed version of methods reverseInPlace and reversed.
