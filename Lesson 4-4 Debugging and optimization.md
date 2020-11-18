# Lesson 4-4 Debugging and optimization



### Debugging Spark is harder on Standalone mode

- Previously, we ran Spark codes in the local mode where you can easily fix the code on your laptop because you can view the error in your code on your local machine.
- For Standalone mode, the cluster (group of manager and executor) load data, distribute the tasks among them and the executor executes the code. The result is either a successful output or a log of the errors. The logs are captured in a separate machine than the executor, which makes it important to interpret the syntax of the logs - this can get tricky.
- One other thing that makes the standalone mode difficult to deploy the code is that your **laptop environment will be completely different than AWS EMR** or other cloud systems. As a result, you will always have to test your code rigorously on different environment settings to make sure the code works.