# What is Volttack?![](https://img.shields.io/badge/License-USSLab-blue)
We analyze the security of Internet of Things (IoT) devices from the perspective of sensing and actuating. Particularly, we discover a vulnerability in power supply modules and proposed Volttack attacks. To launch a Volttack attack, attackers may compromise the power source and inject malicious signals through the power supply module, which is indispensable in most devices. Eventually, Volttack attacks may cause the sensor measurement irrelevant to reality or maneuver the actuator in a way disregarding the desired command. 
To understand Volttack, we systematically analyze the underlying principle of power supply signals affecting the electronic components, which are building blocks to constitute the sensor or actuator modules. Derived from these findings, we implement and validate Volttack on off-the-shelf products: 6 sensors and 3 actuators, which are used in applications ranging from automobile braking systems, industrial process control to robotic arms. The consequences of manipulating the sensor measurement or actuation include doubled car braking distance and a natural gas leak. The root cause of such a vulnerability stems from the common belief that noises from the power line are unintentional, and our work aims to call for attention to enhancing the security of power supply modules and adding countermeasures to mitigate the attacks. 

<img src=./image/overview.png width="700px"/> 

# Background
To understand the underlying principle of Volttack, we introduce the background of IoT devices from three levels, and from large to small they are the IoT device and system level, the module level, and the electronic component level, respectively.
The Internet of Things (IoT) is the network of physical objects that are capable of connecting and exchanging data with other devices over the Internet for the purpose of serving various applications, e.g., smart manufacturing, home automation, or self-driving. IoT devices, such as smart speakers, consist of multiple modules, e.g., at least a power supply module, a sensing module, a computing module, and an actuation module, such that they can perceive the environment, make decisions, and control the physical world. 
The power supply, sensor, and actuator modules are all composed of electronic components, which are elements of the circuit and include resistors, capacitors, inductors, amplifiers, etc.

<img src=./image/IoT_background.png width="700px"/>

# Attack Mechanism
Sensing and actuating are enabled by analog circuits that are made of various interconnected electronic components. We categorize the power supply's effect on elementary electronic components into two basic mechanisms: interfering with the input and modifying the behavior.
In the first mechanism, the power supply signal is superimposed on the input of an electronic component, and power noises may act as an interfering input that directly changes the component's output.
In the second mechanism, the power supply signal drives the electronic component and may modify its input/output relationship. As a result, power noises may indirectly change the component's output even if the input is kept still. 

<img src=./image/mechanism.png width="700px"/>

# Attack Evaluation
We evaluate the performance of Volttack on 6 sensors and 3 actuators to demonstrate the real-world threat of the attack, which are used in applications ranging from automobile braking systems to industrial process control to robotic arms. In summary, we have achieved the following manipulations.
- For a force sensor (DYTB-002) that is used to measure the force pressure of a driver onto the brake pedal, injecting a signal of 1V at a frequency of 342MHz to the 24V operating voltage can decrease the sensor output by 122N, which is half of the real force and can cause the braking distance to be doubled.
- For a temperature sensor (DHT11) that is used to measure industrial environment temperature, injecting a signal of 0.5V at a frequency of 121MHz to the 12V operating voltage can increase the sensor output by 139&#176;C, which may lead to false excess cooling, a key cause of the British dye factory explosion.
- For a servo (Futaba S9602) that is used to control the joint rotation of robotic arms, injecting a signal of 1.3V at a frequency of 314MHz to the 5.5V operating voltage can rotate the joint 58.4 degrees clockwise, which may jeopardize production or even injure the nearby operator.
- For a valve (Fulaite 05) that is used in the flow control of natural gas, injecting a signal of 0.5V at a frequency of 75MHz to the 5V operating voltage can open the closed valve to 34%, which may cause a gas leak.

<img src=./image/setup.png width="700px"/>


# End-to-end Attack
To demonstrate the practicality, we perform end-to-end attacks with three methods: fabricating a malicious battery with the attack devices embedded, placing a current injection probe on the power cable, and connecting the attack devices to the power network using a customized coupler.
- Counterfeit battery

<img src=./image/battery.png width="700px"/>

- Current injection probe

<img src=./image/BCI.png width="700px"/>

- Customized coupler

<img src=./image/coupler.png width="700px"/>

# Video Demos
Here are **video demos** showing the real-world impact of the Volttack.

<!-- <img src=./demo/servo-coupler.gif width="500px" /> -->

<!-- <video id="video" controls="" preload="none" poster="封面">
      <source id="mp4" src=./demo/servo-coupler.mp4 type="video/mp4">
</videos> -->

<video id="video" controls="controls" preload="none">
      <source id="mp4" src="./demo/servo-coupler.mp4" type="video/mp4" width="700px">
</video>

<video id="video" controls="controls" preload="none">
      <source id="mp4" src="./demo/valve-coupler.mp4" type="video/mp4" width="700px">
</video>

<video id="video" controls="controls" preload="none">
      <source id="mp4" src="./demo/valve-probe.mp4" type="video/mp4" width="700px">
</video>

# Citation

```

```

# Contact

- Prof. Wenyuan Xu (<wyxu@zju.edu.cn>)
- Prof. Xiaoyu Ji (<xji@zju.edu.cn>)

# Powered by

<table bgcolor="white">
<tr valign="middle">
<td width="50%" align="center" colspan="2">
 <a href="http://usslab.org">Ubiquitous System Security Laboratory (USSLab) 
</td>
<td width="50%" align="center" colspan="2">
  <a href="http://www.zju.edu.cn/english">Zhejiang University 
</td>
</tr>
<tr valign="middle">
<td width="50%" align="center" colspan="2">
  <a href="http://usslab.org"></a>
  <a href="http://usslab.org"><img 
src="./image/usslab_logo.png" height="80"></a>
</td>
<td width="50%" align="center" colspan="2">
  <a href="http://www.zju.edu.cn/english/"></a>
  <a href="http://www.zju.edu.cn/english/"><img 
src="./image/zju_logo.png" height="80"></a>
</td>
</tr>
</table>
