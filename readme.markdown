#Monokai-Sublime-Text-Octopress

## Sublime Text Style Highlighting for PHP and JavaScript Coders Running Octopress
##### Based on bdryanovski's original patch [here](https://github.com/bdryanovski/Octopress---Monokai).

---------------

Back in January, bdryanovski created a patch for the solarized syntax highlighting that octopress uses as a front end to its pygments based syntax highlighter. 

The patch worked great, except that it looked much different (for PHP and JavaScript) than I was used to from Sublime Text's interpretation of the Monokai theme. 

So - I made a few adjustments. 

##Languages and Consistency
Most of the code I write is either JavaScript or PHP, although I do poke at projects written in C or Python with sticks of varying lengths from time to time. 

So - this patch is optimized for PHP and JavaScript - even then, the theme isn't perfect due to some differences between sublime text and pygments. 

For example - in PHP, while Sublime Text differentiates between the keywords "class" and "public" (giving the former a color of light blue and the latter a color of bright red), pygments does not - assigning a single css class of ".k" (for keyword presumably) to both. 

Then there were conflicts between languages. Pygments sometimes assigns the same class for different features in different languges. For example - both non-stdlib functions in PHP and Object properties in JavaScript share the same class (.nx). I actually probably should have favored JavaScript in this case - as I certainly use JavaScript object properties more regularly than PHP functions that don't belong to any class or the stdlib, but I optimized for PHP first and am too lazy to go back and regenerate diff files for patches. Feel free to knock yourself out. 

Finally - there are some places where Sublime Text seems to fall short. Pygments gets it right (in my opinion) for C highlighting. For some reason, Sublime Text treats the dereference, conditional and arithmetic operators as punctuation (coloring them white) while pygments appropriately assigns the .o css class (bright red)... 

In any case, all 4 of the languages I tested turned out pretty well. I wasn't going for perfection (luckily), just something that somewhat resembles my typical dev environment. You can see screenshots below that illustrate the shortcoming described above. If your particular flavor of programming isn't well supported - you might try [bdryanovski's original monokai patch](https://github.com/bdryanovski/Octopress---Monokai).

##Tests
![JavaScript](http://i.imgur.com/PtBUU.png)

![PHP](http://i.imgur.com/cO7iO.png)

![C](http://i.imgur.com/qCfIl.png)

![Python](http://i.imgur.com/07szc.png)


##Apply the Patch 

Go to your home directory: 
```
$ cd $HOME
```

Clone into the repo
```
$ git clone https://sanukcode@github.com/sanukcode/Monokai-Sublime-Text-Octopress.git
```

Go to wherever you installed octopress (note - the patch works on unmodified, fresh installations. No promises if you have tweaked any of the files we are patching...)
```
$ cd /path/to/octopress/
```

Patch the appropriate files:
```
  $ patch -u sass/base/_solarized.scss  $HOME/Monokai-Sublime-Text-Octopress/_solarized.scss.patch
```
```
$ patch -u sass/custom/_colors.scss   $HOME/Monokai-Sublime-Text-Octopress/_colors.scss.patch
```
```
$ patch -u sass/partials/_syntax.scss $HOME/Monokai-Sublime-Text-Octopress/_syntax.scss.patch
```

If you re-generate your site, you should see the new highlighting in action!



