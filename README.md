# Lambda-to-S3 Access Denied – AWS Troubleshooting Lab

This project simulates a real-world AWS issue where a Lambda function fails to copy files between S3 buckets due to improper IAM role permissions. I used logs, role investigation, and manual testing to identify and resolve the issue just like a real cloud support engineer would.


##  What This Covers
	•	Diagnosing AccessDenied errors using CloudWatch Logs
	•	Understanding IAM Role behavior in Lambda
	•	Assigning and validating custom IAM policies
	•	Real troubleshooting flow you’d follow in a support engineer role


##  Steps I Took
	1.	Deployed a working Lambda function to copy files from one S3 bucket to another.
	2.	Set up a broken simulation using the same code, but introduced a misconfigured IAM role.
	3.	Uploaded a test file to the source bucket — but nothing appeared in the destination.
	4.	Opened CloudWatch Logs and saw:
Error: An error occurred (AccessDenied) when calling the GetObject operation
	5.	Reviewed the execution role attached to the function.
	6.	Found it was using the default basic role with no S3 permissions.
	7.	Created a custom IAM role with:
	•	s3:GetObject on source bucket
	•	s3:PutObject on destination bucket
	8.	Attached this custom role to the Lambda function.
	9.	Re-tested the upload — and the file was successfully copied to the destination bucket.


## Why I Did This
This was part of my structured cloud support engineer training where I simulate broken environments on purpose. I used real debugging steps to resolve the issue using AWS tools. It strengthened my ability to work through permission issues under pressure.



📘 What I Learned
	•	CloudWatch Logs are critical for root cause discovery
	•	Lambda roles aren’t retroactively updated — you must assign the correct one
	•	Even working code will fail without proper execution context
	•	IAM misconfiguration is one of the top issues in cloud troubleshooting
	•	I can confidently trace and fix failures without being told what’s wrong

⸻
