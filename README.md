package com.company;


public final class ProjConstants {

    // ---------*---------*---------*---------*---------*
    // Integer Constants

    public static final int MINFLOOR = 1;
    public static final int MAXFLOOR = 20;


    // ---------*---------*---------*---------*---------*---------*---------*---------*
    // The caller references the constants using ProjConstants.MAXDATA and other terms.
    // To prevent the caller from constructing objects of this class it is declared a private constructor
    //
    private ProjConstants(){
        //this prevents even the native class from calling this constructor as well
        throw new AssertionError();
    }


}
