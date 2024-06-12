0. The goal of phase 2b is to perform benchmarking/scalability tests of sample three-tier lakehouse solution.

1. In main.tf, change machine_type at:

```
module "dataproc" {
  depends_on   = [module.vpc]
  source       = "github.com/bdg-tbd/tbd-workshop-1.git?ref=v1.0.36/modules/dataproc"
  project_name = var.project_name
  region       = var.region
  subnet       = module.vpc.subnets[local.notebook_subnet_id].id
  machine_type = "e2-standard-2"
}
```

and subsititute "e2-standard-2" with "e2-standard-4".

2. If needed request to increase cpu quotas (e.g. to 30 CPUs): 
https://console.cloud.google.com/apis/api/compute.googleapis.com/quotas?project=tbd-2023z-9918

3. Using tbd-tpc-di notebook perform dbt run with different number of executors, i.e., 1, 2, and 5, by changing:
```
 "spark.executor.instances": "2"
```

in profiles.yml.

4. In the notebook, collect console output from dbt run, then parse it and retrieve total execution time and execution times of processing each model. Save the results from each number of executors. 
![image](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/b0d2da95-d6f9-4269-b46c-4b0317e1a237)

5. Analyze the performance and scalability of execution times of each model. Visualize and discucss the final results.
![Execution times](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/a3665077-23a1-42e9-a212-2f228fbd4107)

![Total execution time depending on number of executors](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/8166271a-0768-4532-aec0-6334e0651cfd)

The chart illustrates that the most significant performance improvement when increasing the number of executors occurs with the longest tasks. For shorter tasks, there is no noticeable increase in performance. This is likely because, for short tasks, the time spent initializing the task is greater than the time spent on the actual computation, meaning that adding more executors does not accelerate the process
