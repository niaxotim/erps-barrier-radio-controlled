### @activities true
### @explicitHints true

# ERPS STEM WEEK :: Barrier - Radio Control Receiver

## Introduction
### Introduction Step @unplugged
In this challenge, we are going to go a bit further with our code for our access barrier.  

Hopefully you already have a working barrier when pressing the ``||input:on button A||`` and ``||input:on button B||`` buttons.  

But this isn't that convenient, is it? Having to be by your barrier to make it work is a bit inefficient...  

How else could we make it work? Well, that's where the power of remote control using radio comes in!  
  
![Radio barrier](https://raw.githubusercontent.com/niaxotim/erps-barrier-basic/master/assets/no_entry.png)

## Setting up our radio
### Step 1
our BBC micro:bit has an in-built radio transmitter. This transmitter works on different 'channels'.  

We have to set which channel we want to use to transmit, and then listen on the same channel when we receive.  

Let's set our radio channel using a ``||radio:radio set group||`` block - make sure you set it to the channel assigned to you!  

#### ~ tutorialhint
```blocks
radio.setGroup(255)
```

## Setting up our barrier
### Step 2
Like in our basic example, when we turn our barrier on for the first time, it would be good to have a 'default' state, where it is closed.  

We can do this using the ``||Kitronik_ACCESSbit.Move barrier Down||`` block. Let's put this inside our ``||basic.on start||`` block.  


#### ~ tutorialhint
```blocks
radio.setGroup(255)
Kitronik_ACCESSbit.barrierControl(Kitronik_ACCESSbit.BarrierPosition.Down)
```


## Moving our barrier
### Step 3
Now we want to be able to respond to when we receive commands on our radio channel.  

Our radio can receive three types of inputs - 'numbers', 'strings' (text), and 'key:value pairs'.  

In our case, we're going to keep it simple, and check for 'strings' - we're going to look for the words "up" and "down".  

Let's start by dragging in a ``||radio:on radio received receivedString||`` block.

#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
})
```

### Step 4
When we receive "up" on the radio, we want to be able to open our barrier. We need to check what value we've received.  

Let's use an ``||logic:if-else||`` block inside our radio block.  Click on the '+' to add an 'if else' section, then use the '-' to remove the 'else' part.


#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
    if (true) {
    } else if (false) {
    }
})
```

### Step 5
Now we need to check the value that our radio has received. Drag a ``||logic:"" = ""||`` logic block to replace the condition in our 'if' statment.

In the left-hand-side of the equals statement, drag the ``||variables:receivedString||`` variable, and in the right-hand-side, type "up".

#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "up") {
    } else if (false) {
    }
})
```

### Step 6
To complete this part of the block, we need to set our barrier to be in the 'up' position when our condition is met.  

Drag a ``||Kitronik_ACCESSbit.Move barrier Up||`` block underneath our 'up' check.

#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "up") {
        Kitronik_ACCESSbit.barrierControl(Kitronik_ACCESSbit.BarrierPosition.Up)
    } else if (false) {
    }
})
```

### Step 7
Can you now figure out how to make the barrier go down again, when we receive "down" on our radio?  

Hint: it's very much like our 'up' check. Check out the hint if you get stuck ;)


#### ~ tutorialhint
```blocks
radio.onReceivedString(function (receivedString) {
    if (receivedString == "up") {
        Kitronik_ACCESSbit.barrierControl(Kitronik_ACCESSbit.BarrierPosition.Up)
    } else if (receivedString == "down") {
        Kitronik_ACCESSbit.barrierControl(Kitronik_ACCESSbit.BarrierPosition.Down)
    }
})
```

### Step 8
Connect your second BBC micro:bit and click ``|Download|`` to transfer your code.  
  
When your micro:bit powers up, does the barrier set itself to the 'down' position as expected?
  

### Barrier Basic Tutorial Complete @unplugged
Great work! You're barrier is ready to be controlled remotely!  
Now we need to create the code to send our radio signals. For that, you'll need another micro:bit, and [this tutorial](https://makecode.microbit.org/#tutorial:github:niaxotim/erps-barrier-radio-controlled-sender/erps-barrier-radio-controlled-sender-tutorial).  
![Great job](https://raw.githubusercontent.com/niaxotim/erps-barrier-radio-controlled/master/assets/great_job.png)
