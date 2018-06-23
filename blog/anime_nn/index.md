# Lazily building a smug anime face neural network for kicks

<p align="center">
    <img src="image1.jpg" alt="Image of Nightmare Incarnate" />
</p>

> And if you gaze long into an abyss, the abyss also gazes into you.
> \- Friedrich Nietzsche

Summer vacation is a time to kickback, relax, and finally pursue passions now that school is finally over (at least for three months). Some people use the time to kayak, bike, or travel, but unfortunately for me I don't like getting wet, my bike is broken, and I don't have enough money to travel. I decided to spend the time working on some deep learning stuff to kill time.

A while back, in the happier, simpler times of 2017, I watched a Youtube video where some dude wanted to train a [neural network to create jazz](https://www.youtube.com/watch?v=nA3YOFUCn4U). I can't recall the exact details, but basically he converted musical scores into image "heatmaps," and used these pictures as training data. The neural network then spit out a generated heatmap, which he turned back into MIDI. Now, I'm not entirely sure if using images was the best method [(maybe this?)](http://web.mit.edu/music21/), but the idea of training a neural network to generate custom images interested me.

Back to the present day. I chose anime smug faces because I like my cartoons.

In the summer heat, I didn't really feel like writing code, so I wanted to see if I could extend someone else's solution to just generate my cool pics. Fortunately, there are tons of open source projects out there implementing DCGAN, and I ultimately decided [this one](https://github.com/carpedm20/DCGAN-tensorflow) because it had custom dataset already built in.

Now I just needed to collect my data, but where? Fortunately, there are a lot of weeaboos out there, and I managed to find [archives](https://github.com/Wigsinator/smugFaces) that people curate. I could always get more, though, and I found that there was a [subreddit dedicated entirely to smug](https://www.reddit.com/r/Smugs/). Downloading every image using ripme netted about 2k images. However, the problem with reddit (and internet communities in general) is that there are a *ton* of reposts and duplicated content. I needed a way to cut the fat.

Fortunately, fdupes came to the rescue! fdupes is a program by Adrián López that compares files in a directory and deletes duplicates. The process was basically strip all the metadata using exiftool, then delete the duplicates. That's it.

This isn't a perfect solution, as some duplicate images aren't pixel perfect (JPEG artifacts, taking a picture of a may-may on your phone, etc.) but it managed to shrink my image set down to about 1200.

Unfortunately, my data gathering journey ended around here. I had a hard time finding any more original smug faces on the web, and I wasn't really willing to watch a ton of television just to get reaction images. This left me with an abysmally small sample size. For reference, the [NMIST dataset](http://yann.lecun.com/exdb/mnist/) contains around 70k images. I only have about 1k.

Now all I had to do was slap it into the neural network and train it.

TO BE CONTINUED?
