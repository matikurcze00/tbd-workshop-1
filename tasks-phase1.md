IMPORTANT ❗ ❗ ❗ Please remember to destroy all the resources after each work session. You can recreate infrastructure by creating new PR and merging it to master.
  
![img.png](doc/figures/destroy.png)

1. Authors:

   303763

   https://github.com/matikurcze00/tbd-workshop-1

2. Follow all steps in README.md.

3. Select your project and set budget alerts on 5%, 25%, 50%, 80% of 50$ (in cloud console -> billing -> budget & alerts -> create buget; unclick discounts and promotions&others while creating budget).
 ![image](https://github.com/matikurcze00/tbd-workshop-1/assets/80173470/9927615e-659c-4b0b-8ac5-1f7502193401)

  ![img.png](doc/figures/discounts.png)

5. From avaialble Github Actions select and run destroy on main branch.
   
7. Create new git branch and:
    1. Modify tasks-phase1.md file.
    
    2. Create PR from this branch to **YOUR** master and merge it to make new release. 
    
    ***place the screenshot from GA after succesfull application of release***


8. Analyze terraform code. Play with terraform plan, terraform graph to investigate different modules.
Moduł dataproc zarządza klastrami Google Dataproc w Google Cloud, włączając wymagane usługi i korzystając z konfiguracji określonej przez zmienne, takie jak typ maszyny czy wersja obrazu. Dzięki integracji z Google Cloud Platform, moduł ten pozwala na efektywne wykorzystanie zasobów chmurowych, optymalizując koszty i poprawiając wydajność operacji. Graf wykonania Terraform pokazuje kolejność tworzenia, aktualizacji lub usuwania zasobów, zapewniając kontrolowane i przewidywalne zmiany infrastruktury.

Graf 
digraph {
        compound = "true"
        newrank = "true"
        subgraph "root" {
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" [label = "google_dataproc_cluster.tbd-dataproc-cluster", shape = "box"]
                "[root] google_project_service.dataproc (expand)" [label = "google_project_service.dataproc", shape = "box"]
                "[root] provider[\"registry.terraform.io/hashicorp/google\"]" [label = "provider[\"registry.terraform.io/hashicorp/google\"]", shape = "diamond"]
                "[root] var.image_version" [label = "var.image_version", shape = "note"]
                "[root] var.machine_type" [label = "var.machine_type", shape = "note"]
                "[root] var.project_name" [label = "var.project_name", shape = "note"]
                "[root] var.region" [label = "var.region", shape = "note"]
                "[root] var.subnet" [label = "var.subnet", shape = "note"]
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" -> "[root] google_project_service.dataproc (expand)"
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" -> "[root] var.image_version"
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" -> "[root] var.machine_type"
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" -> "[root] var.project_name"
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" -> "[root] var.region"
                "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)" -> "[root] var.subnet"
                "[root] google_project_service.dataproc (expand)" -> "[root] provider[\"registry.terraform.io/hashicorp/google\"]"
                "[root] output.dataproc_cluster_name (expand)" -> "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)"
                "[root] provider[\"registry.terraform.io/hashicorp/google\"] (close)" -> "[root] google_dataproc_cluster.tbd-dataproc-cluster (expand)"
                "[root] root" -> "[root] output.dataproc_cluster_name (expand)"
                "[root] root" -> "[root] provider[\"registry.terraform.io/hashicorp/google\"] (close)"
                
   
9. Reach YARN UI
   
   ***place the command you used for setting up the tunnel, the port and the screenshot of YARN UI here***
   
10. Draw an architecture diagram (e.g. in draw.io) that includes:
    1. VPC topology with service assignment to subnets
    2. Description of the components of service accounts
    3. List of buckets for disposal
    4. Description of network communication (ports, why it is necessary to specify the host for the driver) of Apache Spark running from Vertex AI Workbech
  
    ***place your diagram here***

11. Create a new PR and add costs by entering the expected consumption into Infracost
For all the resources of type: `google_artifact_registry`, `google_storage_bucket`, `google_service_networking_connection`
create a sample usage profiles and add it to the Infracost task in CI/CD pipeline. Usage file [example](https://github.com/infracost/infracost/blob/master/infracost-usage-example.yml) 

   ***place the expected consumption you entered here***

   ***place the screenshot from infracost output here***

11. Create a BigQuery dataset and an external table using SQL
    
    ***place the code and output here***
   
    ***why does ORC not require a table schema?***

  
12. Start an interactive session from Vertex AI workbench:

    ***place the screenshot of notebook here***
   
13. Find and correct the error in spark-job.py

    ***describe the cause and how to find the error***

14. Additional tasks using Terraform:

    1. Add support for arbitrary machine types and worker nodes for a Dataproc cluster and JupyterLab instance

    ***place the link to the modified file and inserted terraform code***
    
    3. Add support for preemptible/spot instances in a Dataproc cluster

    ***place the link to the modified file and inserted terraform code***
    
    3. Perform additional hardening of Jupyterlab environment, i.e. disable sudo access and enable secure boot
    
    ***place the link to the modified file and inserted terraform code***

    4. (Optional) Get access to Apache Spark WebUI

    ***place the link to the modified file and inserted terraform code***
