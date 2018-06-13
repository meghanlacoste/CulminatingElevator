package com.company;


/**
 * Created by 13549lac on 24/05/2018.
 */

import static com.company.ProjConstants.*;

public class Elevator {

// all of the methods that allow you to view its state (what floor its on, direction up or down)


    private boolean up = true;
    private boolean userMode = true;
    private int currentFloor = 1;
    int nextFloor = 1;



    //create array of objects
    //ID number would be the index of the array

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



    public void setCurrentFloor (int currentFloor) {

    }

    public int getCurrentFloor (){
        return currentFloor;
    }




    public void setNextFloor (int nextFloor){

    }

    public int getNextFloor (){
        return nextFloor;
    }




}// end Elevator Class





