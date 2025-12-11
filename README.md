#Experiment-6-Series-Queues-with-infinite-capacity--Open-Jackson-Network-
/
# Aim: 
To find

	a)Average number of materials in the system 
  
	b) Average number of materials in the each conveyor 
  
	c) Waiting time of each material in the system
  
	d) Waiting time of each material in each conveyor
  
If the arrival of materials follow Poisson process with the mean interval time 12 seconds, service time of lathe machine in series follow exponential distribution with service time 1 seconds, 1.5 seconds and 1.3 seconds respectively and average service time of robot is 7 seconds. 
# Software required: Visual Components and Python 
# Theory: 
An open Jackson network is a system of k service stations where station i (i = 1,2,3,…,k) has the following characteristics:
(i)  An infinite queue capacity
(ii) Customers arrive at station i from outside of the system according to a Poisson process with parameter rᵢ.
(iii) Cᵢ servers at station i with an exponential service time distribution with parameter μᵢ.
(iv) Customers completing service at station i next go to station j.
(v) Let λⱼ denote the total arrival rate of customers to station Sⱼ. Then the traffic flow equation is:
<img width="861" height="335" alt="image" src="https://github.com/user-attachments/assets/738ebddb-78ac-486a-b7c5-606ee3beb094" />
# Program 
Name:P.Abinaya
Slot Name:3P1-1
Reference Number:25014594
```
arr_time = float(input("Enter the mean inter arrival time of objects from feeder (in secs): "))
ser_time1 = float(input("Enter the mean inter service time of lathe machine 1 (in secs): "))
ser_time2 = float(input("Enter the mean inter service time of lathe machine 2 (in secs): "))
ser_time3 = float(input("Enter the mean inter service time of lathe machine 3 (in secs): "))
Robot_time = float(input("Enter the Additional time taken for the robot (in secs): "))

# Rates
lam = 1 / arr_time
mu1 = 1 / (ser_time1 + Robot_time)
mu2 = 1 / (ser_time2 + Robot_time)
mu3 = 1 / (ser_time3 + Robot_time)

print("---------------------------------------------")
print("Series Queues with Infinite Capacity - Open Jackson Network")
print("---------------------------------------------")

# Stability condition
if (lam < mu1) and (lam < mu2) and (lam < mu3):

    # Ls = average number in system at each station
    Ls1 = lam / (mu1 - lam)
    Ls2 = lam / (mu2 - lam)
    Ls3 = lam / (mu3 - lam)

    # Total objects in all systems
    Ls = Ls1 + Ls2 + Ls3

    # Lq = average number in queue at each station
    Lq1 = Ls1 - (lam / mu1)
    Lq2 = Ls2 - (lam / mu2)
    Lq3 = Ls3 - (lam / mu3)

    # Waiting times
    Wq1 = Lq1 / lam
    Wq2 = Lq2 / lam
    Wq3 = Lq3 / lam

    # Overall waiting time in all 3 stations
    Ws = Ls / lam

    print(f"Average number of objects in system S1: {Ls1:.2f}")
    print(f"Average number of objects in system S2: {Ls2:.2f}")
    print(f"Average number of objects in system S3: {Ls3:.2f}")
    print(f"Total objects in the overall system: {Ls:.2f}")

    print(f"Average number of objects in queue S1: {Lq1:.2f}")
    print(f"Average number of objects in queue S2: {Lq2:.2f}")
    print(f"Average number of objects in queue S3: {Lq3:.2f}")

    print(f"Average waiting time in queue S1: {Wq1:.2f} secs")
    print(f"Average waiting time in queue S2: {Wq2:.2f} secs")
    print(f"Average waiting time in queue S3: {Wq3:.2f} secs")

    print(f"Overall average waiting time in the system: {Ws:.2f} secs")

else:
    print("Warning! Objects overflow will happen in the conveyor")

print("--------------------------------------------------------------")



```
Add Colab Link:https://colab.research.google.com/drive/1OehZmZl_GSLT7y1G4u7P_O-CeZN6hUsl?usp=sharing
# Output
<img width="1019" height="800" alt="Screenshot 2025-12-11 194251" src="https://github.com/user-attachments/assets/032f89b3-e445-48d1-a703-85990a765ce2" />

# Result
  The average number of material in the system and in the conveyor and waiting time are successfully found. 
