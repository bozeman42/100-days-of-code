# 100 Days Of Code - Log


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


### Days 9-10: March 20-21, 2018

**Today's Progress**: I continued work on new player registration. It's working a lot better than it was previously. I think the remaining step will be completed when I get to the 'shop' portion of the project. New players will be sent to the shop and compelled to register three bullets/bites.

**Thoughts:** I think I've improved the architecture a bit at least. I had some tough times emotionally the past couple days as I'm not great at the job hunt and that's causing a lot of stress. I'm going to start a new approach on that tomorrow and check in with a place where I interviewed last week. This evening I had coffee with a fellow I met at a Jr. Developer meetup. He's a C#/.NET developer and wants to try collaborating on a project. I'll have to brainstorm for projects to work on. I would invite him to work on ZotN, but we might sell it and I cannot pay him.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/). Check branches for recent work.


### Day 8: March 19, 2018

**Today's Progress**: I've come to realize that I would like a lot more of the data processing and logic to occur on the server. I did some coding preparation for this, but also did a lot of work writing flow-charts and plans for how I want the data to flow. Mostly I want the client to do is check that the data format of a scanned asset is correct, then pass that assets information to the server and proceed to request the next asset. Especially in terms of a game I want the logic - faction assignment being the thing that triggered this realization - to take place on the server. Also as a test run I tried using a raspberry pi to host only the database. It worked quite well! I think I will use a raspberry pi to host the database when we roll it out.

**Thoughts:** I still have a lot to learn when it comes to fully planning a project. I've never thought 'I wish I would have planned less' when working on a project. I think my next work on the project should be to finish fully flushing out the plan. Actually do break it into pieces.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/). Check branches for recent work.


### Day 7: March 18, 2018

**Today's Progress**: Main progress is that I finished asset registration and scanned all assets into the database. Woo! I also wrote a visual indicator to let the user know that a scan has been registered. No particularily interesting concepts added, just getting the work done.

**Thoughts:** It was super fun scanning in all of the assets once registration was working. 

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)


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


### Day 5: March 16, 2018

**Today's Progress**: In my zombie game project (all JavaScript, with AngularJS and ExpressJS and webpack) I rewrote the interface for the dedicated QR code scanner code so I can switch QR code reading methods between the dedicated scanner that produces keyboard input and the webcam-based scanner by changing a value in a config file. Pretty satisfying. I thought about how to do that when going through the OOP portion of the C# course. I also finalized the data structure for the project and the QR Codes for all of the game assets. The QR codes contain JSON objects which are read into the application to record events and check in. Now that the QR code format is finalized, we produced some prototypes that I can use for testing and development.

**Thoughts:** A lot of the planning for a project is in developing the data structures that are needed. There's often multiple technically valid ways of structuring your data, but some ways are easier to utilize and extend.

**Link to work:** [Zombies of the North](https://github.com/bozeman42/zotn/)


### Day 4: March 15, 2018

**Today's Progress**: More work on ASP.NET MVC. Today *actually* working on MVC. Got a basic CRUD app working using a MemoryCache rather than a database. 

**Thoughts:** A different world from an ExpressJS / Node.js backend. I'm very curious how you would integrate this with a front-end framework / library like Angular or React. I feel like there's got to be a way to make a REST API instead of this way of doing things. Well, WaysOfDoingThings++.

**Link to work:** [ASP.NET MVC CRUD app](https://github.com/bozeman42/csharp-crud-basics)


### Day 3: March 14, 2018

**Today's Progress**: I forgot my QR code scanner at home, so I decided to dive into a [Udemy course on C#, ASP.NET MVC](https://www.udemy.com/better-web-development-pro-techniques-for-success/learn/v4/overview). I got through the portion that was a C# primer and a sort of intro to OOP principles. They went through making a number guessing game, but I mostly didn't pay attention to how he built it and used it to experiment a bit. I tried to use the advice given in a talk I watched at DevFest titled "How to write code that reads like poetry." It certainly makes the main game loop understandable:
```C#
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


### Day 2: March 13, 2018

**Today's Progress**: I made a branch of ZotN which uses the physical QR Code scanner and it is now working the way I want it. I decided to capture all keyboard input while the QR scanner is active and turn it off when I desire user input. Thankfully I had brought in the webcam QR code scanner in a pretty modular way so I just wrote the physical scanner interface so it worked in a similar way to the webcam scanner. Minimal changes were needed to get it working with my existing controllers / services. The main problem I ran into was that when creating a custom event it seems you can only attach information to a 'detail' property on an object, so I have to access this detail property where previously the data itself was returned. (content.detail vs content)

**Thoughts:** Getting the QR code scanner to work as I desired took more effort than I anticipated, but that feels like one of the constants of development. Things usually take more effort than it appears.

**Link to work:** [physical scanner branch of ZotN](https://github.com/bozeman42/zotn/tree/feature-physical-qrcode-scanner)


### Day 1: March 12, 2018

**Today's Progress**: Experimented with a few methods of capturing input from a QR code reader. Time based and prefix based.

**Thoughts:** The time based method is *close* to being what I want, but I am having difficulty figuring out how to prevent text from showing up when scanned, but allowing keyboard input.

**Link to work:** [QR test code](https://github.com/bozeman42/qrtest)
