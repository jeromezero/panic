this is a test

<!-- lets make a comment -->
some more fucking shit
and carry on  with some other shit over here

and then another comment
motherfucker this is a whole  
(<!--.+)[\w]+( -->)

\b(?<!<!-- )[\w']+(?! -->)\b

(?:start:(?=\w+(?:-\w+){2,9}:end)|(?<=-)\G)(\w+)(?:-|:end)

(?:<!-- (?=\w+(?:-\w+){2,9}: -->)|(?<=-)\G)(\w+)(?:-| -->)

match comments only (in php, not python. python doesn't have the \G 'start of match' token):

    (?:<!-- (?=\w+(?: \w+){2,} -->)|(?<= )\G)(\w+)(?: | -->)

this next one matches two separate groups - the first returns comments, the second returns words that are not in comments. Kind of works, but not for the custom regex features of the sublime wordcount app, for whatever reason. Well, I assume it has to do with the groups. though, with only one group returning results, you'd think those would be little golden children ... you'd think (I thought) that would be clear enough, but it doesn't work that way. Words are counted just the same, whether they are inside comments or out. 

    (?!<!--[^\>]*\>)|(\b\w+\b)

Now I am having a distracting thought. The twice above regex snippet returns precisely words that are in the comments, not words that are without. What if I inverted the comment selectors and made an either/or addendum, so that the search would return words between either the beginning of the file OR the end of a comment and the start of a comment OR the end of the file? that might do it.

Goddamned rabbit hole. 

This is surely not the ideal way to handle the problem at hand, I'm not much of a coder, but I can see a kind of madness buried in these regex puzzles ....

Such a trap. Every time I get anywhere with this problem, and feel like I am starting to understand the issue, and am seeing a path through, I bang my head against the zero-width assertion of the positive lookbehind.