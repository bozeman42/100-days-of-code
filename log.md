# 100 Days Of Code - Log
---


### Day 28: April 7, 2018

**Today's Progress**: Did the first two projects in [JavaScript30](https://javascript30.com/). The drumkit I was mostly able to recreate after only seeing the appearance and functionality of the project. I then watched the video to see if there was anything I liked about the way he did the project. I learned about 'transitionend' events so you can run code when a CSS transition is complete. Pretty cool! I also did the CSS clock, which was cool. It was good to see some creative use of CSS. Also a specific thing I learned about was cubic bezier curves for transition timing functions. [This site](http://cubic-bezier.com/#.17,.67,.83,.67) was very useful in learning how to visualize the meaning of the arguments to the `cubic-bezier(x1,y1,x2,y2)` function.

Additionally I made good on my threat to make a device (Raspberry Pi with a wee bit of wire, a resistor and an LED) that is just a light that blinks when the US House of Representatives is in session using the API at https://in-session.house.gov/. It's sitting on the arm of my couch.

**Thoughts:** While the javascript has been fairly trivial in JavaScript30 so far, there have been some good kernels of knowledge in each project so far. I feel like it's worth my time.

**Link to work:** 


### Day 27: April 6, 2018

**Today's Progress**: Worked on learning some C# on MicroSoft's site.

**Thoughts:** 

**Link to work:**


### Day 26: April 5, 2018

**Today's Progress**: Started work on the shop in ZotN. 

**Thoughts:** Got started way to late today. Not very productive at all.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn)


### Day 25: April 5, 2018

**Today's Progress**: Today I finally got the lanyard exchange piece of ZotN working. Zombies gain experience on death and Hunters... turn into zombies! It doesn't handle error as cleanly as I would like, but I will work on that in the future. 

**Thoughts:** After the react/react-redux lectures I attended I am kind of pining for the state management of react for this project.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn)


### Day 23-24: April 3-4, 2018

**Today's Progress**: I attended some lectures about react-redux and redux-saga. I had taken a udemy course on react-redux, and I heard of sagas at a react meetup. The udemy course introduced redux all at once and it was very confusing initially. After a while I started to get the hang of it. This lecture was massively superior. Redux was introduced piece by piece so that it was clear what each piece was doing. The sagas lecture was also great. I believe I will use sagas in any project where I use redux in the future.

