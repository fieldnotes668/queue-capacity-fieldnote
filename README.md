# When a Queue Stops Catching Up

A standalone, interactive fieldnote about queue backlog and worker capacity. Open `index.html` in a browser; there are no build steps, external libraries, remote scripts, or tracking.

The model advances in one-minute steps:

```text
next backlog = max(0, current backlog + arrivals - worker capacity)
worker capacity = worker count × jobs per worker per minute
```

A burst begins after minute 10 and lasts for the selected duration. The chart displays backlog through minute 60. The drain estimate after the burst assumes arrivals return to the normal rate and service capacity remains constant. If normal arrivals meet or exceed capacity, the model reports that the queue cannot catch up.

This is an educational model, not a production forecast. It omits job-size variation, retries, priority queues, worker failures, provider rate limits, and feedback from downstream systems. A real dashboard should show oldest-job age, arrival and completion rates, retry volume, and queue length together.
