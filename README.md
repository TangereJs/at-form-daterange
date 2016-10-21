at-form-daterange
=================

#### at-form-daterange Flow 5.
###### at-core-form enter use case

This is a use case where `at-form-daterange` is inside `at-core-form`. User is typing into `at-form-daterange` input field and then presses `enter` key.

Its expected that pressing the `enter` key submits the form. Before form is submitted, form is validated, which validates each element on the form.

For `at-form-daterange` this means that `.validate` function will be called before characters that user typed into `at-form-daterange` input field are processed into `at-form-daterange.value`.

So, in `at-form-daterange.validate` this situation must be detected and handled correctly.

User can
* clear existing value
* enter invalid value
* enter correct value

`daterange` must maintain last user input as `_lastUserInput`. When flow 5 happens
* if `_lastUserInput === currentUserInput`) nothing should happen
* if `_lastUserInput !== currentUserInput` then user input should be processed

###### Clear existing value
1. `_lastUserInput = currentUserInput`
2. Display value should become "" (this is already true)
3. `outputValue` should be updated to empty string
4. datepikcers should be updated to empty string
5. start date and end date should be updated to empty string

##### Enter invalid value
1. `_lastUserInput = currentUserInput`
2. Display value should become invalid value (this is already true)
3. `outputValue` should be updated to invalid value
4. datepikcers should be updated to empty string
5. start date and end date should be updated to empty string

##### Enter correct value
1. `_lastUserInput = currentUserInput`
2. Display value should become correct value (this is already true)
3. user input should be parsed into start date and end date momentjs objects
3. `outputValue` should be updated to start-date/end-date string
4. datepikcers should be updated to correct date range
5. start date and end date should be updated to correct values
