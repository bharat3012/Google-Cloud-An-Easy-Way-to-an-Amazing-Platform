# Google Cloud: An-Easy-Way-to-an-Amazing-Platform
Best descripted way to use your google cloud account for free free free :) 


## Why Clouds?

<img src="images/E2_1.png" />

So you finally decided to get into the Deep Learning game only to realize that training your Deep Learning models on your laptop takes a zillion years because either you don’t have a GPU and so you have to train your models on a CPU or you are even more unlucky and are stuck with AMD. Either way, I know how it feels and it truly sucks :(
      ## Get your game on already, AMD!

## What is cloud computing ?
<img src="images/E2_1.png" />
In cloud computing, the capital investment in building and maintaining data centers is replaced by consuming IT resources as an elastic, utility-like service from a cloud “provider” (including storage, computing, networking, data processing and analytics, application development, machine learning, and even fully managed services).
      



## Google Cloud Platform $300 free credit — incredible offer for Deep Learning students
Hello friends! 
If your a Machine Learning Engineer/ Deep Learning Engineer / Developer and still you have not already signed up for GCP account, you can enable GCP from any of your gmail account from here: https://cloud.google.com/free/ and get $300 free credit for first year(free wow gpu for 12 months). This credit is good enough for almost 1000 hours of Nvidia Tesla K80 GPUs or Nvidia Tesla P100 GPUs!!

# Before We Begin:
# --- BIG REMINDER: Make sure you stop your instances!-----

Don’t forget to stop your instance when you are done (by clicking on the stop button at the top of the page showing your instances), otherwise you will run out of credits and that will be very sad. :(

If you follow our instructions below correctly, you should be able to restart your instance and the downloaded software will still be available.

<img src="images/E2_1.png" /> 

# Create and Configure Your Account:
If you don’t have a Google Cloud account already, create one by going to the Google Cloud homepage: https://cloud.google.com/free/ and clicking on Compute. When you get to the next page, click on the blue TRY IT FREE button. If you are not logged into gmail, you will see a page that looks like the one below. Sign into your gmail account or create a new one if you do not already have an account, fill all the neccessary card details( you can use any credit card or debit card(Not SBI) as a payment method).


<img src="images/E2_1.png" /> 

Click the appropriate yes or no button for the first option, and check yes for the second option after you have read the required agreements. Press the blue Agree and continue button to continue to the next page to enter the requested information (your name, billing address and credit card information). Remember to select “Individual” as “Account Type”:

<img src="images/E2_1.png" /> 


Once you have entered the required information, press the blue Start my free trial button. You will be greeted by a page like this:
Tan Tadha da dha--- Now you in  your google cloud platform!! Click on Google Cloud Platform appeared in blue colour at top left corner, and it will take you to the main dashboard:
 
                                            Dashboard will looks like
 <img src="images/E2_1.png" /> 
 
 **Important Note

Some users, who have signed up for GCP recently, can see this error on starting their projects

                         “Quota ‘GPUS_ALL_REGIONS’ exceeded. Limit: 0.0 globally.”

Please go to `Dashboard-> IAM & admin -> Quotas` -> and search for the following quota `GPUs (all region)`.

In case limit for this is 0, you need to request Google to increase this to 1 or whatever value you need.

## Create a Virtual Instance:
To launch a virtual instance:- Follow this : `Compute Engine-> VM Instances-> Create`.
This will take you to a page that looks like the screenshot below. `(NOTE: Please carefully read the instructions in addition to looking at the screenshots. The instructions tell you generally what values I prefer to fill in :)).`

<img src="images/E2_1.png" /> 
Name: xyz --> Zone: us-central-1-c --> (click on custoomize) CPU & Memory size: 4 --> GPU :1 -Nvdia Tesla P100 or K80 (would be affordable) --> click `change` boot disk and select `ubuntu 16.04` as defualt and 100 GB disk size-->Check and select Allow HTTP traffic and Allow HTTPS traffic --> atlast Press Create.

Bravo! You have successfully created your `VM instance` -- It will be set permanently fixed which contains Internal and External IP addresses ( From here your gpu start costing your credits). See below screenshot

 <img src="images/E2_1.png" /> 
 
 ## Most Important but Most Panicking Setup in few commands lines: :)
 
`curl -O https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1604_9.0.176-1_amd64.deb
sudo apt-get update
sudo apt-get install cuda-9-0
sudo nvidia-smi -pm 1

nvidia-smi

wget "https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu1604/x86_64/libcudnn7_7.0.4.31-1+cuda9.0_amd64.deb"

sudo dpkg -i libcudnn7_7.0.4.31-1+cuda9.0_amd64.deb

echo 'export CUDA_HOME=/usr/local/cuda' >> ~/.bashrc
echo 'export PATH=$PATH:$CUDA_HOME/bin' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/extras/CUPTI/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc

sudo apt-get install python3-dev python3-pip libcupti-dev
sudo pip3 install tensorflow-gpu

# this applies to all GPUs
sudo nvidia-smi -pm 1


import tensorflow as tf

with tf.device('/cpu:0'):
    a_c = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a-cpu')
    b_c = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b-cpu')
    c_c = tf.matmul(a_c, b_c, name='c-cpu')

with tf.device('/gpu:0'):
    a_g = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[2, 3], name='a-gpu')
    b_g = tf.constant([1.0, 2.0, 3.0, 4.0, 5.0, 6.0], shape=[3, 2], name='b-gpu')
    c_g = tf.matmul(a_g, b_g, name='c-gpu')

with tf.Session(config=tf.ConfigProto(log_device_placement=True)) as sess:
    print (sess.run(c_c))
    print (sess.run(c_g))

print 'DONE!'`
 (Special Thanks `Kumar Shubham Sir` - https://github.com/krsubham48?tab=repositories : for this wonderfull series of commands) 
 
 



