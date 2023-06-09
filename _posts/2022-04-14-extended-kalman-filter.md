---
title:  "Extended Kalman Filter for State Estimation of Mobile Robot"
mathjax: true
layout: post
categories: media
excerpt_img_url: ../assets/EKF.png
---

## Overview and Motivation

State estimation helps in accurate feedback control of a system. IN mobile robotics space this plays an important role in mapping and navigation.

The objective of this project is to estimate the state of a Jackal robot using the GPU and IMU data. Kalman Filter is an optimal state estimator. Since the dynamics of the robot is nonlinear an Extended Kalman Filter(EKF) was used to estimate the state of the robot.  

- Languages: C++
- Framework: ROS
- Software : Gazebo 
- Skills   : Nonlinear Dynamics, Sensor Fusion

## Approach

ROS Bags were provided with GPU data consisting of robot coordinates and IMU data consisting of orientation and angular velocity. Different functions were implemented for state prediction and state updation of the EKF. The Gazebo environment has a rocky terrain and hence the state of system considered was: $$[x,\ y,\ z,\ roll,\ pitch,\ yaw]$$. The control input to the system was: $$u\ =\ [v_t,\ \omega_{t}]$$ where $$v_t$$ and $$\omega_{t}$$ are the linear and angular velocities. 

A linear transformation was used to convert GPU's geoemtric cooridnates data(latitude, longitude and altitude) to cartesian cooridnates. Jacobians were evaluated to develop system model and sensor model. Covariances for process noise and measurement noise was tuned based on the knowledge of initial pose and confidence on the sensor data. 

## Result

![](/assets/EKF.jpg)

The algorithm could accurately estimate the 3D pose of the robot. An error of less than 0.5m was achieved for the 3D pose of the robot. 

## Challenges
- Hard to tune the covariances to work for corner cases like around a canyon. Posterior error might increase. 

