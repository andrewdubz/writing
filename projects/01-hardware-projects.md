My current work project is finishing at the end of November for most of the team. So I'm thinking about what's next.

I was resisting learning Kotlin because I was looking for something more "fun" but actually once I've started going through my Kotlin book I'm quite enjoying it.

As much as I feel pressure to prioritise keeping my skills aligned with what the market wants, and will pay well for, I'm wanting to increase the amount of play. And I keep coming back to that plywood box of switches and lamps that my Dad made for me and intrigued me, leading to a curiosity with electronics and then onto coding. I should add that my Mum supported this too, probably because she could see the economic benefit. Maybe a hardware-plus-code project will bring somebody else the same joy that that first gizmo brought me.

Hardware projects bring additional challenges in getting started beyond pure software projects. You need the kit in the first place. And you need some understanding of how to connect things safely. And then there is the cost and practicality of getting the kit. My current thinking is to use a pre-built device like a [Kitronik](https://kitronik.co.uk/blogs/resources/how-to-make-a-custom-football-pitch-for-move-motor). This comes with [Python code](https://github.com/KitronikLtd/Kitronik-Pico-Mini-Controller-MicroPython) already supplied. Having pre-built libraries may be useful in some cases but I think it makes more sense to teach the coding from first principles. 

I looked at using the popular [Go programming language](https://tinygo.org/docs/tutorials/blinky/). But frankly the experience is poor.

I followed the simple example and tried to "flash" it to the board.

The programme complained that I was using the wrong version.

So I tried to update it. That failed because I had to update my local version of "xcode-select". So I downloaded that, which took 10 minutes or so. When I tried it again I was told that my version of Xcode was out of date. And that's on a Mac. I wonder if the experience on Windows would be better or worse.

[As an aside, my wife keeps reminding me to do things that I enjoy. This project is one possible way to accomplish that. I think another is to collaborate on creative projects with others ... corporate contracting projects don't score so highly in this respect.]

So I had a look at another approach. And I was reminded of the [Kaluma](https://kalumajs.org/download/) project which allows us to write JavaScript programmes that run on the device.

To make this happen we need to update the firmware code that runs on the board; this is the "interpreter" that knows what to do with the code we send to the board.

The way we do this is to plug in the (Raspberry Pi Pico) board with the "BOOT" button pressed, and connect with a micro-USB cable to the computer. This mounts the board as a removable device onto which we can drag the [firmware](https://kalumajs.org/download/).

When the UF2 file has been copied onto the board it reboots and is now able to accept JavaScript programmes.

Now we can load an [example](https://github.com/kaluma-project/examples/tree/main/blink) programme onto the board. We load the programme by running

`kaluma flash <filename>`

Here is an example "Hello World" programme which blinks an LED in JavaScript.

```
var led = 25;
pinMode(led, OUTPUT);
setInterval(() => {
  digitalToggle(led);
}, 1000);
```

This does actually make the LED blink; I'm having some issues with my video uploading service this morning so for now you'll have to take my word for it. :slight_smile: 
