# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---

This is the first project of the Udacity "Self-Driving Car" Nanoprogram. In this project you are required to detect lane lines in images using Python 3 and OpenCV. I learned a lot as a robotisist with Mechanical Engineering background. This document will cover a quick reflection of the project, and tips for solving both technical and software setting issues. 

Reflection 
---

An OpenCV based vision pipeline was developed for detecting lane lines and then drawing averaged boundary lines in the road videos. The pipeline can be developed and tested by the images in the "test_images" first. Then videos in the "test_videos" folder can be processed. In the pipeline development, color selection, Gaussian blurring, Canny edge detection, region of interest selection, and Hough transform line detection techniques were used. 

The built pipeline works fine for straight white and yellow line detections, but doesn't work for curved lines. This is due to the fact that the used "draw_lines()" method assuming the lane lines were linear. Moreover, even replacing the line drawing method, the "region_of_interest()" may loss normal functions for the steep roads. 

In order to work for the curved and steep road lane detections, more advanced and adaptive region of interest selection technique need to be applied. 

Technical Setting Issues
---

This section cover solutions for the software settings problems I met before I started programming. All solutions are for Windows. 

**Step 1:** Set up the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md)

The miniconda never installed properly using the provided link, so I downed the full version of [Anaconda](https://www.anaconda.com/download/). The Udacity course [Anaconda and Jupyter Notebooks](https://classroom.udacity.com/courses/ud1111) is useful for quick review, you got the basic feeling about went through the materials. 

After installing [Anaconda](https://www.anaconda.com/download/), I got totally confused to the following instructions. I did some search and found a guy with similar difficulties: [The Anaconda installation guide is so confusing](https://discussions.udacity.com/t/the-anaconda-installation-guide-is-so-confusing/312695). Based on the answers and my own trial and error, I summarized the following steps: 

1. Install the [Git](https://git-scm.com/downloads), open "Git CMD", clone the environment by pasting "git clone https://github.com/udacity/CarND-Term1-Starter-Kit.git" 

2. Open "Anaconda Prompt", navigate to the "CarND-Term1-Starter-Kit"folder by using "cd CarND-Term1-Starter-Kit" 
Set up the environment using "conda env create -f environment.yml" in "Anaconda Prompt"
Verify that the carnd-term1 environment was created in your environments by using "conda info --envs" in "Anaconda Prompt"
Activate the environment by using "activate carnd-term1". This MUST be done each time you begin a new working session i.e. open a new terminal window. 

**Step 2:** Open the code in a Jupyter Notebook

You will complete the project code in a Jupyter notebook.  If you are unfamiliar with Jupyter Notebooks, check out <A HREF="https://www.packtpub.com/books/content/basics-jupyter-notebook-and-python" target="_blank">Cyrille Rossant's Basics of Jupyter Notebook and Python</A> to get started.

Jupyter is an Ipython notebook where you can run blocks of code and see results interactively.  All the code for this project is contained in a Jupyter notebook. To start Jupyter in your browser, use terminal to navigate to your project directory and then run the following command at the terminal prompt (be sure you've activated your Python 3 carnd-term1 environment as described in the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) installation instructions!):

`> jupyter notebook`

A browser window will appear showing the contents of the current directory.  Click on the file called "P1.ipynb".  Another browser window will appear displaying the notebook.  Follow the instructions in the notebook to complete the project.  

**Step 3:** Complete the project and submit both the Ipython notebook and the project writeup

## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).

