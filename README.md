# stopwatch
A simple timer for the 6.1 overview notebook

## 1 Overview

These stopwatches were developed specifically for the Chapter 6.1-6.3 Overview Notebook. However, they can be used wherever we want students to use a stopwatch for collecting data. Unless specified as otherwise, these stopwatches will record their data in a centralized Google sheet. The data can be easily downloaded into R for a specific class or user.

### 1.1 Stopwatch behavior parameters

The following parameters, which can be included in the url that configures the stopwatch, determine the behavior of the stopwatch. (We will show examples of urls below.)

<table border="1" style="font-size: 18px; margin-left: 0; border-collapse: collapse; width: 100%;">
  <thead>
    <tr>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 13.33%;">Parameter</th>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 60%;">Description</th>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 13.33%;">Default</th>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 13.33%;">Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">trials</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Maximum number of trials before the button is disabled. If omitted, no limit is enforced.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">(none)</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Any positive integer</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">progress</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Controls whether the live timer is shown or hidden during the trial.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">show</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">show, hide</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">result</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Controls whether the elapsed time is shown at the end of each trial.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">show</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">show, hide</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">save_data</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">If set to false, trial data will not be saved to the Google Sheet.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">true</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">true, false</td>
    </tr>
  </tbody>
</table>

### 1.2 Data submission parameters

The following additional parameters can be set and passed on with the data for each trial.

<table border="1" style="font-size: 18px; margin-left: 0; border-collapse: collapse; width: 100%;">
  <thead>
    <tr>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 13.33%;">Parameter</th>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 60%;">Description</th>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 13.33%;">Default</th>
      <th style="border: 1px solid black; text-align: left; vertical-align: top; width: 13.33%;">Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">class_id</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Identifies the class for grouping or filtering data. Set by the teacher in the notebook and can be any unique ID (e.g., the teacher's email address)</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">anonymous</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Any string</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">user_id</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Identifies the user. Typically set in the notebook to the be user's Jupyter ID.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">anonymous</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Any string</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">session_id</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Unique identifier for each  session. New sessions start on browser refresh or cell being re-run.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">(generated)</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">5-character alphanumeric string</td>
    </tr>
     <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">date</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Timestamp for each trial, recorded in UTC. Useful for sorting, filtering, or session tracking.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">(generated)</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">ISO 8601 UTC timestamp</td>
    </tr>
    <tr>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">condition</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Used to label experimental or instructional groups. Saved in the dataset for analysis.</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">none</td>
      <td style="border: 1px solid black; text-align: left; vertical-align: top;">Any string</td>
    </tr>
  </tbody>
</table>
## 2 Data Saved in Centralized Google Sheet

Data from the stopwatch are save in a centralized Google sheet that holds data for many classes. Example code for importing data from the spreadsheet into R is shown in section 3, below. By filtering data, you can look at only data for your class, for yourself (i.e., a single user), or for everyone. 6 variables are posted to the Google sheet, for each trial, in this order: 

- class_id - a unique ID supplied by the teacher)
- user_id - typically the Jupyter ID generated in the notebook)
- session_id - a unique ID that is generated each time the code is run)
- date 
- condition - can be any text string)
- trial - the attempt number for a session)
- time_sec

### 2.1 Setting the data submission parameters

The values of `class_id`, `condition`, and `user_id` are generally set somewhere in the student-facing notebook before the cell in which the stopwatch appears. They could be set at the top of the notebook (in the setup cell), or revised later in the notebook (e.g., if the teacher wants to include both conditions in a notebook). The other variables are set automatically by the app.

## 3 A fully functioning Jupyter notebook with examples is included in this repository


