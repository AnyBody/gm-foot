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

1. Make the model load

2. Fix ankle joints and ligaments

3. Add lower leg muscles back

4. Validate results


Usage: 
=============

This implmentation only works with the TLEM 2 leg model. It also requires that
the existing feet and lower leg muscles are disabled with the following setting:
``#define BM_FOOT_MODEL _FOOT_MODEL_NONE_``. 

.. note:: This switch is only available in AMMR 2.0.1 or later.

Secondly, the GM foot model must use its own special scaling law. The code for
enabling the implementation looks like this: 

.. code-block:: AnyScript

    // Setup required for using th GM foot model
    #define BM_LEG_MODEL _LEG_MODEL_TLEM2_
    #define BM_FOOT_MODEL _FOOT_MODEL_NONE_
    #define BM_SCALING _SCALING_USERDEFINED_
    #path BM_SCALING_FILE "ScalingLengthMassFat.any"  
        
    // Inlcude the Human model as always
    #include "<ANYBODY_PATH_BODY>/HumanModel.any"

    // Finally include the GM foot model.
    #include "FootGM.any"


See :file:`test_main.any` for an example of including the GM foot. 
