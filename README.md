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


![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/e091135f-9b0f-4dc7-849e-5311f1030612)

For Availability policies, leave it at Standard which is ideal for most workloads while the Spot option is ideal for workload that can be interrupted.


![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/980ed1ba-2048-4489-80e8-f75ef6caaeb9)


Time limit can be set for the virtual machine which will perform an action configure by you, here we set a time limit of 5 hours, after 5 hours the instance will be Stop, other action include Terminate, Restart and Hibernate.

Leave all other options default and head over to Boot disk.

STEP 3

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/a11a0c50-e022-46b7-ad9c-7dce4af24edb)

Click CHANGE, here you select the image or snapshot which can be any operating system you want to want your virtual machine to launch with, Next select the type of boot disk type, they are various types;

Balanced persistent disk
SSD Persistent Disk
Standard Persistent Disk
Extreme Persistent Disk
Hyperdisk Balanced
Hyperdisk Extreme
Hyperdisk Throughput
Local SSDs
Cloud Storage Bucket

I will leave the default boot disk type and operating system. Now input disk size of your choice, I will be going with the default size.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/e3e820ff-e35f-4a35-8ec8-378db48a19ff)


Under Deletion rule leave the default option, this means when you delete the instance your boot disk will also get deleted so you won’t any charges for boot disk when your instance is has been deleted, the other option being “Keep boot disk” as the name suggest your instance will be deleted but your boot disk will remain and can be used to launch another virtual machine.

For Storage pool leave it unchecked

Under Encryption leave the default option which Google-managed encryption key, for the other options; CMEK and CSEK.


![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/c203c198-ebc0-4dd9-8f9a-16a0311cdc0c)

CMEK (Customer-Managed Encryption Key):

Key Management: You create and manage the encryption keys yourself using a separate Key Management Service (KMS) offered by the cloud provider.
Data Encryption: The cloud provider uses your keys to encrypt your data at rest.
Key Storage: The KMS stores your encryption keys securely, separate from the data itself.
CSEK (Customer-Supplied Encryption Key):

Key Management: You generate and manage the encryption keys entirely on your own.
Data Encryption: You provide the keys to the cloud provider, who then uses them to encrypt your data at rest.
Key Storage: You are responsible for the secure storage and management of your encryption keys.
STEP 4

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/31ef9a7c-9fb7-4b59-9771-80d851f408b6)


Under Access scopes leave the default option selected. Access scopes are a way of controlling a virtual machine (VM) instance’s access to Google Cloud services and APIs. They are essentially predefined sets of permissions assigned during VM creation, but this is being phased out in favor of IAM roles, which offer more robust and secure permission management.

Next, Firewall here you specify incoming traffic from outside a network into your virtual machine.

Leave the Observability option unchecked.

Observability -Ops Agent: This is an agent that will be installed in your virtual machine during the process of launching it, this agent collects key metrics and logs from your system and sends it to GCP for monitoring and diagnostic purpose.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/44790959-1661-423d-845f-df374fa98842)


Under Network Performance Configuration; There are two network interface card options

gVNIC: Developed specifically by Google for their Compute Engine platform. It’s the next-generation interface and the default option for newer machine types (Generation 3 and onwards). Designed for higher performance compared to VirtIO. It offers better throughput, especially for high-bandwidth configurations (50–100 Gbps). Additionally, gVNIC allows for introducing new network functionalities beyond VirtIO’s capabilities.
VirtIO: An industry standard open-source virtual I/O (input/output) specification. It’s widely supported by various cloud providers, including Google Cloud Platform (GCP) on older machine types. While established and reliable, VirtIO might not be suitable for demanding network workloads due to potential performance limitations.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/c782b47a-f1ea-4331-a42e-f31300a58a2e)

Next select a network interface which also can be referred to as a VPC, under IP stack type leave the default option which is IPv4. Only IPv4 address will be assign to your virtual machine.

Next is Primary internal IPv4 address; there are two main options for assigning an internal IP address to your instance:

Ephemeral IP: This is a temporary address assigned from the pool available in your subnet.

Restarting the instance won’t affect its internal IP, but deleting and recreating the instance will give it a new one.
You can choose to have Google automatically assign an ephemeral IP (Ephemeral (Automatic)) or manually specify one (Ephemeral (Custom)).
Static IP: If you need the IP address to remain the same even after deleting and recreating the instance, then you’ll need to select or create a static internal IP.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/bfbdac51-17d3-4aab-9a84-d108d1a59dd1)


Leave the rest default and click DONE

Scroll down to Disks, here you can add another disk to your virtual machine instance, under Security leave the default settings

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/c081b343-06a6-4f3b-81a4-884ccd2d6a0f)

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/a55fd321-4231-4bc9-8511-b1a3561b97a4)


Under VM access the console and gcloud can streamline your initial VM connection. By default, they will handle SSH key generation on your behalf, saving you a manual step, but you can manually generate your own SSH keys.

Here is a guide on generating ➡️ SSH Keys

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/deea6bcd-f93c-4b9c-ba24-4532182710ca)

Under the Automation section, here you specify a startup script. A startup script is a file that contains commands that run when a virtual machine (VM) instance boots. Startup scripts can be used to install software and updates, and to ensure that services are running within the virtual machine.

Note for Linux OS you use Bash script while for Windows you use local batch file, Command shell script, or unsigned PowerShell script.

At the right side of your console page you will see the Monthly estimate of your Virtual Machine instance with the current configuration.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/7b51568b-f007-46b8-9084-698f0f8201fb)

After reviewing, you click CREATE.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/a8ce53d9-9464-48ef-bcb2-2ff9f2ddddd7)

Congratulations !!! you have successfully launch a Virtual Machine with Google Cloud Platform.

STEP 5
Now it’s time to log into your instance.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/5a00f77b-07b7-4c21-a78f-ce44578ec90f)

At the right under connect click the SSH, automatically another browser will open.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/8cae8bf8-063e-44fe-84b1-1c2b723b26d0)

A pop screen will show requiring you to authorize

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/bbad9527-e8ff-469d-916d-0a9f55053c14)

Click authorize.

Congratulations you have successfully logged into your instance.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/32dd39ed-3501-40bb-bae6-2fbb1c0d0974)
SSH-in-browser


STEP 6
To delete or terminate your instance, go back to the instance console page, select your instance and click delete, this will remove all resources you just created.

![image](https://github.com/DiogoMic/Virtual-Machine-in-GCP/assets/89931817/829854f8-8e80-4bfd-92fc-d5f568c165a2)


Congratulations !!! you have successfully created and terminate a Virtual Machine in GCP.


