---
layout: post
title: "Clock animation in Swift"
categories: [iOS, Swift]
tags: [iOS, Swift, animations, timer]
---

A live clock made with SwiftUI. The clock is a transparent image without the hands. The animated portions are the thin rectangle views that rotate in a circle with the help of a ```timer``` object and ```rotationEffect```.

<div style="text-align: center;">
<video width="640" height="480" autoplay loop muted>
  <source src="/assets/vids/giphy.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
</div>

### How to get a transparent Image

1. Go to google and search for an image. In this case, search for "a clock with no hands."
2. Click the images tab
3. Click on tools.
4. Click colors and select transparent.

## Code to Display Clock

```
Image(.clockWithNoHand)
    .overlay{
        Rectangle() //Second hand
            .frame(width: 2, height: 120) 
            .offset(y: -30)
            .rotationEffect(.degrees(secondAmount))
        Rectangle() //Minute hand
            .fill(.green) 
            .frame(width: 2, height: 120)
            .offset(y: -30)
            .rotationEffect(.degrees(minuteAmount))
        Rectangle() //Hour hand
            .fill(.red)
            .frame(width: 2, height: 120)
            .offset(y: -30)
            .rotationEffect(.degrees(hourAmount))
    }
    .onAppear{
      runClock()
    }
```

### RunClock() Function

```
func runClock(){
    Timer.scheduledTimer(withTimeInterval: 1.0, repeats: true) { s in
        secondAmount += 6.0 // 360 / 60
        minuteAmount += 0.1 // 360 / (60 * 60)
        hourAmount += hourCalcAmount // 360 / (60 * 60 * 12)
        
        //secondamount, hourAmount, minuteamount dont go to infinity!
        if Int(secondAmount) == 360 {
            secondAmount = 0.0
        }
        else if Int(minuteAmount) == 360 {
            minuteAmount = 0.0
        }
        else if Int(hourAmount) == 360 {
            hourAmount = 0.0
        }
    }
}
```