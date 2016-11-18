
# Drawing Dice with Pillow

During a break today, I needed to create images for writing a dice game during a C++ course. The tools of choice were **Python** and **Pillow**. This is the outcome:

![Dice](images/pillow_dice.png)

The Python code is somewhat crude, but it demonstrates that you can write useful programs without using *any* indentation or other sophisticated program constructs.

    :::python
    from PIL import Image
    from PIL import ImageDraw
    
    w = Image.new('RGB', (64,64), '#80b940')    
    d = ImageDraw.Draw(w)
    
    d.ellipse(((26, 26), (38, 38)), '#ffffff')
    one = w.copy()
    
    d.ellipse(((10, 10), (22, 22)), '#ffffff')
    d.ellipse(((42, 42), (54, 54)), '#ffffff')
    three = w.copy()
    
    d.ellipse(((10, 42), (22, 54)), '#ffffff')
    d.ellipse(((42, 10), (54, 22)), '#ffffff')
    five = w.copy()
    
    d.ellipse(((26, 26), (38, 38)), '#80b940')
    four = w.copy()
    
    d.ellipse(((10, 42), (22, 54)), '#80b940')
    d.ellipse(((42, 10), (54, 22)), '#80b940')
    two = w.copy()
    
    d.ellipse(((10, 42), (22, 54)), '#ffffff')
    d.ellipse(((42, 10), (54, 22)), '#ffffff')
    d.ellipse(((26, 10), (38, 22)), '#ffffff')
    d.ellipse(((26, 42), (38, 54)), '#ffffff')
    six = w.copy()
    
    dice = Image.new('RGB', (64*6,64), '#80b940')
    dice.paste(one, box=(64 * 0, 0))
    dice.paste(two, box=(64 * 1, 0))
    dice.paste(three, box=(64 * 2, 0))
    dice.paste(four, box=(64 * 3, 0))
    dice.paste(five, box=(64 * 4, 0))
    dice.paste(six, box=(64 * 5, 0))
    dice.save('pillow_dice.png')


If you want to try the code yourself, you need to install **Pillow** first:

    pip install pillow

Read more about Pillow on [https://python-pillow.org/](https://python-pillow.org/).