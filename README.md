# TelloPoseController

This is a repository for a DJI Tello Pose controller. With this, you can use the DJI tello's camera to control your drone base on body movements. 
Currently, this is fully functional, and working. 

[YouTube Video:](https://youtu.be/xK86IWhwe3g) https://youtu.be/xK86IWhwe3g



Libraries Required:
- Mediapipe
- CV2
- Numpy
- DJItellopy
- Pickle
- Pandas


## Files: 
1.  videos2frame.py
  - Converts video from computer into frames
2. my_pose_train.py
  - Appends the .csv file from 1
3. knncvs.py
  - Trains KNN File and saves it as .pickle file extention
4. PoseModule.py
  - Test model without the drone running
5. drone_pose_control.py
  - Run with a drone
6. Poses_knn
  - .pickle file with the model saved

# How does it work? 

Inside my Python VENV, the first Python File we see is drone_pose_control.py. This file is the one that takes in our captured camera movements, processes them onboard or computer, and then sends it back to the drone to conduct the decided movement. Next, we have PoseModule.py. This is a way to test the code without having to use a DJI Tello drone. 

Those are the main control front end scripts. Now, lets look at the backend scripts. But before we look at the backend script, we need to understand how the program classifies and recognizes poses. For our code, we’re employing a very special type of neural network, called KNN.  Now, you may be wondering, what exactly is a KNN? The k-nearest neighbors (KNN) algorithm is a simple, easy-to-implement supervised machine learning algorithm that can be used to solve both classification and regression problems. Pause! Let us unpack that.

A supervised machine learning algorithm (as opposed to an unsupervised machine learning algorithm) is one that relies on labeled input data to learn a function that produces an appropriate output when given new unlabeled data. Imagine a computer is a child, we are its supervisor (e.g. parent, guardian, or teacher), and we want the child (computer) to learn what a pig looks like. We will show the child several different pictures, some of which are pigs and the rest could be pictures of anything (cats, dogs, etc).  When we see a pig, we shout pig. When we see anything else, we shout not pig. So, for our use case, instead of a pig, we’re doing a much more complex recognition based on the position of our joints, as classified by this Media Pipe recognition module. As we can see, there are 32 points that can be classified and recognized by this module. 
