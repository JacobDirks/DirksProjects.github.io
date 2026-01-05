---
title: MicroController Code
tags:
- tag1
- tag2
---

## **Overview**

After creating the schematic and manufacturing the PCB we now have the opportunity to code. For that we are going to use MPLAB X V5.45. 

```
#include "mcc_generated_files/mcc.h"

void lowerMotor(void);
void raiseMotor(void);

/*
                    lowerMotor process*/
void lowerMotor(void){
    while(limit_f_GetValue() == 0){
        if(move_f_GetValue() != 1){ // if it's already set we don't need to set it again
            move_f_SetHigh(); 
        }
        __delay_ms(10);
    }
    move_f_SetLow();
}

void raiseMotor(void){
    while(limit_r_GetValue() == 0){
        if(move_r_GetValue()!= 1){
            move_r_SetHigh();
        }
        __delay_ms(10);
    }
    move_r_SetLow();
}

void main(void)
{
    // Initialize the device
    SYSTEM_Initialize();

    //initalize adcc
    ADCC_Initialize();
    //initalize dac
    DAC1_Initialize();
    // start all gpio
    PIN_MANAGER_Initialize();
    
    uint16_t conversionResult;
    //led_Toggle();
    //__delay_ms(1000);
    
    bool processDone = true;
    
    if(limit_r_GetValue() == 0){
            raiseMotor();
        }
    
    while (1)
    {
        // Add your application code
        // check if request is high
            //if so do rest
            /*
             send processing signal high
             * Start motor forward.
             * Wait till limit switch forward is hit.
             * Stop motor movement
             * Read ADCC
             * Write DAC
             * Set processing Low
             * wait till request is low
             * set processing high
             * Reverse motor start
             * Wait till limit switch is hit
             * Stop motor
             * Wait till request is high again
             */
        led_SetHigh();
        
        processDone == true; // set it to true so I can simulate it for checkoff
        
        if((request_GetValue() == 1) && (processDone == true)){ // this checks if it is high
           
            if(limit_f_GetValue() == 0){
                led_SetLow();
                process_SetHigh();
                lowerMotor(); // we do technically get stuck here until the motor is down but at least its sampling every couple ms
            }
            ADCC_StartConversion(moistureIn);
            
            while(!ADCC_IsConversionDone()){ // not sure what to do to not wait on this.
            
            }
            
            conversionResult = ADCC_GetConversionResult();
            DAC1_SetOutput((uint8_t)conversionResult);
            
            process_SetLow(); // we can keep setting low
            led_SetHigh();
            processDone = false;
        }
        
        
        if((request_GetValue() == 0) && (processDone == false)){
        led_SetLow();
        process_SetHigh();
        
            if(limit_r_GetValue() == 0){
                raiseMotor();
            }
            process_SetLow();
            led_SetHigh();
            processDone = true;
        }
        
    }
}

```

It can also be found as ["a zip file for individual verification"](supplied/Dirks_SubSystem.zip) and as it stands we have a ["complete system code version."](supplied/Dirks_SubSystem_complete.zip)  
