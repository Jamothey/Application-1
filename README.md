ANALYSIS / ENGINEERING:
1. VARYING PRIORITIES
   - When changing the print task priority to a higher priority than the blink task priority, there was not
     a noticable difference in the rate of which the LED was blinking. The question explains that this is
     likely due to the print task being in sleep mode for a majority of the time. Similarly when I increased
     the delay inside of the print task it did not do much to influence the LED. However making the messages
     longer (A LOT LONGER) did effect the LED in a way because it caused the print function to take longer,
     but this string had to be very large and happen repeatedly.
2. INCREASE LOAD
   - After removing the vTaskDelay() function from the print task the LED was not longer blinking consistently.
     it would sometimes be longer, other times it would be shorter, overall it was just irregular. Another note,
     similar to what was discussed in question 1, even on the same priority, character length matter because this
     can effect how long the CPU will stay inside of the print_task function.
3. THEMATIC CUSTOMIZATION
   - I used two different messages in the print task, one that signals a new message being recieved and another
     that signaled the message being processed successfully. These messages are short to not overload the
     communication system and not cause other processes in the same same priority level to miss there deadlines.
     Keeping the messages shorter keeps the system from being affected by the character amount as discussed in
     question 2 (INCREASE LOAD).


REAL-TIME CONCEPT CHECK
- LED blink task period: 0.5s -> 0.25s on, 0.25s off
- Print task period: 10s -> although there are two different messages that are printed the period of messages
  bring printed is 10s.

- Yes, the system maintained the timing requirements set in the assignment, I check this by observing the LED in
  wokwi as well as the console where the print task would print, I then verified it by using timing messages to
  print to the console when each event occurred (these messages were found in the instructions for the assignment).
  I observed these past 20000 ms and it showed a consistent delay and timing of the task that followed the disired
  deadline timing requirements.

- I ran the super-loop baseline code and observed that the LED would have a period of 10 seconds because the loop
  would have to process the printed message and delay before returning to toggling the LED. This is an example of
  causing the LED to miss timing requirements. Another way that I did this was by removing the delay in the printing
  task and making its priority higher, while also adding the print statement that I used for getting the time in the
  blink task function back. This caused the LED to blink extremely slow because the system was overflowed by the
  constant messages, and with it being a higher priority it caused it to interrupt the blink function, slowing it down
  causing it to miss its deadline.

EXTRA CREDIT MATERIAL
- I have the code that logs the timing details of the blink task to the console in the code, I just have it commented out
  because I did not think it was necessary with the period also being printed. I changed the LED in the Simulator from RED
  to GREEN
- I changed the blink task name and variables to something that would be more along the lines off a SPACE SYSTEM using Variables
  like DCIState which stands for DATA COLLECTION INDICATOR STATE.
- I incorporated the calculations for the period into my program and had them only printed once as to not flood the console.
  Although I knew to take time stamps for the significant moments in time (initial_time, current_time), I used CHAT GPT in
  order to obtain the correct syntax (TickType_t, xTaskGetTickCount, xTaskGetTickCount). I then incorporated my own counters
  in order for the program to only print the determined period one time.
