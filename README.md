# pattern_dur_var_freq_fixed_dataset_zero
Pattern Duration variable and Frequency Fixed - Dataset with zero, no outlier, no negative numbers

**Vibrotactile Data Representation — Variable Duration, Fixed Frequency (VDRVF)**  
This Arduino-based project implements a set of perceptual tasks using vibrotactile feedback, where vibration duration is mapped from a discrete data array and the vibration frequency is fixed.

## Hardware Requirements
- Arduino Mega 2560
- 8 LRA (Linear Resonant Actuators)
- 8 push buttons
- Wires and breadboard or custom PCB
- Optional: sponge mounts for vibration isolation

## Pin Configuration
- Motors are connected to PWM pins: 12, 11, 10, 9, 8, 7, 6, 5
- Buttons are connected to digital pins: 43, 39, 35, 31, 52, 50, 46, 42

## Data Input
The array `dataValues[8]` defines the data points to be encoded as vibrotactile pulses. Values must be between 0 and 100.  
- Value `0` is treated as "no vibration" (pulse duration = 0 ms).
- Values from `1` to `100` are linearly mapped to pulse durations between `100 ms` and `800 ms`.

```
int dataValues[8] = {0, 30, 50, 70, 90, 100, 20, 40};
```

## Tasks Implemented

### Task 1: Identify the Shortest Vibration
Participants must press the button corresponding to the motor with the shortest vibration duration.

### Task 2: Identify the Longest Vibration
Participants must identify the motor with the longest vibration duration.

### Task 3: Sort by Swapping
Participants can press two buttons to swap motors until they believe the durations are sorted in ascending order. The task ends with a double-click on button 7.

## Experiment Flow
- Each task includes 3 randomized trials.
- Between tasks, a pause is enforced, waiting for any button press to continue.
- After all tasks, the experiment terminates.

## Output
- All trial data (durations, responses, correctness, response time) are printed to the Serial Monitor (baud rate: 9600).

## Notes
- All durations are recomputed at setup from the data array.
- Adjust `TRIALS_PER_GROUP` or `TOTAL_GROUPS` to modify experiment length.

## License
This project is open source and provided under the MIT License.

---

For academic use, please cite appropriately and consider sharing feedback or modifications.