**Thoughts:** Thank you to [Luke Schlangen @lukeschlangen](https://twitter.com/lukeschlangen) at [Prime Digital Academy](https://primeacademy.io/) for the opportunity to beta test your lectures!

**Link to work:** in private repo


### Day 22: April 2, 2018

**Today's Progress**: Today I went through some react.js prep work for some lectures I am going to attend about react-redux and redux-saga. The material was very well put together. Learned a lot about how the spread operator works (`...myArrayOrObject`) and using a function that takes in a property name to return a change handling function for that property so you can write it once and handle all input changes for many inputs.

**Thoughts:** I've worked on learning react before, but I am once again impressed with the incredible instruction at [Prime Digital Academy](https://primeacademy.io/). They break things down and introduce concepts in an order so that every piece makes sense.

**Link to work:** in private repo


### Day 21: April 1, 2018

**Today's Progress**: Today I updated my copy of a group project that was written in a way that is time sensitive. It checks the current date and tries to get data from the previous quarter. This is a portfolio piece, but it is not getting new data so it was no longer functioning properly. I wrote a workaround for this issue by coding in a date last December to the program. How I would *actually* fix it if I were to continue work on this project would be to have it check the database to see what the most recent report was and work off of that data.

I also did a bit of work on ZotN. My current problem is mostly logistical as it involves determining if a player needs to exchange an asset or just needs a new asset, and then performing the exchange. Trying to figure out what the best order of events would be for that exchange feels more awkward than I anticipated.

**Thoughts:** 

**Link to work:** [Cushman & Wakefield project](https://github.com/bozeman42/prime-teamcw/) hosted [here](https://lit-spire-97387.herokuapp.com/#/home). It's on the free tier of Heroku so it will take a bit to load the first time.
***


### Day 19-20: March 30-31, 2018

**Today's Progress**: I brought some of the things I learned in the React experiment into my AngularJS version of ZotN. I made the scanning indicator work on the common EventEmitter pattern and implemented a good-scan/bad-scan for the player select screen. I created a player-info component to use wherever I want to display player information. Just add a Player object and the information is displayed! To make things a little smoother I added 'concurrently' to the project so I can run the webpack build and my server at the same time with one terminal command. The game now displays the player that bit you if you scan a bite card on the death controller. I feel like I'm procrastinating on writing the logic for exchanging lanyards when you level up or are turned into a zombie. I need to write down a good plan of action for that and get moving.

**Thoughts:** It was kind of hard fitting in the time on the 31st. From when I woke up to late at night my time was in the hands of other people. 

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Day 18: March 29, 2018

**Today's Progress**: Today I wanted to focus on learning something new, so I decided to see how far I could get porting Zombies of the North into a React application. I got farther along than I anticipated. It was a really good React refresh and I also learned some things that will be useful whether in react or elsewhere. I just copied the server portion directly from the AngularJS version. It's a REST API so that shoudn't really need to change. I was able to get the player list displaying on the player select screen, and I got the scanner working.

One problem I had which had what I think is an elegant solution is that I have a scan indicator component that I wanted to turn green briefly when a scan occurs. The Scanner class in an interface that creates an instance of one of two different scanner types (webcam or a dedicated scanner that looks like HID input). The scan events are initiated from these internal scanner instances and the Scanner class listens for these events and passes the scanned input to a callback. Instead of trying to get the scan indicator to pry into the inner workings of the Scanner class, I added a common EventEmitter object and imported that EventEmitter into both the Scanner class and the scan indicator. The Scanner class receives the scan event from the internal components and then emits a scan event from the common EventEmitter. The scan indicator then can detect the event and turn green.

I think the next logical step is to bring the emitter into the logic that determines if the scan is valid or not and emit 'good-scan' 'bad-scan' events instead of just using the Scanner's 'scan' events to indicate what's going on. Then I can provide some feedback as to whether the data was valid rather than just showing that the scanner has some output.

**Thoughts:** Learned a lot today. Really liking the common emitter pattern. We'll see how it works out!

**Link to work:** [Zombies of the North: react edition](https://github.com/bozeman42/zotn-react/)
***


### Day 17: March 28, 2018

**Today's Progress**: Working on [Zombies of the North](https://github.com/bozeman42/zotn/). Today I wrote the code that levels up a player. It went pretty smoothly. My initial thought was doing it in a series of several queries to the database, but then I realized I can pull all of the information I need in one query, and then post the changes in one more query. Much more straightforward. I still need to write the code for having the player exchange for their new lanyard and turning killed hunters into zombies.

**Thoughts:** I'm not sure how I feel about the flow of the 'death controller'. I think I need to show the current state of the project to the other (non-programmer) folks on the team to get some comments and make sure everything is headed in the right direction.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Day 16: March 27, 2018

**Today's Progress**:

Project: [Zombies of the North](https://github.com/bozeman42/zotn/)

Today I worked on the process of scanning in any bullets / bites received and granting the appropriate players credits and points. I learned how to include multiple queries in a single transaction with node pg.

If you have a pool set up for pg you can use multiple `client.query(queryText)` calls before closing the connection and you can make these queries [atomic](https://en.wikipedia.org/wiki/Atomicity_(database_systems)) by using `BEGIN TRANSACTION;` and `COMMIT;` like so:
```JavaScript

...

client.query(`BEGIN TRANSACTION;`);
client.query(`UPDATE table1 SET column1 = value WHERE id = 1;`);
client.query(`UPDATE table2 SET column2 = value2 WHERE id = 1;`);
client.query(`COMMIT;`, resultCallback(queryError,result){ ... } );

...

```
This way, if any of the queries within the transaction fail, all changes are rolled back and no changes are made. Very useful!

Next I will need to write leveling up and exchanging lanyards for level up or turning to zombies.

**Thoughts:** Today was productive and I learned some new things, so I feel pretty good about it.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Day 15: March 26, 2018

**Today's Progress**: Worked on the next controller in ZotN: reporting if you've been killed. You are asked if you've been killed, then if will ask you to scan any bullets or bites that you received. I also tried adding a new method for restarting the scanner to the scanner service. I think it should work better and also I won't have to write a new reset function in every new controller that uses the scanner. I will give it more thorough testing soon. I noticed some slight differences in functionality between the webcam scanner and dedicated scanner so I made an effort to fix that. I had to make the webcam scanner extend the EventEmitter class so I could use addListener directly on the class as I did with the dedicated scanner.

**Thoughts:** Tired today but got some good work done.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Day 14: March 25, 2018

**Today's Progress**: Worked on some game logic. When you report kills, you are granted XP, Credits, and Score. Also the player ID is removed from the faction lanyard of your victim (they will need to collect a new lanyard the next time they check in).

**Thoughts:** I enjoyed getting to work with slightly more involved logic on the server. Multiple database queries in one request.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Days 13: March 24, 2018

**Today's Progress**: I found a bug that would show up if you tried registering two players in one 'load' of the page. When you tried to input the nickname of the second player you would be unable to enter text in the input box. This was due to event listeners not being properly removed when using navigation buttons. I was attempting to do that, but I wasn't waiting for the process to properly complete before changing the view, and with that, adding another scanner + event listeners. I was able to resolve the issue by placing the navigation code in a `.then` after the stop command is given to the scanner service.

**Thoughts:** Not much other than that there are a lot of things to keep in mind.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Days 11-12: March 22-23, 2018

**Today's Progress**: Reworked how data flowed in ZotN's kill controller. Also learned `get` and `set` syntax for making an improved class interface. It allows you to create methods that are called when you use the property access and assignment syntax. For example:

```JavaScript
class Triangle {
  constructor(width,height){
    this.width = width;
    this.height = height;
  }
  
  get area() {
    return (this.width * this.height) / 2;
  }
}
```

You would then be able to access the computed area of the triangle like so.

```JavaScript
let triangle = new Triangle(3,8);
console.log( triangle.area ); // 12
```

In ZotN an example of the usage is to assign the appropriate faction icon as a part of setting the faction of a player.

**Thoughts:** I'm learning a lot while making this project. I am looking forward to having a job so I can have the benefit of learning from more experienced developers in addition to my own research.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Days 9-10: March 20-21, 2018

**Today's Progress**: I continued work on new player registration. It's working a lot better than it was previously. I think the remaining step will be completed when I get to the 'shop' portion of the project. New players will be sent to the shop and compelled to register three bullets/bites.

**Thoughts:** I think I've improved the architecture a bit at least. I had some tough times emotionally the past couple days as I'm not great at the job hunt and that's causing a lot of stress. I'm going to start a new approach on that tomorrow and check in with a place where I interviewed last week. This evening I had coffee with a fellow I met at a Jr. Developer meetup. He's a C#/.NET developer and wants to try collaborating on a project. I'll have to brainstorm for projects to work on. I would invite him to work on ZotN, but we might sell it and I cannot pay him.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/). Check branches for recent work.
***


### Day 8: March 19, 2018

**Today's Progress**: I've come to realize that I would like a lot more of the data processing and logic to occur on the server. I did some coding preparation for this, but also did a lot of work writing flow-charts and plans for how I want the data to flow. Mostly I want the client to do is check that the data format of a scanned asset is correct, then pass that assets information to the server and proceed to request the next asset. Especially in terms of a game I want the logic - faction assignment being the thing that triggered this realization - to take place on the server. Also as a test run I tried using a raspberry pi to host only the database. It worked quite well! I think I will use a raspberry pi to host the database when we roll it out.

**Thoughts:** I still have a lot to learn when it comes to fully planning a project. I've never thought 'I wish I would have planned less' when working on a project. I think my next work on the project should be to finish fully flushing out the plan. Actually do break it into pieces.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/). Check branches for recent work.
***


### Day 7: March 18, 2018

**Today's Progress**: Main progress is that I finished asset registration and scanned all assets into the database. Woo! I also wrote a visual indicator to let the user know that a scan has been registered. No particularily interesting concepts added, just getting the work done.

**Thoughts:** It was super fun scanning in all of the assets once registration was working. 

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***


### Day 6: March 17, 2018

**Today's Progress**: I was beginning to write another callback function for taking scanner input in Zombies of the North when I realized I was writing code to validate that the input was a JSON object *again*. I didn't want to keep writing this code over and over so I wrote a kind of 'middleware' validation function that would take a callback and return a function that would take the scanner content, confirm that it was valid JSON, then call the callback with the object produced by parsing the JSON. If the scanner output is not a JSON object it will report invalid input. This way my callbacks can assume that they are receiving an object and they only need to validate that the correct type of object was passed.

```JavaScript
  validateAndParseJSON(callback) {
    const vm = this;
    return function(content) {
      if (vm.isJSON(content)) {
        callback(JSON.parse(content));
      }
    }
  }

  
  isJSON(str) {
    try {
      JSON.parse(str);
      return true;
    } catch (error) {
      console.error(error);
      return false;
    }
  }
```

I also brought the Player class up to date with the full data structure for players in the database, and wrote routes that retrieve data for all registered assets in the game. Up next for this project is writing the asset registration controller and service so I can begin scanning the prototypes into the system.

**Thoughts:** Learning principles of coding is one thing, recognizing an opportunity to apply those principles is another. Today was brought to you by **DRY**: Don't Repeat Yourself.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/tree/feature-asset-registration)
***


### Day 5: March 16, 2018

**Today's Progress**: In my zombie game project (all JavaScript, with AngularJS and ExpressJS and webpack) I rewrote the interface for the dedicated QR code scanner code so I can switch QR code reading methods between the dedicated scanner that produces keyboard input and the webcam-based scanner by changing a value in a config file. Pretty satisfying. I thought about how to do that when going through the OOP portion of the C# course. I also finalized the data structure for the project and the QR Codes for all of the game assets. The QR codes contain JSON objects which are read into the application to record events and check in. Now that the QR code format is finalized, we produced some prototypes that I can use for testing and development.

**Thoughts:** A lot of the planning for a project is in developing the data structures that are needed. There's often multiple technically valid ways of structuring your data, but some ways are easier to utilize and extend.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)
***

### Day 4: March 15, 2018

**Today's Progress**: More work on ASP.NET MVC. Today *actually* working on MVC. Got a basic CRUD app working using a MemoryCache rather than a database. 

**Thoughts:** A different world from an ExpressJS / Node.js backend. I'm very curious how you would integrate this with a front-end framework / library like Angular or React. I feel like there's got to be a way to make a REST API instead of this way of doing things. Well, WaysOfDoingThings++.

**Link to work:** [ASP.NET MVC CRUD app](https://github.com/bozeman42/csharp-crud-basics)
***


### Day 3: March 14, 2018

**Today's Progress**: I forgot my QR code scanner at home, so I decided to dive into a [Udemy course on C#, ASP.NET MVC](https://www.udemy.com/better-web-development-pro-techniques-for-success/learn/v4/overview). I got through the portion that was a C# primer and a sort of intro to OOP principles. They went through making a number guessing game, but I mostly didn't pay attention to how he built it and used it to experiment a bit. I tried to use the advice given in a talk I watched at DevFest titled "How to write code that reads like poetry." It certainly makes the main game loop understandable:
```
        public static void Main(string[] args)
        {
            Random rand = new Random();
            answer = rand.Next(10) + 1;
            while (!IsGuessCorrect())
            {
                GetGuess();
                GiveHint();
            }
        }
```
I'm beginning to feel a little more comfortable with C#, but real comfort will have to wait until I've built something real with it. I enjoyed the OOP princliples portion and I think I can bring that into some of my other projects to make it easier to swap out implementation of a feature e.g. switching between webcam based QR code scanning and the dedicated scanner. I *almost* did that part well, but I can do better. I was getting pretty tired when I tried starting the MVC section of the course, and it looks like a pretty big can of worms, so I'm saving that for another day.

**Thoughts:** Flew through the "easy" parts of this course. MVC looks like a bit of a bear, though! Got to work hard!

**Link to work:** [number guessing game.](https://github.com/bozeman42/csharp-number-guessing-game)
***

### Day 2: March 13, 2018

**Today's Progress**: I made a branch of ZotN which uses the physical QR Code scanner and it is now working the way I want it. I decided to capture all keyboard input while the QR scanner is active and turn it off when I desire user input. Thankfully I had brought in the webcam QR code scanner in a pretty modular way so I just wrote the physical scanner interface so it worked in a similar way to the webcam scanner. Minimal changes were needed to get it working with my existing controllers / services. The main problem I ran into was that when creating a custom event it seems you can only attach information to a 'detail' property on an object, so I have to access this detail property where previously the data itself was returned. (content.detail vs content)

**Thoughts:** Getting the QR code scanner to work as I desired took more effort than I anticipated, but that feels like one of the constants of development. Things usually take more effort than it appears.

**Link to work:** [physical scanner branch of ZotN](https://github.com/bozeman42/zotn/tree/feature-physical-qrcode-scanner)
***


### Day 1: March 12, 2018

**Today's Progress**: Experimented with a few methods of capturing input from a QR code reader. Time based and prefix based.

**Thoughts:** The time based method is *close* to being what I want, but I am having difficulty figuring out how to prevent text from showing up when scanned, but allowing keyboard input.

**Link to work:** [QR test code](https://github.com/bozeman42/qrtest)
