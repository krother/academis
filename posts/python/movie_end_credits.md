
# Creating End Credits for a Movie in Python

Recently, I happened to participate in a TV production. 
The part behind the scenes involved creating the end credits, and somehow the task landed on my desk. Unsurprisingly, I chose to solve the task with **Python**. You probably could do the same in 10 minutes using Windows MovieMaker or the IPhone 7, but my solution contains a panda. 

This is what the outcome looks like:

<iframe width="420" height="315" src="https://www.youtube.com/embed/2OZP4taiXqg" frameborder="0" allowfullscreen></iframe>

Let's see how it was done:

----

## 1. Create fake names

I used the [`faker` library](http://faker.readthedocs.io/en/latest/) to generate random names and job descriptions. `faker` can generate all kinds of test data, but here we are happy with just a list of `(job, name)` tuples:

    :::python
    from faker import Factory

    N_NAMES = 30

    fake = Factory.create()
    text = []
    while len(text) < N_NAMES:
        job = fake.job()
        name = fake.name()
        if len(job) < 25:
            text.append((job, name))

----

## 2. Create a static image clip 

I wanted to have an immobilized logo visible throughout the clip. In this example, I replaced the producers logo with a panda:

![panda image](images/panda.png)

The [`moviepy` library](https://zulko.github.io/moviepy/) by *zulko* creates movie clips from images quite easily. It benefits from `moviepy` methods like resizing and repositioning right away. The only thing you *must* do is to set the duration (in seconds):

    :::python
    from moviepy.editor import ImageClip

    DURATION = 25
    POSITION = 950, 300
    SIZE = 235, 298

    logo = ImageClip("panda.png").resize(SIZE).set_pos(POSITION)
    logo.duration = DURATION

----

## 3. Create a clip with moving text

Creating a real animation with text was more work. In addition to `moviepy`, I needed the [`gizeh` library](https://github.com/Zulko/gizeh) (also by *zulko*) that creates vector graphics and converts them to `numpy` matrices. The core part is a function that is called for each frame of the clip. Because of the two text columns, the code is a bit longer than a minimal script would be.

    :::python
    from moviepy.editor import CompositeVideoClip
    import gizeh as gz
    import moviepy.editor as mpy

    W, H = 1200, 1000

    LEFTCOL = 450
    RIGHTCOL = 490
    TEXTSIZE = 28
    LINE_HEIGHT = 50

    SCROLLSPEED = 130
    BOTTOM_START = H * 1.2

    def make_frame(t):
        """Draw text elements in each frame"""
        surface = gz.Surface(W, H, bg_color=(0,0,0))
        for i, line in enumerate(text):
            job, name = line
            ypos = LINE_HEIGHT * i - int(t * SCROLLSPEED) + BOTTOM_START
            
            txt = gz.text(job, "Amiri", TEXTSIZE, fontweight='bold', \
                          h_align='right', fill=(1,1,1))
            left = gz.Group([txt]).translate((LEFTCOL, ypos))
            left.draw(surface)
            txt = gz.text(name, "Amiri", TEXTSIZE, \
                          fontweight='normal',h_align='left', fill=(1,1,1))
            right = gz.Group([txt]).translate((RIGHTCOL, ypos))
            right.draw(surface)
        return surface.get_npimage()

    clip = mpy.VideoClip(make_frame, duration=DURATION)

----

## 4. Assemble and export the clip

Combining both the image and the text to a single movie takes a single line of code - this worked well for me. Concatenating two clips is a bit worse, because it tends to fail gloriously if the clips have different sizes. It took me a while to find the parameters for exporting clips in high resolution, which is why I included both my `.avi` and `.mpg` solution.

    :::python
    final = CompositeVideoClip([clip, logo])

    final.subclip(0, DURATION).write_videofile("end_credits.avi", \
        codec="h264", fps=24) 
    final.subclip(0, DURATION).write_videofile("end_credits.mp4", \
        codec="mpeg4", fps=24) 

----

## 5. Caveats

Like many Python libraries, `moviepy` doesn't do all the work by itself. It delegates all the heavy calculations to the `ffmpeg` library. In order to get all codecs I wanted working, I had to compile `ffmpeg` from source three times. In the end, everything worked out fine, but it was not an entirely sunny walk. But at least you get credits for it ;-)

