
# Lab : Testing First  

## In this lab you'll complete the following objectives:  

Write a failing test
1. Use TDD to test a JSON data contract
2. Use TDD to test JSON deserialization


### Writing a Failing Test

**CashCardJsonTest**
package example.cashcard;

import org.junit.jupiter.api.Test;
import static org.assertj.core.api.Assertions.assertThat;

class CashCardJsonTest {

   @Test
   void myFirstTest() {
     // assertThat(1).isEqualTo(42);  // Failed
      assertThat(42).isEqualTo(42);   // Succeeded
   }
}
