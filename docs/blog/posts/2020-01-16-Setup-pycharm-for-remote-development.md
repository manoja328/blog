---
layout: post
title:  "Setup pycharm for remote development"
excerpt: Setup pycharm for remote development
date:   2020-01-16 15:19:37 -0400
categories: welcome
---

If you are like me who does  Machine Learning  using a think client laptop then this post might serve you.   I  use  my MacBook Pro 2015 to do most of the coding/debugging and  data exploration. While, all the  heavy computation happens on  GPUs in the remote server.  Ideally,  I wanted a platform with both remote folder mounting or explorer options with a decent IDE that support python programming.  I started with Spyder IDE  because of its simplicity. Besides,  it also has a good  support for visualization of  native python data types and some advanced data types like numpy and  pandas arrays. But, Spyder's debugging it still not that user friendly. I also tried VSCode editor after  installing the  "remote-SSH" extension from their applications marketplace. It was easy to setup but the fact that it was abruptly  closing SSH sessions and  asked to restart the editor constantly  frustrated me. Not to mention, the debugger was still not that advanced in VSCode too.

Pycharm is a relatively well built IDE for python programming.  Also, I found that their debugging experience is much better than  other python IDEs. I recently found out that they also had support for remote programming. I decided to try it and so far I have found it to be reasonably good. Here, I want to share my steps for setting it up in Pycharm.

- First you need to create a new project and select  the remote ssh interpreter as the option. Also select the remote project location.
  ![image-20200901162756884](/assets/image-20200901162756884.png)

- Then go to Tools -> Deployment -> Configuration and setup:

  - Root Path:  `<folder from remote machine>`

  - Mappings: ( so when you press the run button Pycharm will run files remotely)

    - Local path: `<folder on your laptop>`
    - Deployment path: /

    ![image-20200907180811374](/assets/image-20200907180811374.png)

- Also in Tools -> Configuration set it to upload only when `Windows + S` is pressed. 
  ![image-20200901163246462](/assets/image-20200901163246462.png)

**Note: You can make multiple configurations for the same project  and easily deploy the same project on any remote machine.**

With this, I can run  code in my remote machine with files available  in  both the remote and local machines.  I  set it up so that the files from local machine are uploaded to the remote machine and not both ways. So now when I save huge model checkpoints,  images from dataset, predictions or  log files, etc.  they only exist on remote machines and are not pulled to the local machine. I can still access  any remote files from  *Tools -> Deployment -> Browse Remote Host.*

Now my final setup looks like this: 

![image-20200901165201491](/assets/image-20200901165201491.png)

​				[ The left file explorer is for my local folder and the right one for remote machine]



##  A common error: Remote deployment settings not found!!:

Pycharm for some reason  complains with the error message saying *remote deployment  settings for remote debugger not found*. You can fix that by adding path mappings  from project  interpreter settings tab.

![image-20200907181156083](/assets/image-20200907181156083.png)



A word of warning, if you are tryin to debug in pycharm then rather than always showing all the variables only show the variables you need to watch.

![image-20210116224926023](/assets/image-20210116224926023.png)



Hope this helps. Cheers !
