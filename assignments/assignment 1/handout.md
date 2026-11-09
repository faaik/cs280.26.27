## The Great Potato Space Program

A team of backyard engineers is trying to launch potatoes into space. So far, their biggest achievement is getting one over the neighbor's fence. Build a Java program that reads their records and produces five reports.

**Total - 100 points**

### 1. Input files

Read all program data from the three supplied CSV files in `input/`. Each file represents one kind of object, and each data row represents one instance.

| File | CSV header | What each row represents |
| --- | --- | --- |
| `potatoes.csv` | `potatoId,name,type` | One potato astronaut. |
| `launchers.csv` | `launcherId,name,maxPayloadKg` | One launcher with a maximum payload in kilograms. |
| `launch_attempts.csv` | `attemptId,potatoId,launcherId,payloadKg,flightRating` | One completed launch attempt involving one potato and one launcher. Both can appear in multiple attempts. |

Each file starts with a header and may contain zero or more data rows in any order. Assume valid data, unique IDs within each file, and existing potato and launcher IDs in every attempt. Field values contain no commas, quotes, or leading or trailing spaces.

The payload includes the potato, its capsule, and any equipment. Payloads and launcher limits are positive whole kilograms. Flight ratings range from 1 (barely left the ramp) to 5 (cleared the fence in style).

### 2. Scoring and payload limits

Every completed launch earns whole-number points. The potato’s type determines the formula.

| Potato type | Score |
| --- | --- |
| `FINGERLING` | `3 × payloadKg + 2 × flightRating` |
| `PURPLE` | `4 × payloadKg + flightRating` |
| `RUSSET` | `2 × payloadKg + flightRating` |
| `YUKON_GOLD` | `2 × payloadKg + 3 × flightRating` |

A launch exceeds the payload limit when `payloadKg` is greater than the launcher’s `maxPayloadKg`. The excess is `payloadKg - maxPayloadKg`. A payload exactly at the limit is allowed. Over-limit launches still count toward scores, totals, and rankings.

### 3. Java and class design requirements

- Model potatoes, launchers, and launch attempts as objects. Each attempt must hold references to its potato and launcher. Use one map from potato ID to potato object and another from launcher ID to launcher object to look up those objects when loading attempts.
- Create a shared potato superclass and one concrete subclass for each of the four types. Declare the scoring operation in a custom interface, implement each formula in its corresponding subclass, and call the scoring operation through the interface.
- Store the attempts in an `ArrayList`. Implement `Comparable` on the launch-attempt class and use its natural ordering for Report 5.
- Keep fields private and separate file reading, domain logic, and report generation into methods or classes with clear responsibilities. Choose your own class and method names apart from the `Main` entry point.
- Read input with `Scanner` and write reports with `FileWriter` or `PrintWriter`. The program must run without keyboard input and write all report data to files.

### 4. The five reports

Create `output/` if needed. Write exactly the five CSV reports below and replace their contents on every run. Write the specified header even when there are no data rows. Use commas with no spaces around separators, write numbers without units, and sort IDs as text.

#### Report 1 - Potato flight log

**File** `01_potato_flight_log.csv`
**Header** `potatoId,name,type,attemptCount,totalPoints`

Write one row per potato, sorted by potato ID ascending. Count its attempts and sum their scores. Include potatoes with no attempts, with zeros for both values.

#### Report 2 - Launcher activity

**File** `02_launcher_activity.csv`
**Header** `launcherId,name,attemptCount,totalPayloadKg,overLimitCount`

Write one row per launcher, sorted by launcher ID ascending. Count its attempts, sum their payloads, and count how many exceeded the limit. Include unused launchers, with zeros for all three values.

#### Report 3 - Launch results by potato and launcher

**File** `03_launch_results_by_pair.csv`
**Header** `potatoId,launcherId,attemptCount,totalPoints`

Write one row for every potato–launcher pair that appears in the launch attempts. For each pair, count its attempts and sum their scores. Include attempts that exceeded the payload limit. Sort by potato ID ascending, then by launcher ID ascending.

#### Report 4 - Payload limit violations

**File** `04_payload_violations.csv`
**Header** `attemptId,potatoId,launcherId,payloadKg,maxPayloadKg,excessKg`

Write one row per over-limit attempt. Sort by excess kilograms descending, then by attempt ID ascending when the excess is the same.

#### Report 5 - The three best test flights

**File** `05_best_test_flights.csv`
**Header** `attemptId,potatoName,launcherName,flightRating,payloadKg,points`

Use `Comparable` to rank attempts by flight rating descending, then payload descending, then attempt ID ascending. Write the first three attempts in that order, or all attempts if fewer than three exist.

### 5. Sample checks

- Sir Spud (`P01`) has 3 attempts and 44 total points.
- The first two data rows in Report 3 are `P01,L01,2,36` and `P01,L02,1,8`, in that order.
- Attempt `A06` appears first in Report 4, with an excess of 2 kg.
- The three best test flights are `A04`, `A12`, and `A03`, in that order.

### 6. Submission

Create a GitHub repository for this assessment, initialize its main branch, and invite `faaik`, as a collaborator before you begin.

Complete the milestones below in order. Open one pull request per milestone, with main as the base branch for all five.
| Pull request | Milestone | What to include |
| --- | --- | --- |
| 1 | Domain model and scoring | Model potatoes, launchers, and launch attempts. Implement and check the four scoring formulas. |
| 2 | CSV input and object lookup | Add the three supplied CSV files. Read them and link each attempt to its potato and launcher. |
| 3 | Potato and launcher reports | Generate Reports 1 and 2, including potatoes and launchers with no attempts. |
| 4 | Potato–launcher report | Generate Report 3 and check that repeated attempts for the same pair appear in a single row. |
| 5 | Final reports and verification | Generate Reports 4 and 5, run the full program, and include the final five output files and README. |

For each milestone, create a fresh branch from main. Open the pull request after your first meaningful commit and push further changes to that branch as you work. In each PR description, briefly explain what you changed, how you checked it, and one design decision you made.

Merge each of the first four PRs after completing and checking that milestone, then branch from the updated main. Leave the fifth PR open for grading and submit its URL.

By the final pull request, the repository must contain:
- Java source files in src/, with src/Main.java as the entry point. Use the default package.
- The three supplied CSV files in input/.
- The five generated CSV reports in output/.
- A README.md with 3–5 sentences explaining how you modeled the relationships, what you used the maps for, and where you put the scoring logic.

### 7. Grading

| Criterion | Points |
| --- | ---: |
| Domain models, encapsulation, and object relationships | 20 |
| Inheritance and scoring through a custom interface | 12 |
| ID lookups and organization of data for report generation (Map / ArrayList) | 7 |
| `ArrayList` and `Comparable` | 6 |
| Separation of responsibilities and design explanation | 5 |
| File input and output, filenames, and CSV headers | 10 |
| Report calculations, included rows, and ordering (8 points per report) | 40 |
| **Total** | **100** |