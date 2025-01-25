# Node.js Server Unresponsiveness Bug

This repository demonstrates a common issue in Node.js servers: unresponsiveness due to long-running tasks in the main event loop. The `server.js` file contains a simple HTTP server that simulates a 5-second delay before responding to requests. This blocks the event loop, preventing other requests from being processed and potentially leading to timeouts or unresponsive behavior.

The `serverSolution.js` file provides a solution to this issue by offloading the long-running task to a worker thread using the `worker_threads` module. This prevents blocking of the main event loop, allowing the server to remain responsive.

## How to Reproduce
1. Clone this repository.
2. Navigate to the project directory.
3. Run `node server.js`. 
4. Make a request to `http://localhost:3000`. Notice the significant delay before getting a response.
5. Run `node serverSolution.js`. 
6. Make another request to `http://localhost:3000`. The response should be almost instant. 

## Solution
The solution uses worker threads to offload the long-running task and demonstrates a common pattern for handling computationally intensive operations in Node.js without blocking the event loop.