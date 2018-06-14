package com.company;

import java.util.Objects;
import java.util.Scanner;
import static com.company.ProjConstants.*;
public class Main {

    public static void main(String[] args) {

        //create object from elevator class
        Elevator myElevator = new  Elevator();

        // CREATE ARRAY OF BOOLEANS UP AND DOWN FOR ALL REQUESTS (MAX 20 ITEMS)
        boolean [] up  = new boolean [19];

        // THEN AS THE ELEVATOR TRAVELS UP THE FLOORS (CHECK EACH FLOOR INBETWEEN
        // THE CURRFLOOR AND REQUEST TO SEE IF THERE ARE UP OR DOWN REQUESTS) CHECK TO SEE IF THE REQUESTS ARE
        // IN THE SAME DIRECTION. GO TO THE FLOOR CLOSEST FIRST SO IF THERE IS A NEXT
        // FLOOR REQUEST AT THAT FLOOR OR FUTURE ONE IN THE SAME DIRECTION STOP.

        int [] floor = new int [19];
        // MAYBE have the current floor be data at floor [0] and then order any requests into the array like adding to the frequency of the value  Data[dataItem] += 1;


        //create NEW ARRAY from 1 - 4
        //  ID number would be the index of the array

      int [] ElevatorID = {1,2,3,4};

        //  -get position(current floor) of each elevator from the elevator class
        //  -get direction of each elevator from the elevator class



        //INITIALIZE VARIABLES:

        boolean userMode = true;
        boolean direction = false;
        up [0] = true;
        boolean currentFloor = false;
        floor [0]= 1;
        int currentFloorNumb = 1;
        boolean floorRequest =  false;
        int requestFloorNumb = 1;
        String userInput= null;


        //- DISPLAY user or admin mode
        System.out.print(" Select 'AM' to enter into admin mode, press any other key to remain in user mode\n");

        // INPUT choice from user
        Scanner scanSystemIn = new Scanner(System.in);
        userInput = scanSystemIn.next();

        //IF choice is admin, set boolean modechoice to false
        if (Objects.equals(userInput, "AM") || Objects.equals(userInput, "Am") || Objects.equals(userInput, "am")) {
            userMode = false;
            System.out.print("Elevator is in Admin Mode\n");
            myElevator.setMode(userMode);


        } else {
            myElevator.setMode(userMode);
        }
        //     ENDWHILE

// sets up or down button option
        //    WHILE boolean direction is not up or down
        while (!direction){
            System.out.print("\nSelect 'U' to go up, Select 'D' to go down\n");

            Scanner scanSystemDirection =new Scanner(System.in);
            userInput= scanSystemDirection.next();

            if (Objects.equals(userInput, "D") || Objects.equals(userInput, "d")) {
                // ************ WHAT SHOULD THE BE INSIDE  THE []
                up [currentFloorNumb] = false;
                direction = true;
                System.out.print("Direction: Down\n");
                // SET ELEVATOR DIRECTION TO DOWN
                myElevator.setDirection(false);
            }

            else if ((Objects.equals(userInput, "U") || Objects.equals(userInput, "u"))) {
                direction = true;
                System.out.print("Direction: Up\n");
                // SET ELEVATOR DIRECTION TO UP
                myElevator.setDirection(true);
            }
            else {
                System.out.print("Please Enter a Valid option\n\n");
            }

        }// END WHILE(direction!=true)


        while (!currentFloor){
            //  - Request current floor from user
            System.out.print("\nEnter your current floor\n");
            Scanner scanSystemCfloor =new Scanner(System.in);

            if (scanSystemCfloor.hasNextInt()){

                currentFloorNumb = scanSystemCfloor.nextInt();

                if (currentFloorNumb <=20 && currentFloorNumb >=1){

                 //**** SHOULD I SEPARATE CURRENT FLOOR AND REQUEST FLOOR ARRAYS & HOW DO I IMPLEMENT THIS IN THE ELEVATOR CLASS
                    floor[currentFloorNumb]+=1;
                 // myElevator.setCurrentFloor(currentFloorNumb);

                  System.out.print("\ncurrent floor: " + currentFloorNumb +"\n");
                    currentFloor=true;
                } else {
                    System.out.print("\nThat is not a valid floor, try again \n");

                }

            } else {

                System.out.print("\nThat is not a valid integer, try again \n");
            }



        }



        //   -maintenance service indicator:user, or admin

        // -------------------------------------------------------------------------------------------------


        //WHILE userMode !(in admin mode)

        while (!userMode){

            //  IF in service (not at current floor)THEN

            //  WHILE no floor has been requested

            while (!floorRequest) {

                System.out.print("\n Select Desired Floor\n");
                Scanner scanSystemRfloor = new Scanner(System.in);

                if (scanSystemRfloor.hasNextInt()) {

                    requestFloorNumb = scanSystemRfloor.nextInt();

                    if (requestFloorNumb <= 20 && requestFloorNumb >= 1) {
                            
                        floor[requestFloorNumb] +=1;
                     
                        //   myElevator.setNextFloor(requestFloorNumb);

                        System.out.print("\nrequested floor: " + requestFloorNumb +"\n");

                        floorRequest = true;

                    } else {
                        System.out.print("\nThat is not a valid floor, try again \n");

                    }

                } else {

                    System.out.print("\nThat is not a valid integer, try again \n");
                }


                //   IF elevator is at current floor number and admin mode THEN
                //           - SET boolean userMode true


            } //   END WHILE(!floorrequest)

            //   ELSE admin mode and not in service(holding at current floor)



        } // End while(!usermode)




//if the unit is given its current floor number it should immediately exit admin mode and return to user service


      //        -------------------------------------------------------------------------------------- -
// this is the procedure for user mode


              if (userMode && (up[currentFloorNumb] = true) ){


             // - Determine the elevator which should be sent by calling on the elevator class for the separate
       // indexes.Select an elevator which is going in the same direction (below current floor and going up or
      //  above current floor and going down)and is on a floor closest to the current floor.

      //  IF the elevator has reached the current floor
        if (myElevator.getCurrentFloor() == myElevator.getNextFloor()){
            //   -set elevator start position to current floor
        }




        while (!floorRequest) {

            System.out.print("\n Select Desired Floor\n");
            Scanner scanSystemRfloor = new Scanner(System.in);

            if (scanSystemRfloor.hasNextInt()) {

                requestFloorNumb = scanSystemRfloor.nextInt();

                if (requestFloorNumb <= 20 && requestFloorNumb >= 1 && requestFloorNumb!= currentFloorNumb) {

                if (requestFloorNumb > currentFloorNumb){
                    System.out.print("\n\nswitching direction to up\n\n");
                    up [currentFloorNumb]= true;
                    break;

                } else {

                    myElevator.setNextFloor(requestFloorNumb);

                    System.out.print("\nrequested floor: " + requestFloorNumb + "\n");

                    floorRequest = true;

                    //IF other request between current floor and floor request
                    //         - store floor request but send elevator to other request first
                    //        ENDIF
                    // ELSE
                    //          - send elevator to requested floor

                }

                } else {
                    System.out.print("\nThat is not a valid floor, try again \n");

                }

            } else {

                System.out.print("\nThat is not a valid integer, try again \n");
            }
        } //  ENDWHILE

        } // end if user mode and up

        // IF IN USER MODE AND REQUEST DOWNWARDS
        if (userMode && (up [currentFloorNumb]= false)){

            // - Determine the elevator which should be sent by calling on the elevator class for the separate
            // indexes.Select an elevator which is going in the same direction (below current floor and going up or
            //  above current floor and going down)and is on a floor closest to the current floor.

            //  IF the elevator has reached the current floor
            if (myElevator.getCurrentFloor() == myElevator.getNextFloor()){
                //   -set elevator start position to current floor
            }


            while (!floorRequest) {

                System.out.print("\n Select Desired Floor\n");
                Scanner scanSystemRfloor = new Scanner(System.in);

                if (scanSystemRfloor.hasNextInt()) {

                    requestFloorNumb = scanSystemRfloor.nextInt();

                    if (requestFloorNumb <= 20 && requestFloorNumb >= 1 && requestFloorNumb!= currentFloorNumb) {

                        if (requestFloorNumb > currentFloorNumb){
                           System.out.print("\n\nswitching direction to up\n\n");
                            up [currentFloorNumb] = true;
                            break;

                        } else {


                            myElevator.setNextFloor(requestFloorNumb);

                            System.out.print("\nrequested floor: " + requestFloorNumb + "\n");

                            floorRequest = true;

                            //IF other request between current floor and floor request
                            //         - store floor request but send elevator to other request first
                            //        ENDIF
                            // ELSE
                            //          - send elevator to requested floor
                        }

                    } else {
                        System.out.print("\nThat is not a valid floor, try again \n");

                    }

                } else {

                    System.out.print("\nThat is not a valid integer, try again \n");
                }
            } //  ENDWHILE




        }// end if user mode and down




    }// end main method
} // end main class
