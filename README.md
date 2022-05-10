# ESE-516-Quarantine-Health-Monitoring-System
The goal of this project is to use the concepts of IoT to remotely monitor the vitals of a patient afflicted with mild/moderate symptoms of COVID-19 and to restrict further spread of infection by controlling the ambient temperature and humidity of the room. Further, an SOS signal was added to aid the patient and call his/her guardian/caretaker.


## Inspiration
It was found that patients with mild to moderate COVID-19 symptoms like mild pneumonia, diarrhea, headache and musculoskeletal symptoms caused a strain on medical resources and contributed to even more COVID-19 cases by availing healthcare institutions and hospitals for their services. This could have been avoided if the patients were instructed to isolate themselves and employ self-care routines to nurse themselves back to health.


Paulo Mecenas, Renata Travassos da Rosa Moreira Bastos, Antonio Carlos Rosário Vallinoto and David Normando (2020) found that the rate of infection for this type of disease rose with dry air and cold temperatures [source](https://pubmed.ncbi.nlm.nih.gov/32946453/). 


## What it does
Using the conclusion and the study above, we built a proprietary product to help perform self-care routines and reduce infection rates by recording the ambient temperature, relative humidity and the patient's vitals like the pulse. As this data is recorded on the cloud, the ambient temperature and humidity can be tuned to reduce COVID-19 air transmission and the vital signs of the isolated patient can be studied to deduce if the patient's health is improving or deteriorating. Further, a touch-based SOS-alert feature was also added for the comfort of the isolated patient. 


## How we built it
The plan of attack we employed was to use the ATSAMW25-XPRO microcontroller to acquire readings of three sensors- a temperature and humidity (SHTC3) sensor, pulse/heartbeat (SEN-11574) sensor and touch (TTP223B) sensor to perform the critical tasks of collecting the ambient temperature and humidity values, vitals recordings and the SOS alert system, and deploy these values to the cloud using MQTT protocol.

Additionally, a buzzer buzzes whenever the touch sensor is activated and a LED to indicate whether the product is switched ON or switched OFF.

In order to integrate and deploy all these elements of our product together on a single board, we designed a PCB board to incorporate different circuitry of our project including power management, SD card memory, USB connector, FTDI and the sensor circuitry. 


## Challenges we ran into

We had some trouble designing our buck circuit with the MP3213 chip. There were two variants, a 8 pin and a 12 pin IC. The 12 pin variant was easily available on SnapEDA but the 8 pin was not so we had to create our own footprint for this component. 

The second issue we ran into was component acquisition. Due to the public health crisis, there have been cases where our chosen components which in thousands on one day went out of stock overnight. This forced us to look for alternate and roughly similar values that matched our design specification. One such example is our Groove Touch sensor, which we had to replace with TTP223B Capacitive Touch Sensor. Even at the time of scripting this post, our PCB board production hasn't arrived due to the lockdown protocols.

The component placement on the PCB was also very tricky. We encountered several DRC errors before finally correctly designing our PCB. As we had several circuits to fit onto our board, we had to choose a large in size for our application, which was not what we intended for our application.


## Accomplishments that we're proud of

### Hardware Features:
Our PCB board was designed such that it could be deployed on a shelf or a table and still work. The quarantined patient exhibiting mild COVID-19 symptoms may not always be bed-ridden so we had to make sure, that the design did not tether the patient to a spot. We achieved this by making the pulse sensor and touch sensors stand alone sensors. As the ambient temperature and humidity sensor is not required on the patient's body, it was integrated in the PCB. Apart from the design, we are also proud of accuracy of the sensors that we see updating to the cloud regularly. We employed some of the best practices while PCB designing by keeping the traces as short as possible, performing effective bypassing by keeping the capacitor as close as possible to the IC pin, using vias to trace through different layers of the PCB and having a ground plane and power plane to improve electrical performance.

### Software Features:
Our PCB board was designed such that it could be deployed on a shelf or a table and still work. The quarantined patient exhibiting mild COVID-19 symptoms may not always be bed-ridden so we had to make sure, that the design did not tether the patient to a spot. We achieved this by making the pulse sensor and touch sensors stand alone sensors. As the ambient temperature and humidity sensor is not required on the patient's body, it was integrated in the PCB. Apart from the design, we are also proud of accuracy of the sensors that we see updating to the cloud regularly. We employed some of the best practices while PCB designing by keeping the traces as short as possible, performing effective bypassing by keeping the capacitor as close as possible to the IC pin, using vias to trace through different layers of the PCB and having a ground plane and power plane to improve electrical performance.




## What we learned

This was definitely a new experience for us! 

Although we knew a bit of PCB designing from our undergrad years, it was truly rewarding in terms the amount of new and interesting content we covered this semester with regards to PCB designing. We also learnt how to make efficient designs and best practices used by professionals in this field which we are very grateful for.

FreeRTOS was new to us and we benefitted from this project as we got hands-on training implementing concepts like multitasking, scheduling, context switching, and real-time scheduling. As we had three sensors with three different mode of operations- I2C, Digital and ADC, we had to cover all aspects and concepts in order to implement the project correctly.

In order to work with the ATSAM25-XPRO microcontroller on Atmel studio, we gained valuable experience in developing board support packages and porting libraries to our custom board. We even learnt the bootloader implementation on an embedded device and how the flow chart has to be designed so as to prevent the device from getting bricked.

Finally, to implement the IoT part of our project, we even hosted a website through Node-red and learned to use MQTT for embedded platforms to visualize our data on a dashboard.
 
## What's next for Quarantine Health Monitoring System

Currently, our project is in its initial stage. The project can be improved upon by sending a mail or text containing the patient's vitals to the caretaker/medical professional to save the doctor's time of logging into a dashboard.


This means that the medical professionals can monitor the data on the move. Also, the SOS system can be programmed to locate and broadcast all the closest hospitals and ambulances for help. This will save precious time and save the family the trouble of booking an ambulance. Also, relays could be used to automatically increase or decrease the HVAC to maintain optimum temperature to reduce infection spread. 

Other effective strategies such as AI chatbots can be used to eliminate the need of a caretaker/nurse and essentially automate the caretaking.
