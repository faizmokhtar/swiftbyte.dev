---
title: How to load Lottie animation from remote URL
description: ""
date: 2022-04-25T15:06:07.098Z
preview: ""
draft: false
lead: A quick guide on how to load Lottie animation from remote URL
tags:
  - ios-libraries
  - animation
categories: ""
slug: load-lottie-animation-remote-url
---

[Lottie][1] is an open source library from Airbnb that allows us to ship beautiful animations in our app with little effort.

Usually we ship [Lottie][1] animation by including the `.json` file in our app but [Lottie][1] also allows us to load the animation through remote URL as well. We can do it by calling `Animation.loadedFrom(url:closure:animationCache)` function

Here is an example on how to do it:

```swift

    // create the animation view to play the Lottie's animation
    lazy var lottieView: AnimationView = {
        let view = AnimationView()
        view.translatesAutoresizingMaskIntoConstraints = false
        view.loopMode = .loop
        view.contentMode = .scaleAspectFit
        return view
    }()

    func viewDidLoad() {
        ...
        // load lottie from valid remote url
        let url = URL(string: "https://assets1.lottiefiles.com/packages/lf20_ujlt8xt3.json")!
        Animation.loadedFrom(url: url, closure: { [weak self] animation in
            self?.lottieView.animation = animation
            self?.lottieView.play()
        }, animationCache: LRUAnimationCache.sharedCache)
        ...
    }    
```

That's it. Here is the full gist if you want to run it in Xcode. Make sure you have already include [lottie-ios][2] library in your project to avoid any error. 

{{<gist faizmokhtar fc9cf870d93018dbb66fa7894e68fcb2>}}

Here's the Lottie animation in action courtesy of [lottiefiles.com](https://lottiefiles.com/):

<p align="center">
  <img width="600" height="200" src="/remote-lottie-animation.gif">
</p>

![Lottie animation in action](/remote-lottie-animation.gif)

[1]: https://airbnb.design/lottie/
[2]: https://github.com/airbnb/lottie-ios