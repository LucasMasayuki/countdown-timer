<h1 align="center">
   🕐	<a href="#"> Countdown timer </a>
</h1>

<h3 align="center">
  Countdown timer built in svelte with sapper
</h3>

<p align="center">
  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/LucasMasayuki/countdown-timer?color=%2304D361">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/LucasMasayuki/countdown-timer">
  
  <a href="https://github.com/LucasMasayuki/countdown-timer/commits/master">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/LucasMasayuki/countdown-timer">
  </a>
    
   <img alt="License" src="https://img.shields.io/github/license/LucasMasayuki/countdown-timer">
   <a href="https://github.com/LucasMasayuki/countdown-timer/stargazers">
    <img alt="Stargazers" src="https://img.shields.io/github/stars/LucasMasayuki/countdown-timer?style=social">
  </a>

  <a href="https://rocketseat.com.br">
    <img alt="made by Rocketseat" src="https://img.shields.io/badge/made%20by-Lucas Masayuki-%237519C1">
  </a>
</p>


<h4 align="center"> 
	 Status: Finished
</h4>

<p align="center">
 <a href="#about">About</a> •
 <a href="#features">Features</a> •
 <a href="#layout">Layout</a> • 
 <a href="#tech-stack">Tech Stack</a> • 
 <a href="#author">Author</a> • 
 <a href="#user-content-license">License</a>

</p>

## About

 🕐 Countdown timer - Countdown timer developed in svelte with sapper.

---

## Features
 
- [x] User can see an event input box containing an event name field, an date field, an optional time, and a 'Start' button.
- [x] User can define the event by entering its name, the date it is scheduled to take place, and an optional time of the event. If the time is omitted it is assumed to be at Midnight on the event date in the local time zone.
- [x] User can see a warning message if the event name is blank.
- [x] User can see a warning message if the event date or time are incorrectly entered.
- [x] User can see a warning message if the time until the event data and time that has been entered would overflow the precision of the countdown timer.
- [x] User can see the elements in the countdown timer automatically decrement. For example, when the remaining seconds count reaches 0 the remaining minutes count will decrement by 1 and the seconds will start to countdown from 59. This progression must take place from seconds all the way up to the remaining days position in countdown display.
- [x] User can save the event so that it persists across sessions
- [x] User can see a countdown timer that has been defined

---

## Layout

### Mobile

<p align="center">
  <p>Light Mode</p>
  
  <img src="https://user-images.githubusercontent.com/30118832/122001196-5298f600-cd86-11eb-9350-8c581b1f1540.png">
  
  <p>Dark Mode</p>
  
  <img src="https://user-images.githubusercontent.com/30118832/122001128-3d23cc00-cd86-11eb-8fbb-7772263de00e.png">
</p>

### Web

<p align="center" style="display: flex; align-items: flex-start; justify-content: center;">
  <p>Light Mode</p>
  
  <img src="https://user-images.githubusercontent.com/30118832/122000903-ea4a1480-cd85-11eb-9d2f-f369b2234250.png">
  
  <p>Dark Mode</p>
  
  <img src="https://user-images.githubusercontent.com/30118832/122000867-dd2d2580-cd85-11eb-8085-113ddbe5d9e9.png">
</p>

---


### Pre-requisites

Before you begin, you will need to have the following tools installed on your machine:
[Git] (https://git-scm.com), [Node.js] (https://nodejs.org/en/).
In addition, it is good to have an editor to work with the code like [VSCode] (https://code.visualstudio.com/)

#### Running the application

```bash

# Clone this repository
$ git clone git@github.com:LucasMasayuki/countdown-timer.git

# Access the project folder in your terminal
$ cd countdown-timer

# Install the dependencies
$ npm install

# Run the application in development mode
$ npm run dev

# The application will open on the port: 3000 - go to http://localhost:3000

```

---

## Tech Stack

The following tools were used in the construction of the project:

#### **Website**  ([Svelte](https://svelte.dev/)  +  [TypeScript](https://www.typescriptlang.org/))

-   **[Sapper](https://sapper.svelte.dev/)**
-   **[Webpack](https://webpack.js.org/)**

> See the file  [package.json](https://github.com/LucasMasayuki/countdown-timer/package.json)

---

## Author

 <img style="border-radius: 50%; height:100px;" src="https://user-images.githubusercontent.com/30118832/122002927-c1774e80-cd88-11eb-8a1f-c5361fb01435.jpg" width="100px;" alt="Lucas Masayuki"/>
 <br />
 <sub><b>Lucas Masayuki</b></sub>
 <br />

[![Linkedin Badge](https://img.shields.io/badge/-Lucas-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/lucastamaribuchi/)](https://www.linkedin.com/in/lucastamaribuchi/) 
[![Gmail Badge](https://img.shields.io/badge/-lutamaribuchi@gmail.com-c14438?style=flat-square&logo=Gmail&logoColor=white&link=mailto:lutamaribuchi@gmail.com)](mailto:lutamaribucchi@gmail.com)

---

## License

This project is under the license [MIT](./LICENSE).

developed by Lucas Masayuki 👋🏽 [Get in Touch!](Https://www.linkedin.com/in/lucastamaribuchi/)
