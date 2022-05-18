---
title: "The LSA Gloves project"
date: 2022-05-15
autoThumbnailImage: false
thumbnailImagePosition: "top"
thumbnailImage: /img/presentation/cover_presentation.jpg
metaAlignment: center
---
In the last post I said the project with which we got our engineering degree deserved its own post. Indeed, I'm going to explain a little what was this project which consisted of a glove with sensors and embedded machine learning  connected to a Flutter mobile app that translates gestures of the Argentinian sign language.

<!--more-->
# The project
The LSA Gloves project (LSA states for *lengua de señas argentina* (argentinian sign language)) was the result of more than a year of hard work done with Jazmín Ferreiro, with the guidance of our teachers Pablo Deymonnaz and Sebastián García Marra. It's been the final project necessary to get our degrees.

<p align="center">
	<img width="100%" height="100%" src="/img/presentation/glove_photo.jpg">
	<p align="center">
		<i>Me and the glove we made using an Esp32 and IMU sensors</i>
	</p>
</p>

The goal of this project was to answer the following questions: *Could this kind of technology represent a tool to reduce the communicational breach people having speaking disabilities face? How far are we from a technological point of view to bring a technological solution to this problem?*

This idea was the result of a long process of thinking, of bringing up ideas. Our thinking process was driven by the fact that we wanted to work with technologies we found interesting from a technological point of view, applying them if possible to solve some social necessity. Working with embedded systems as well as coding in Rust was a hard requirement for instance, we then thought about communications, machine learning, virtual reality... It took us some time to define our guidelines.

In the end, those guidelines ended up being the following ones:
* Embedded systems and sensors
* Prototype design
* Mobile development
* Data analysis
* Machine learning

We liked the idea of working with a glove. In fact one of our first ideas was to work with a boxing glove with sensors which would allow us to collect data and something in the field of high intensity training. We even had the contact of the president of the argentinian box federation, whom we knew wanted to collaborate with the university in order to build some kind of technological equipment to improve the training of professional boxers. Unfortunately, Argentina was still under lockdown due to Covid-19 and all the gymnasiums were closed indefinitely. This would have affected our collaboration with the federation and we mutually decided not to move forward with the project due to these circumstances.

After this failed project attempt, we didn't fully discard the idea of a glove. We had seen there were some gloves made for virtual reality, which isn't something new, in fact this idea dates back to the 70's, when the first personal computers were being developed and there was still the debate about how the human-computer interface should be. Eventhough this kind of interface didn't prevail as much as the monitor-keyboard-mouse interface, a glove following this idea had been successfully commercialized back in the 80's. That was the PowerGlove which allowed its users to interact with the Nintendo video console with a virtual reality game. After that, the idea of the glove as a human-computer interface prevailed in our collective consciousness as something pretty cool, there have been many films featuring this kind of device such as in Minority Report, where we could see Tom Cruise controlling a futuristic screen with his hands using gloves. Nowadays there are some start ups selling this kind of product, generally to control computers, robots or -as mentioned- for virtual reality.

As we had the idea of doing something different with some social aplication, we started focusing ourselves on the idea of working with sign language. There are some projects around which involve a video camera and machine learning to recognize some positions of the hand and translate them as some gestures of sign language. Those projects have potential but face some difficulties related to the usability of the product and its technical aspects. For instance the user would need to be facing a camera constantly, affecting its usability. From a technical point of view, the machine learning algorithm's performance is affected by factors such as the luminosity or the envioronment in which the images are taken, even the color of the skin of the user can be a factor. With a glove we wouldn't have those problems, plus the device could be used anywhere. Also, we expected it'd be easier to recognize dynamic gestures -as most of the gestures in sign language aren't static- by recognizing patterns in the signals from the sensors during a determined time window.

The LSA Gloves project covered all of the technological guidelines we had thought at the beginning. The main objectives of the project were:
* Manufacturing a glove with a microcontroller and sensors in each finger to register the movements of the hands
* Developing a mobile app to interact with the glove
	* For doing data collections
	* For displaying the interpretations of the gestures
