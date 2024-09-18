# API Load Testing Report

This repository contains the performance test results for the JSONPlaceholder [Posts API](https://jsonplaceholder.typicode.com/posts). The tests were executed using [Apache JMeter](https://jmeter.apache.org/) to evaluate the API's performance under different load conditions. 

## Overview

The API load testing was performed to measure the server's performance when subjected to different levels of concurrent users, assessing its capacity to handle traffic while maintaining stability and throughput. The tests include various levels of concurrent users and multiple iterations, allowing us to observe the system's behavior under increasing load.

### Test Scenarios:

1. **30 Concurrent Requests** with 5 Loop Count:
   - **Avg TPS (Transactions Per Second):** ~27
   - **Total API Requests:** 180

2. **50 Concurrent Requests** with 5 Loop Count:
   - **Avg TPS:** ~28
   - **Total API Requests:** 300

3. **90 Concurrent Requests** with 5 Loop Count:
   - **Avg TPS:** ~49
   - **Total API Requests:** 540

4. **300 Concurrent Requests** with 10 Loop Count:
   - **Avg TPS:** ~42
   - **Total API Requests:** 3000

5. **900 Concurrent Requests** with 5 Loop Count:
   - **Avg TPS:** ~33
   - **Total API Requests:** 5400

6. **1800 Concurrent Requests** with 5 Loop Count (Stress Test):
   - **Avg TPS:** ~32
   - **Total API Requests:** 9000
   - **Error Rate:** 0.22% (4 requests timed out)

### Summary:
The test results indicate that the server can handle **up to 1600 concurrent API requests** with minimal error rate (0.22%). Beyond this threshold, we observed a minor increase in the error rate (timeout errors). The **throughput**, in terms of Transactions Per Second (TPS), stabilizes around **33 TPS** under high load conditions.

## Test Results

You can find the detailed reports generated from the tests, including graphical data, request-response time distributions, and throughput analysis in the following HTML reports:

- [Report for 100 Requests](API_LoadTesting_100.html/API_LoadTesting_100.html)
- [Report for 300 Requests](API_LoadTesting_300.html/API_LoadTesting_300.html)

Each report contains:
- **Throughput graphs**
- **Response time percentiles**
- **Request error breakdown**
- **Successful vs failed requests**

## Tools Used

- **Testing Tool:** [Apache JMeter](https://jmeter.apache.org/)
- **Test Type:** Performance Load Testing
- **API Endpoint:** `https://jsonplaceholder.typicode.com/posts`
- **Report Format:** HTML

## Test Environment

- **Server IP:** `000.000.000.00`
- **Test Machine:** Local machine
- **Network Conditions:** Default (No artificial throttling)

## Instructions to Run the Test Locally

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/yourusername/API-LoadTesting.git
   ```

2. Open the JMeter `.jmx` test plan:
   - If you don’t have JMeter installed, [download it here](https://jmeter.apache.org/download_jmeter.cgi).
   - Open JMeter and load the test plan files (`API_LoadTesting_100.jmx`, `API_LoadTesting_300.jmx`, etc.) from the `jmeter-tests` folder.

3. Run the JMeter tests in **non-GUI mode** to generate new reports:
   ```bash
   jmeter -n -t jmeter-tests/API_LoadTesting_100.jmx -l results/API_LoadTesting_100.jtl
   jmeter -g results/API_LoadTesting_100.jtl -o report/API_LoadTesting_100.html
   ```

4. Open the generated report in your browser from the `report` folder.

## Key Learnings

1. **API Stability:** The API is stable and can handle high traffic with minimal errors.
2. **Throughput:** There is a consistent throughput of ~33 TPS at high load, with higher numbers for smaller loads.
3. **Error Rate:** Minimal errors were encountered, even at maximum load, indicating good resilience.

## Conclusion

The server performed well under various load conditions, showing an ability to handle large concurrent API requests without significant degradation in response times or an increase in error rates. These results are useful for scaling applications using the JSONPlaceholder API or similar APIs.

---

### Author:
[Refat](https://github.com/REFATBHUYAN)

