Glasgow-Maastricht Foot Model
#############################

This is an work in progress to reimplment the Glasgow-Maastricht (GM) Foot Model with the
TLEM 2.1 lower extremity model int he AnyBody Mannaged Model Repository (AMMR)
version  2.0.1. 

The old implmentaiton of the GM foot model required its own modified
implementation of the TLEM1 lower extremity model. This was a nightmare to
maintain and made it impossible to use the model with new TLEM 2.1 model.

The goal is to restructure the GM foot model to integreate nicely into the 
TLEM 2.1 model without duplicating the entire lower extremity model unnecessarily. 

TODO: 
=====

#. Validate and test new Ankle joint location.

#. Align scaling between foot and Leg (TLEM2).

#. Fix Free posture example application.

#. Add GM foot example based on AnyMoCap.

#. Test and Validate results.


Usage: 
=============

This implmentation only works with the TLEM 2 leg model and it requires that
the existing feet and lower leg muscles are disabled with the following setting:
``#define BM_FOOT_MODEL _FOOT_MODEL_NONE_``. 

.. note:: This switch is only available in AMMR 2.0.1 or later.

To use the GM foot model the file ``GM_Foot_libdef.any`` must be included before 
the first ``Main`` statement. 

.. code-block:: AnyScript

    // Include before the first Main
    #include "path/to/GM_Foot/GM_Foot_libdef.any"

    Main = {

        // Required for using th GM foot model
        #define BM_LEG_MODEL _LEG_MODEL_TLEM2_
        #define BM_FOOT_MODEL _FOOT_MODEL_NONE_
        
        // Include the HumNModel
        #include "<ANYBODY_PATH_BODY>/HumanModel.any"

        // Include the GM foot model after the HumanModel.any
        #include "<GM_FOOT_PATH>/GM_foot_model.any"


See :file:`test_main.any` for an example of including the GM foot. 
