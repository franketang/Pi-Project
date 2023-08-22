# Pi-Project
Pi Calculation using PySpark on Google Cloud Platform

This repository demonstrates how to estimate the value of pi using distributed computing through PySpark, hosted on the Google Cloud Platform (GCP).

Presentation
[Project Pi Slides](https://docs.google.com/presentation/d/1pw_erd39RDkqkPLh4RyZR9yZTZDuUkNF/edit#slide=id.p1)

Overview
We'll be utilizing the Monte Carlo method for pi estimation, where random points are plotted within a square, and we ascertain how many fall within an inscribed circle.

#Design:
Randomly choose a point (x, y) inside a square.
Verify if the point lies inside or outside the circle. Assign a value of 1 for inside, 0 for outside.
Count the points inside the circle (S) versus the total points (N) in the square.
Compute pi using the equation: pi = 4 * (S/N).
Setting Up and Execution

#Prerequisites:
Google Cloud DataProc: Ensure you've access to DataProc on GCP.
PySpark Job Creation:
Activate the Cloud Shell from the top-right corner of the console.
Open the editor using the top-right button in the Cloud Shell.
Create a new Python file for your Spark job. Insert your code.
Save the file (e.g., as pi.py) and exit.
Running the PySpark Job on GCP:
Initiate Cloud Shell:

#Activate the Cloud Shell.
If faced with an authentication issue, use: gcloud auth login and follow the browser instructions.
Submit PySpark Job:

bash
Copy code
gcloud dataproc jobs submit pyspark pi.py --cluster=<cluster-name> --region=<region> -- --partitions <partition-count> --output_uri <output-path>
Inspect Output Files:

bash
Copy code
gsutil ls gs://<bucket-name>/output/
Download Results:

bash
Copy code
gsutil cp gs://<bucket-name>/output/* .
Merge Results:

bash
Copy code
cat part-00003 >> part-00000
Display the Outcome:

bash
Copy code
cat part-00003
Expected Outcome:
The result will be the estimated value of pi.

The above README provides a concise guide on estimating pi using PySpark on GCP. It offers clear steps and has been organized for easy readability. Adjustments can be made based on any added features or changes in the process.






Regenerate
