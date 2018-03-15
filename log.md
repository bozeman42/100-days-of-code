# 100 Days Of Code - Log

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

<!-- 
### Day 0: February 30, 2016 (Example 2)
##### (delete me or comment me out)

**Today's Progress**: Fixed CSS, worked on canvas functionality for the app.

**Thoughts**: I really struggled with CSS, but, overall, I feel like I am slowly getting better at it. Canvas is still new for me, but I managed to figure out some basic functionality.

**Link(s) to work**: [Calculator App](http://www.example.com)


### Day 1: June 27, Monday

**Today's Progress**: I've gone through many exercises on FreeCodeCamp.

**Thoughts** I've recently started coding, and it's a great feeling when I finally solve an algorithm challenge after a lot of attempts and hours spent.

**Link(s) to work**
1. [Find the Longest Word in a String](https://www.freecodecamp.com/challenges/find-the-longest-word-in-a-string)
2. [Title Case a Sentence](https://www.freecodecamp.com/challenges/title-case-a-sentence) -->
