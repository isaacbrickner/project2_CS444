
## Building

_[How to build the program. VS Code part is optional.]_

Command line:

* `make` to build. An executable called `reservations` will be produced.

VS Code:

* The default build task runs `make`.

## Files

* `reservations.c`: The main code to launch the brokers

## Data

This program takes three command line arguments of type integer to simulate brokers, seats, and transactions. 
The seats are stored in an array of `seat_taken` ints. All of the data we are working with is of type `int`.

```
int seat_count;
int broker_count;
int *seat_taken;  // Array of seats
int transaction_count;
int seat_taken_count = 0;
```
## Functions

_[This is a tree of functions and their short descriptions]_

* `main()`
  * `seat_broker()`
    * This is used to "reserve" and "free" seats and verify the seat count from a specified broker (thread)
  * `reserve_seat()`
    * this reserves a seat by setting a seat at position "n" to true or false. 
  * `free_seat()`
    * sets a seat at position "n" to false to "free" it from the array.
  * `is_free()`
    * helper function to check if a seat is free
  * `verify_seat_count()`
    * checks the array of seats agains the global count of taken seats
    
    
* ## Notes

* In `verify_seat_count()` I used a local variable to copy the information from our global seat count in order to add a lock within the function. That way one thread at a time can can increment it and ensure that the seat counts are consistent. Without it, when running, the brokers will be unhappy.