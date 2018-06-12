# CulminatingElevator
package com.company;

import java.util.Objects;
import java.util.Scanner;
public class Main {

    public static void main(String[] args) {

  //create object from elevator class
       Elevator myElevator =new  Elevator();


        //create NEW ARRAY from 1 - 4
      //  ID number would be the index of the array

      //  -get position(current floor) of each elevator from the elevator class
      //  -get direction of each elevator from the elevator class

        //INITIALIZE VARIABLES:

        boolean usermode = true;
        boolean direction = false;
        boolean up= true;
        boolean currentfloor = false;
        boolean floorrequest =  false;
        String userInput= null;

        //- DISPLAY user or admin mode
        System.out.print(" Select 'AM' to enter into admin mode");

        // INPUT choice from user
        Scanner scanSystemIn = new Scanner(System.in);
        userInput = scanSystemIn.next();

        //IF choice is admin, set boolean modechoice to false
        if (Objects.equals(userInput, "AM") || Objects.equals(userInput, "Am") || Objects.equals(userInput, "am")) {
            usermode = false;
        }
   //     ENDWHILE

// sets up or down button option
    //    WHILE boolean direction is not up or down
        while (!direction){
            System.out.print("Select 'U' to go up, Select 'D' to go down");

            Scanner scanSystemDirection =new Scanner(System.in);
            userInput= scanSystemDirection.next();

            if (Objects.equals(userInput, "D") || Objects.equals(userInput, "d")) {
                up = false;
                direction = true;
                System.out.print("Direction: Down");
                // SET ELEVATOR DIRECTION TO DOWN
            }

            else if ((Objects.equals(userInput, "U") || Objects.equals(userInput, "u"))) {
                    direction = true;
                    System.out.print("Direction: Up");
                    // SET ELEVATOR DIRECTION TO UP
            }
            else {
                System.out.print("Please Enter a Valid option\n\n");
            }

        }// END WHILE(direction!=true)

     //   -maintenance service indicator:user, or admin

    // -------------------------------------------------------------------------------------------------


        //WHILE usermode !(in admin mode)
        while (!usermode){

            System.out.print("\n Elevator is in Admin Mode");
            //  - SET elevator to in admin mode in the elevator class
            //  IF in service (not at current floor)THEN

            if myElevator
            //  WHILE boolean floornumber is false
            //          - DISPLAY options of floor numbers
            //  -READ user input
            //  -IF user input is valid (between 1 - 20)and not current floor THEN
            //           - SAVE floor number in elevator class
            //   -SET boolean floornumber to true

            //   IF elevator is at current floor number and admin mode THEN
            //           - SET boolean usermode true

            //   ELSE
            //           - DISPLAY error message to user and ask them to input a valid integer

            //   END WHILE

            //   ELSE admin mode and not in service(holding at current floor)

            //    ENDWHILE

        }



//if the unit is given its current floor number it should immediately exit admin mode and return to user service


     /*           -------------------------------------------------------------------------------------- -
// this is the procedure for user mode
                -display "user mode"

        SWITCH direction
        CASE UP
        -Display "up" as direction
        WHILE the current floor hasn 't been set (currentfloor!)
                - Request current floor from user
        -READ user input
        IF user input is valid(between 1 - 20)
                - SAVE as current floor
                - the current floor selection is true
                - Determine the elevator which should be sent by calling on the elevator class for the separate
        indexes.Select an elevator which is going in the same direction (below current floor and going up or
        above current floor and going down)and is on a floor closest to the current floor.

        IF the elevator has reached the current floor
        -set elevator start position to current floor
        WHILE !floorrequest
                - Request desired floor from the user

        IF user input is valid(between 1 - 20) and not equal to the current floor
                - boolean floor request is true
                - display requested floor

        IF other request between current floor and floor request
                - store floor request but send elevator to other request first
                ENDIF
        ELSE
                - send elevator to requested floor

        ENDIF
                ELSE
        -DISPLAY error message to user and ask them to input a valid integer

        ENDWHILE

                ENDIF
        ELSE
                - DISPLAY error message to user and ask them to input a valid integer

        SET boolean direction to true
        BREAK from case up

        CASE DOWN
        -Display "down" as direction
        WHILE the current floor hasn 't been set (currentfloor!)
                - Request current floor from user
        -READ user input
        IF user input is valid(between 1 - 20)
                - SAVE as current floor
                - the current floor selection is true
                - -Determine the elevator which should be sent by calling on the elevator class for the separate
        indexes.Select an elevator which is going in the same direction (below current floor and going up or
        above current floor and going down)and is on a floor closest to the current floor.

        IF the elevator has reached the current floor
        -set elevator start position to current floor
        WHILE !floor request
                - Request desired floor from the user

        IF user input is valid(between 1 - 20) and not equal to the current floor
                - boolean floor request is true
                - display requested floor

        IF other request between current floor and floor request
                - send to other request first

        ELSE
                - send elevator to requested floor

        ENDIF
                ELSE
        -DISPLAY error message to user and ask them to input a valid integer

        ENDWHILE

                ENDIF
        ELSE
                - DISPLAY error message to user and ask them to input a valid integer

        SET boolean direction to true
        BREAK from case down

        DEFAULT // no valid option selected
                - DISPLAY error message
        BREAK from default case END WHILE



 */


    }// end main method
} // end main class


