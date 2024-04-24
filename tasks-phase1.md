IMPORTANT ❗ ❗ ❗ Please remember to destroy all the resources after each work session. You can recreate infrastructure by creating new PR and merging it to master.
  
![img.png](doc/figures/destroy.png)

1. Authors:

Grupa 6.

Mateusz Roszkowski (303763)

Jan Rybarczyk (304085)

Aleksandra Sobala (309420)

   https://github.com/matikurcze00/tbd-workshop-1

3. Follow all steps in README.md.


4. Select your project and set budget alerts on 5%, 25%, 50%, 80% of 50$ (in cloud console -> billing -> budget & alerts -> create buget; unclick discounts and promotions&others while creating budget).


  ![img.png](doc/figures/discounts.png)
  ![322226905-9927615e-659c-4b0b-8ac5-1f7502193401](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/aef3d489-37fd-48d3-86a1-9e04e0e378ac)


5. From avaialble Github Actions select and run destroy on main branch.
   
7. Create new git branch and:
    1. Modify tasks-phase1.md file.
    
    2. Create PR from this branch to **YOUR** master and merge it to make new release. 

![ga](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/98a7fbc3-c742-4803-b621-0b87eeba2a3e)

8. Analyze terraform code. Play with terraform plan, terraform graph to investigate different modules.

    ***describe one selected module and put the output of terraform graph for this module here***

Moduł dataproc zarządza klastrami Google Dataproc w Google Cloud, włączając wymagane usługi i korzystając z konfiguracji określonej przez zmienne, takie jak typ maszyny czy wersja obrazu. Dzięki integracji z Google Cloud Platform, moduł ten pozwala na efektywne wykorzystanie zasobów chmurowych, optymalizując koszty i poprawiając wydajność operacji. Graf wykonania Terraform pokazuje kolejność tworzenia, aktualizacji lub usuwania zasobów, zapewniając kontrolowane i przewidywalne zmiany infrastruktury.

![graph](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/550faccb-c54b-4d6a-aa95-152aad48e358)


   
9. Reach YARN UI
   
   ![image](https://github.com/matikurcze00/tbd-workshop-1/assets/101199483/d6d45580-7cd7-4fce-8060-20962cca782e)

   
10. Draw an architecture diagram (e.g. in draw.io) that includes:
    1. VPC topology with service assignment to subnets
    2. Description of the components of service accounts
    3. List of buckets for disposal
    4. Description of network communication (ports, why it is necessary to specify the host for the driver) of Apache Spark running from Vertex AI Workbech
  
    ***place your diagram here***
![Architektura_TBD](https://github.com/matikurcze00/tbd-workshop-1/assets/88709044/0d5cf1ea-4a9d-43e5-96d3-6197f74f8de6)


11. Create a new PR and add costs by entering the expected consumption into Infracost
For all the resources of type: `google_artifact_registry`, `google_storage_bucket`, `google_service_networking_connection`
create a sample usage profiles and add it to the Infracost task in CI/CD pipeline. Usage file [example](https://github.com/infracost/infracost/blob/master/infracost-usage-example.yml) 

   [File](https://github.com/matikurcze00/tbd-workshop-1/blob/dev/task-1/infracost-usage.yml)

  ![image](https://github.com/matikurcze00/tbd-workshop-1/assets/80173470/d8a8bedc-ea96-4386-8d75-93ee64686365)

  ![image](https://github.com/matikurcze00/tbd-workshop-1/assets/101199483/a5c41fc3-19e2-476a-bff0-3558f4650586)



11. Create a BigQuery dataset and an external table using SQL
    
    ***place the code and output here***
   
    ***why does ORC not require a table schema?***

  
12. Start an interactive session from Vertex AI workbench:

   ![image](https://github.com/matikurcze00/tbd-workshop-1/assets/101199483/1d89e4ed-2e54-48f4-a222-55579157af00)

   
13. Find and correct the error in spark-job.py

W szczegółach DAGu znajowały się logi błędu, który był powodowany przez złą konfigurację nazwy kubełka (gs://tbd-2024l-9910-data/data/shakespeare/). 
W spark-job.py zmieniliśmy nazwę tego kubełka na naszą własną:

DATA_BUCKET = "gs://tbd-2024l-303763-data/data/shakespeare/"

![image](https://github.com/matikurcze00/tbd-workshop-1/assets/101199483/c0b5304d-9b7a-4c60-a703-0ee4449c8f08)
Przed zmianą nazwy kubełka żaden job nie kończył się sukcesem. Po jego zaktualizowaniu job został ukończony pomyślnie.

14. Additional tasks using Terraform:

    1. Add support for arbitrary machine types and worker nodes for a Dataproc cluster and JupyterLab instance

    ***place the link to the modified file and inserted terraform code***
    
    3. Add support for preemptible/spot instances in a Dataproc cluster

    ***place the link to the modified file and inserted terraform code***
    
    3. Perform additional hardening of Jupyterlab environment, i.e. disable sudo access and enable secure boot
    
    ***place the link to the modified file and inserted terraform code***

    4. (Optional) Get access to Apache Spark WebUI

    ***place the link to the modified file and inserted terraform code***
