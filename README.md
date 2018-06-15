package com.company;


/**
 * Created by 13549lac on 24/05/2018.
 */

import static com.company.ProjConstants.*;
import java.util.Objects;

public class Elevator {

// all of the methods that allow you to view its state (what floor its on, direction up or down)


    private boolean up = true;
    private boolean userMode = true;
    int nextFloor = 1;
    private int currentFloor = 1;



    int [] floor = new int [20];

    //create array of objects
    //ID number would be the index of the array


    public void addNewDataItem ( int floorNum){

        if ((floorNum < MINFLOOR) || (floorNum > MAXFLOOR)) {

            System.out.print("Floor is not within 1-20");


        } else{

            // if the floor is valid are satisfied then 1 is added to the frequency,
            // and the sum of the frequencies (sdItems)

            floor[floorNum] += 1;
            System.out.print("\nFREQUENCY " + floorNum + "  " + floor[floorNum]);



        }


    }



    public void setMode (boolean userMode){


    }

    public boolean getMode(){
        return userMode;

    }



    public void setDirection (boolean up){

    }

    public boolean getDirection(){
        return up;
    }


    public void setCurrentFloor (int elevatorFloor) {

        if (getDirection()) {

            // for (currentFloor= (MINFLOOR + 1) ; currentFloor < MAXFLOOR; currentFloor++){


            while (floor[elevatorFloor] == 0) {
                elevatorFloor++;
                if (floor[elevatorFloor]>0){
                    break;
                }
            }



        } else {

            while (floor[elevatorFloor] == 0) {
                elevatorFloor--;
                if (floor[elevatorFloor]>0){
                    break;
                }
            }


        }
        currentFloor = elevatorFloor;
        System.out.print("\nelevat floor " + elevatorFloor);
        System.out.print("\n curr floor " + currentFloor);
    }

    public int getCurrentFloor (){
       return currentFloor;

    }



    public void setNextFloor (int nextFloor){

        if (getDirection()){

        }

    }

    public int getNextFloor (){
        return nextFloor;
    }




}// end Elevator Class
