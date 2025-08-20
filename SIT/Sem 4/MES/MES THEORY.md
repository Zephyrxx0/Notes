# 8051 Counter/Timer

| GATE | C/T* | M0  | M1  |
| ---- | ---- | --- | --- |

## C/T*:
when set : counter operation (input from Tx input pin)
when cleared : timer operation (input from internal clock)

M1,M0:
Used to set modes of the timer

M1 and M0 together create 4 modes:

| M0  | M1  | Mode |
| --- | --- | ---- |
| 0   | 0   | 0    |
| 0   | 1   | 1    |
| 1   | 0   | 2    |
| 1   | 1   | 3    |

- 13
- 16 
- Auto Reload
- split timer

### MODE 1

16 bits timer.

TCON 'Timer Controller register' 
4bits timer 1, 4bits timer 0

TF1 - Max count/time is reached. If timer 1 overflows , flag sets to 1, a lap is completed and timer is reset. In the next lap TF is set to 0 as timer does not overflow

