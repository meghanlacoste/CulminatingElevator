package com.company;

import java.util.Objects;
import java.util.Scanner;
import static com.company.ProjConstants.*;
public class Main {

    public static void main(String[] args) {

        //create object from elevator class
        Elevator myElevator = new Elevator();

        // CREATE ARRAY OF BOOLEANS UP AND DOWN FOR ALL REQUESTS (MAX 20 ITEMS)
        boolean[] up = new boolean[20];

        // THEN AS THE ELEVATOR TRAVELS UP THE FLOORS (CHECK EACH FLOOR INBETWEEN
        // THE CURRFLOOR AND REQUEST TO SEE IF THERE ARE UP OR DOWN REQUESTS) CHECK TO SEE IF THE REQUESTS ARE
        // IN THE SAME DIRECTION. GO TO THE FLOOR CLOSEST FIRST SO IF THERE IS A NEXT
        // FLOOR REQUEST AT THAT FLOOR OR FUTURE ONE IN THE SAME DIRECTION STOP.

        int[] floor = new int[20];
        // MAYBE have the current floor be data at floor [0] and then order any requests into the array like adding to
        // the frequency of the value  Data[dataItem] += 1;


        //create NEW ARRAY from 1 - 4
        //  ID number would be the index of the array

        int[] ElevatorID = {1, 2, 3, 4};

        //  -get position(current floor) of each elevator from the elevator class
        //  -get direction of each elevator from the elevator class


        //INITIALIZE VARIABLES:

        boolean userMode = true;
        boolean direction = false;
        up[0] = true;
        boolean currentFloor = false;
        floor[0] = 1;
        int currentFloorNumb = 1;
        boolean floorRequest = false;
        int requestFloorNumb = 1;
        String userInput = null;
        boolean inService = true;
        int service =0;
        boolean serviceSelection = false;


        //- DISPLAY user or admin mode
        System.out.print(" Select 'AM' to enter into admin mode, press any other key to remain in user mode\n");

        // INPUT choice from user
        Scanner scanSystemIn = new Scanner(System.in);
        userInput = scanSystemIn.next();

        //IF choice is admin, set boolean modechoice to false
        if (Objects.equals(userInput, "AM") || Objects.equals(userInput, "Am") || Objects.equals(userInput, "am")) {
            userMode = false;
            System.out.print("Elevator is in Admin Mode\n");
            myElevator.setMode(false);

//            while (serviceSelection= false){
            while (myElevator.getMode() == true){


                System.out.print(" ////////////////////////// ");

                System.out.print("Select 1 for in service and 2 for out of service");
                Scanner scanSystemService = new Scanner(System.in);

                if (scanSystemIn.hasNextInt()){
                    service = scanSystemIn.nextInt();
                    switch (service) {
                        case 1: {
                            inService = true;
                            System.out.print ("Elevator is in service");
                            serviceSelection = true;
                            break;
                        }
                        case 2: {
                            inService = false;
                            System.out.print("Elevator is out of service");
                            serviceSelection = true;
                            break;
                        }
                        default: {
                            System.out.print("Please Enter a valid option");
                        }
                    }// end switch statement
            } // end if (scanSystemIn.hasNextInt())

            } // end while service selection is false

        } else {
            myElevator.setMode(true);
        }
        //     ENDWHILE

// sets up or down button option
        //    WHILE boolean direction is not up or down
       /*
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


        */

        // THIS IS THE INITIAL REQUEST FOR AN ELEVATOR

        while (!currentFloor) {
            //  - Request current floor from user
            System.out.print("\nEnter your current floor\n");
            Scanner scanSystemCfloor = new Scanner(System.in);

            if (scanSystemCfloor.hasNextInt()) {

                currentFloorNumb = scanSystemCfloor.nextInt();

                if (currentFloorNumb <= 20 && currentFloorNumb >= 1) {


                    myElevator.addNewDataItem(currentFloorNumb);
                    // myElevator.setCurrentFloor(currentFloorNumb);

                    System.out.print("\ncurrent floor: " + currentFloorNumb + "\n");
                    currentFloor = true;
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


        if (myElevator.getCurrentFloor() == currentFloorNumb) {


            while (!userMode) {

                while (!inService){

                    System.out.print("\nThe elevator is holding at the current \n");
                }
                //  IF in service (not at current floor)THEN



                //  WHILE no floor has been requested

                while (!floorRequest && inService) {

                    System.out.print("\n Select Desired Floor\n");
                    Scanner scanSystemRfloor = new Scanner(System.in);

                    if (scanSystemRfloor.hasNextInt()) {

                        requestFloorNumb = scanSystemRfloor.nextInt();

                        if (requestFloorNumb <= 20 && requestFloorNumb >= 1) {

                            floor[requestFloorNumb] += 1;


                            //   myElevator.setNextFloor(requestFloorNumb);

                            System.out.print("\nrequested floor: " + requestFloorNumb + "\n");

                            floorRequest = true;

                        } else {
                            System.out.print("\nThat is not a valid floor, try again \n");

                        }

                    } else {

                        System.out.print("\nThat is not a valid integer, try again \n");
                    }


                    //if the unit is given its current floor number it should immediately exit
                    // admin mode and return to user service
                    if (currentFloorNumb == myElevator.getCurrentFloor()){
                        userMode= true;
                        myElevator.setMode(true);
                        break;

                    }


                } //   END WHILE(!floorrequest)

                //   ELSE admin mode and not in service(holding at current floor)


            } // End while(!usermode)


        }// end if  if (myElevator.getCurrentFloor()== currentFloorNumb){




        //        -------------------------------------------------------------------------------------- -
// this is the procedure for user mode


        // if (userMode && (up[currentFloorNumb] = true) ){


        // - Determine the elevator which should be sent by calling on the elevator class for the separate
        // indexes.Select an elevator which is going in the same direction (below current floor and going up or
        //  above current floor and going down)and is on a floor closest to the current floor.

        //  IF the elevator has reached the current floor

        //   if (myElevator.getCurrentFloor() == myElevator.getNextFloor()){
        //   -set elevator start position to current floor
        // }

        while (userMode) {
            while (myElevator.getCurrentFloor() == currentFloorNumb || myElevator.getCurrentFloor() == requestFloorNumb) {
                while (!floorRequest) {

                    System.out.print("\n Select Desired Floor\n");
                    Scanner scanSystemRfloor = new Scanner(System.in);

                    if (scanSystemRfloor.hasNextInt()) {

                        requestFloorNumb = scanSystemRfloor.nextInt();

                        if (requestFloorNumb <= 20 && requestFloorNumb >= 1 && requestFloorNumb != currentFloorNumb) {

                            if (requestFloorNumb > currentFloorNumb) {
                                System.out.print("\n\ndirection: up\n\n");
                                up[currentFloorNumb] = true;
                                myElevator.setDirection(up[currentFloorNumb]);


                                myElevator.addNewDataItem(requestFloorNumb);
                                myElevator.setCurrentFloor(1 + currentFloorNumb);

                                System.out.print("\nTEST current floor " + myElevator.getCurrentFloor());


                                //  myElevator.setNextFloor(requestFloorNumb);

                                System.out.print("\nrequested floor: " + requestFloorNumb + "\n");

                                floorRequest = true;


                            } else {

                                System.out.print("\n\ndirection: down\n\n");
                                up[currentFloorNumb] = false;
                                myElevator.setDirection(up[currentFloorNumb]);
                                myElevator.addNewDataItem(requestFloorNumb);
                                myElevator.setCurrentFloor(currentFloorNumb - 1);

                                //  myElevator.setNextFloor(requestFloorNumb);

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
                } //  end while (!floorrequest)


            }// end while (myElevator.getCurrentFloor() == currentFloorNumb || myElevator.getCurrentFloor()== requestFloorNumb )

        } // end while user mode


    }// end main method

    }// end main classs