* Embedding a machine learning algorithm in the microcontroller of the glove for recognizing and interpreting gestures
* Interpreting gestures from the argentinian sign language

In short, the glove would work alongside a mobile application that'd be used for doing the data collections required to later train the machine learning algorithm and also to display the translations of the gestures; the app would be the interface to interact with the glove and the communication would be done via Bluetooth.

The embedded code had to be developed in Rust or C++ if Rust didn't work. The glove had to have bluetooth capability in order to be able to communicate with the mobile application, and it had to have an autonomy of around 1 hour of intense usage (i.e. when doing data collections).

We wanted to develop the mobile app in Flutter, because we wanted to get out from our confort zone as we already had experience working with native Android and because we thought it was an interesting option. Flutter is a new framework which allows the code to be run in multiple platforms such as Android and IOs and has a lot of utilities to build an application quickly.

For the machine learning aspect of this project, we used Edge Impulse, which allowed us to upload all the sensors data to their cloud and train a neural network using TinyML over there. It also provided us with utilities to carry a machine learning project (so we could focus on building a good dataset and a good model), like building an Arduino library with the trained neural network in it, which we could easily deploy in the embedded system using Platformio.

Being this a final project mostly investigative and having a great amount of uncertainty, we limited the scope of the project as to have a functional MVP (minimum viable product). Nevertheless, the amount of work was huge, as we didn't have experience manufacturing hardware prototypes nor coding for embedded devices. 


We presented our final project the 13th of April 2022, at the engineering faculty of the University of Buenos Aires. The team was formed on January 2021, so it's been  one year and four months of work. I won't write here about the technical details of this project (otherwise this article would be too long to read) but you can always watch the recording of our presentation as well as reading the report of this project.

![presentation](/img/presentation/cover_presentation.jpg)


During our presentation we had around 70 spectators (30 in site and 40 watching our livestream), which is a lot, counting friends, family, other students, teachers. The livestream, which was performed via Twitch, was visualized afterwards offline by around 400 viewers, which is really nice and is more than 3 times what's usual for this kind of streams at our university. The assistants were amazed with the demo and we got a score of 10 out of 10 for this project, which is nice.


The video of the stream can now be watched in YouTube:

<p></p>
{{< youtube auZ6JmNIFR8 >}}

In the end this project was super fun. What didn't we learn? Embedded programming, Rust, C++, the bluetooth protocol, 3d design, 3d printing, hardware design and manufacturing, electronics, Flutter, machine learning... even sign language and even how to stream (we became twitch streamers for a day :) ). All of that from a technical perspective, but we also acquired some other knowledge, a more soft one, related to how to start a project from scratch, how to perform investigations and why it's a good thing to give exposure to projects like this one.

About the product, being a solution for the needs of disabled people... we still have a lot of work in front of us to be able to state that "yes it is". Although it's amazing what neural networks can achieve, specially in an embeded device with such limited resources, we can't say we are close to have a functional product. As we state in the presentation, we need to add more gestures, to train the machine learning algorithm with more diverse data, we also need to take into account the left hand as well as the facial expressions which are a key component to the argentinian sign language. A technological solution can not replace the inclusion policies our target audience needs. However, I think with more resources we could achieve something interesting if we continued with this project. Anyone who'd like to continue this or to build something over the basis of our project, feel free to reach out to us, we'll gladly share all the knowledge we have as well as the code and the designs we made for the glove.

In order to put an end to this article, I'm sharing with you the final report of this project, for anyone who'd like to read it. It contains a lot of technical details and information about how we managed to build this system. It's 166 pages long written in spanish.

<div>
<p>
   <embed src="/res/graduation/Informe_trabajo_profesional.pdf" margin="8" width="100%" height="800" type="application/pdf">
</p>
</div>


