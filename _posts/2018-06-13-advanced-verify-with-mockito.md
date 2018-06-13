```
        verify(mock).method(eq("someStringArg"), argThat(complexArg -> {
            
            assertThat(complexArg.getValue1(), is(equalTo("Value 1")));
            assertThat(complexArg.getValue2(), is(equalTo("Value 2")));
            assertThat(complexArg.getValue3(), is(equalTo("Value 3")));
           
            // required for predicate
            return true;
        }));
```
