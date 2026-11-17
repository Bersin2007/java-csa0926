# PROGRAMMING IN JAVA (ASSIGNMENT 3 – CO3)
## Exception Handling & Multithreading

**Repository URL:** [https://github.com/192524027/CSA09-192524027-Assignments](https://github.com/192524027/CSA09-192524027-Assignments)  
**Student A (Primary):** Bhuvanesh H (Register Number: `192524027`)  
**Student B (Pair Partner):** Peer Collaborator (`192524027` Pair-Work Distribution)  
**Java Version:** `OpenJDK 21.0.13 LTS` (Temurin-21.0.13+9)  
**Operating System:** Windows 10/11 x64  

---

## 📋 Individual Contribution Record

| Question | Assessed Area | Bloom's Level | Student A – Primary Responsibility | Student B – Primary Responsibility | Joint Responsibility |
|:---:|:---|:---:|:---|:---|:---|
| **Q1** | Exception hierarchy, try, catch and finally | K4 – Analyse | Throwable hierarchy diagram, catch ordering justification, finally guarantees | 5 test input paths, uncaught stack trace analysis, broader before narrower catch test | Failure point identification & Error vs Exception classification |
| **Q2** | User-defined exceptions, propagation & chaining | K4 – Analyse | Exception hierarchy diagram, checked vs unchecked rationale, 3-layer propagation diagram | Failure scenarios, `getCause()` chaining evidence, lost cause demonstration, test table | Layered abstraction rationale (StorageException vs raw IOException) |
| **Q3** | try-with-resources & debugging | K4 – Analyse | Breakpoint step-through analysis, input failure construction, leaked handle counting | Resource lifecycle analysis, TWR closing guarantees (LIFO), suppressed exceptions | Engineering decision on TWR limitations and atomicity |
| **Q4** | Thread creation and life cycle | K4 – Analyse | Thread vs Runnable design, 6-state life-cycle diagram, `run()` vs `start()` proof, `join()` | 10 execution ordering runs, thread priority experiments, daemon thread behavior | Non-deterministic scheduler analysis and correctness principles |
| **Q5** | Race conditions and synchronization | K4 – Analyse | Reliable double-booking reproduction test, run recordings, interleaving analysis | 10k booking benchmark, fine-grained vs method lock comparison, static vs intrinsic locks | 20-screen cinema deployment architecture decision |
| **Q6** | Deadlock & inter-thread communication | K4 – Analyse | Loop + sync `wait()` rationale, `notify()` vs `notifyAll()` hazard, invariant monitoring | Transfer deadlock reproduction, 4 Coffman conditions, global lock-ordering prevention | Progress guarantees and unifying concurrency theory |
| **Q7** | Concurrent fault-tolerant processor | K5 – Evaluate | ExecutorService + Callable/Future design, lock-free collection selection, class diagram | Fault injection implementation, 1/2/4/8 thread benchmarks, correctness verification | Problem interpretation, thread pool sizing defense, Amdahl's Law analysis |

---

## 🗂️ Project Directory Structure

```
c:/Users/bhuvi/Downloads/Java-Assignment/
├── README.md                                    <- Assignment overview, setup guide, and run commands
├── REPORT.md                                    <- Comprehensive academic report with complete K4/K5 evaluations
├── ASSIGNMENT3.pdf                              <- Official assignment specification
├── render_screenshot.py                         <- Monospace terminal output screenshot renderer
└── Assignment3/
    ├── Task01/                                  <- Q1: ATM Withdrawal Simulation
    │   ├── ATMWithdrawalSimulation.java
    │   ├── BroaderCatchCompilationDemo.java
    │   ├── UncaughtDemo.java
    │   ├── card_reader.dat
    │   ├── output.txt
    │   ├── screenshot_output.png
    │   └── uncaught_trace.txt
    ├── Task02/                                  <- Q2: Online Examination Portal
    │   ├── OnlineExamPortal.java
    │   ├── StorageDemo.java
    │   ├── output.txt
    │   └── screenshot_output.png
    ├── Task03/                                  <- Q3: Daily Sales Report Generator
    │   ├── DailySalesReportManual.java
    │   ├── DailySalesReportTWR.java
    │   ├── DailySalesComparisonDemo.java
    │   ├── stores/ (store1.csv, store2.csv, store3_corrupt.csv, store4.csv)
    │   ├── report_manual.csv / report_twr.csv
    │   ├── output.txt
    │   └── screenshot_output.png
    ├── Task04/                                  <- Q4: Parallel Answer-Script Scanning
    │   ├── AnswerScriptScannerThread.java
    │   ├── AnswerScriptScannerRunnable.java
    │   ├── ScannerExperimentsDemo.java
    │   ├── output.txt
    │   └── screenshot_output.png
    ├── Task05/                                  <- Q5: Cinema Seat-Booking Race Conditions
    │   ├── SeatBooking.java
    │   ├── SeatBookingRaceExperiment.java
    │   ├── output.txt
    │   └── screenshot_output.png
    ├── Task06/                                  <- Q6: Deadlock & Inter-Thread Communication
    │   ├── TokenCounter.java
    │   ├── HostelWalletTransfer.java
    │   ├── output.txt
    │   └── screenshot_output.png
    └── Task07/                                  <- Q7: Concurrent Fault-Tolerant Processor
        ├── SemesterResultProcessor.java
        ├── verify_dataset/ (10 hand-checked test files)
        ├── output.txt
        └── screenshot_output.png
```

---

## 🚀 Compilation and Execution Instructions

All commands can be executed from the root directory or inside `Assignment3/`.

### Task 01: Bank ATM Simulation (Q1)
```bash
cd Assignment3
javac Task01/*.java
java Task01.ATMWithdrawalSimulation
java Task01.UncaughtDemo
```
* **Result Note:** Verified 5 distinct execution paths (valid withdrawal, non-numeric input, negative amount, insufficient funds, missing card reader file). Demonstrated guaranteed cleanup in `finally` and proved unreachable catch compilation error under broader-before-narrower ordering.

---

### Task 02: Online Examination Portal (Q2)
```bash
cd Assignment3
javac Task02/*.java
java Task02.StorageDemo
java Task02.OnlineExamPortal
```
* **Result Note:** Completed `StorageDemo` TODO 1 matching expected output (`Saved answer01.pdf`, `Error: Could not store answer02.pdf`, `Cause: Disk quota exceeded`). Demonstrated 3-layer checked exception propagation and diagnostic cause preservation via `getCause()`.

---

### Task 03: Daily Sales Report Generator (Q3)
```bash
cd Assignment3
javac Task03/*.java
java Task03.DailySalesComparisonDemo
```
* **Result Note:** Proved that both manual and TWR implementations generate identical reports on valid inputs. Under injected corruption (`store3_corrupt.csv`), manual cleanup leaks 1 open file handle while TWR guarantees 0 open handles via synthetic compiler `finally` blocks and supports suppressed exceptions.

---

### Task 04: Parallel Answer-Script Scanning (Q4)
```bash
cd Assignment3
javac Task04/*.java
java Task04.ScannerExperimentsDemo
```
* **Result Note:** Demonstrated scanning via both `Thread` and `Runnable` implementations. Provided empirical proof that direct `.run()` executes synchronously on the `main` thread. Recorded 10 non-deterministic completion orders and demonstrated daemon thread termination behavior.

---

### Task 05: Cinema Seat Booking Race Conditions (Q5)
```bash
cd Assignment3
javac Task05/*.java
java Task05.SeatBooking
java Task05.SeatBookingRaceExperiment
```
* **Result Note:** Completed `SeatBooking` TODO 1 matching expected output (`Seats sold: 10`). Demonstrated race conditions in unsynchronized code selling up to 33 seats (98 overbookings across 10 runs). Synchronized method and fine-grained synchronized blocks maintained strict 10-seat caps with benchmark performance across 10,000 requests.

---

### Task 06: Deadlock & Hostel Mess Token Counter (Q6)
```bash
cd Assignment3
javac Task06/*.java
java Task06.TokenCounter
java Task06.HostelWalletTransfer
```
* **Result Note:** Completed `TokenCounter` TODO 1 and 2 matching expected output (`Sum of tokens collected: 210 (expected 210)`). Successfully reproduced transfer deadlock and resolved it using strict account ID lock ordering. Proved buffer size invariant ($0 \le \text{count} \le 5$) and explained the critical failure of `if` versus `while` in `wait()`.

---

### Task 07: Concurrent Fault-Tolerant Processor (Q7)
```bash
cd Assignment3
javac Task07/*.java
java Task07.SemesterResultProcessor
```
* **Result Note:** Validated 100% accuracy on a 10-file hand-checked control set (7 valid, 2 corrupt, 1 missing). Scaled across 10,000 files measuring execution time across 1, 2, 4, and 8 threads with a 5.15x speedup (2141 ms down to 416 ms) and zero unhandled errors.

---

## 📊 Summary of Completed Code Exercises

1. **Q2 `StorageDemo.java` (Page 4):**
   ```java
   } catch (IOException e) {
       throw new SubmissionStorageException("Could not store " + fileName, e);
   }
   ```
2. **Q5 `SeatBooking.java` (Page 7):**
   ```java
   public synchronized boolean book(int seat) {
       if (!booked[seat]) {
           booked[seat] = true;
           bookingsMade++;
           return true;
       }
       return false;
   }
   ```
3. **Q6 `TokenCounter.java` (Page 9):**
   ```java
   public synchronized void put(int token) throws InterruptedException {
       while (count == buffer.length) {
           wait();
       }
       buffer[in] = token;
       in = (in + 1) % buffer.length;
       count++;
       notifyAll();
   }

   public synchronized int take() throws InterruptedException {
       while (count == 0) {
           wait();
       }
       int token = buffer[out];
       out = (out + 1) % buffer.length;
       count--;
       notifyAll();
       return token;
   }
   ```
