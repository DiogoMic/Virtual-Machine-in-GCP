# Virtual-Machine-in-GCP
Launch Your First GCP VM in Minutes: A Beginner’s Guide.

So we are going to launch a virtual machine on the google cloud platform.

Head over to your google cloud console homepage, select the project you would want to use

### STEP 1

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/d88b3b72-ac47-4c1f-b27f-412b3133d4fc)

Next click the menu icon at the left top to open the menu panel.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/2516101a-3b15-492d-be85-7bd06455740a)

STEP 2
Next click CREATE INSTANCE

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/03b76ee3-923f-41c2-8e93-d97f45e654ae)

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/f04916ec-da82-4217-af32-81ce2acfa3cd)


If it’s the first time you are accessing your Compute Engine, you will be prompted to ENABLE the Compute Engine API, after successfully enabling the API, click Compute Engine and select VM instances.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/b04b7cd0-df8c-436e-9c9c-0de911551f9f)


Now give your a Name, select your region and Zone, remember to select a region where you have a VPC resource created, without a VPC in that region your VM instance creation won’t work.

Under Machine configuration, leave the default selection as General purpose. There are other options like Compute Optimised; which are used for Application with heavy compute power, Memory Optimised: used for application with heavy memory usage, Storage Optimised: used for application that will be needing high volume of storage and lastly GPUs; this are used for graphic intense application.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/547f15c0-46a4-4e67-a1f0-964238d5eb30)

Leaving the default selection in Machine configuration, head over to ADVANCED CONFIGURATIONS.
