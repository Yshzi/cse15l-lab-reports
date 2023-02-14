# Lab Report 3: Researching Commands
## Grep
Grep is a function in bash that stands for global regular expression print. 
Basically, what it does is it takes a string and file path and finds lines that 
contain the string in the file path and prints it. Modifiers can be combined with other modifiers to have a combined effect.
The following commands will be from the working directory written_2/
### grep -r (string) (filepath)[^2]
This command allows us to recursively use grep which now allows grep to be used 
on directories as well as files.
#### Command:
```
grep -r "creating" non-fiction/OUP/Fletcher/
```
#### Output:
```
non-fiction/OUP/Fletcher//ch1.txt:To understand the phenomenon of communal redemption, we must turn to the Bible as our source. The model of the Hebrews’ deliverance from servitude and their ensuing acceptance of God’s law at Mount Sinai have repeatedly appealed to dominant powers of the West and often to opposite sides of the same conflict. In the rhetoric of the abolitionists, slavery in the United States made the country into “a House of Bondage.” Both blacks and whites identified with the same story of liberation from this domain of oppression. Nat Turner thought he was recreating the biblical story when he led a slave revolt in 1831. The slaves whom Harriet Tubman led to freedom in the North called her Moses. Abraham Lincoln readily saw himself in the image of Moses leading his people out of bondage into the realm of freedom.
non-fiction/OUP/Fletcher//ch5.txt:There is much to be said about the proper reading of this passage, particularly in relation to the contrary story of creation in Genesis 2, a story that supposedly justifies the subordination of women. The proper reading of the text, as I have argued elsewhere,25 has God creating a single being, both male and female. God gives this being, called Adam, dominion over all the animals but not over the first woman, yet to be created. Only in the later story of the Garden of Eden do we encounter the curse and subordination of Eve. For those who look to the Bible for guidance, therefore, it makes a tremendous difference whether one relies primarily on the egalitarian message in chapter 1, of ultimate human dignity for all, or on chapter 2, with its story leading to the curse of women that they be “ruled by their husbands.”
non-fiction/OUP/Fletcher//ch6.txt:The ancient Israelites would spend forty years wandering in the desert before the passing of time would generate a new people, unaffected by the mentality of the “fleshpots of Egypt.” Modern political conditions rarely offer this luxury. The Soviets dreamed of creating a “new man” who would regard the communist system as the natural backdrop for cooperation. History never gave them the chance. But Germans could engineer a radical transformation after the fall of the Berlin Wall and the unification of the country. The West Germans absorbed the former German Democratic Republic and then restaffed the courts and the law faculties with new personnel, drawn overwhelmingly from Western ranks.
```
Usually when grep is used on a directory it gives a message saying that the 
filepath is a directory and therefore the string cannot be searched for. 
This command is useful as we can combine it with other commands and have access 
to multiple files in different directories so long as they have the same parent 
directory.
#### Command:
```
grep -r "creating"  non-fiction/OUP/Fletcher/ch6.txt
```
#### Output:
```
non-fiction/OUP/Fletcher/ch6.txt:The ancient Israelites would spend forty years wandering in the desert before the passing of time would generate a new people, unaffected by the mentality of the “fleshpots of Egypt.” Modern political conditions rarely offer this luxury. The Soviets dreamed of creating a “new man” who would regard the communist system as the natural backdrop for cooperation. History never gave them the chance. But Germans could engineer a radical transformation after the fall of the Berlin Wall and the unification of the country. The West Germans absorbed the former German Democratic Republic and then restaffed the courts and the law faculties with new personnel, drawn overwhelmingly from Western ranks.
```
Here, since we gave a filepath to a file it only searches that one file because there's no other directory for it to go to.
###  grep -c (string) (filepath)[^1]
This method of using grep gives the number of times a string occcurs in a certain filepath.
#### Command:
``` 
grep -c "Finally" non-fiction/OUP/Rybczynski/*.txt
```
#### Output:
```
non-fiction/OUP/Rybczynski/ch1.txt:0
non-fiction/OUP/Rybczynski/ch2.txt:0
non-fiction/OUP/Rybczynski/ch3.txt:1
```
This output tells us that the word "Finally" was found once in 
non-fiction/OUP/Rybczynski/ch3.txt and 0 times in 
non-fiction/OUP/Rybczynski/ch1.txt and non-fiction/OUP/Rybczynski/ch2.txt. 
This is useful because if we were simply looking for how many times a word 
occurs in the file we have an amount. 
#### Command:
``` 
grep -c  "Finally" non-fiction/OUP/Rybczynski/
```
#### Output:
```
grep: non-fiction/OUP/Rybczynski/: Is a directory
```
When grep -c is used on a directory it is unable to search for the string and 
thus gives a message to the user. If we combined the recursive modifier and 
used grep -rc we would be able to look through the directory and have the 
same output as grep -c "Finally" non-fiction/OUP/Rybczynski/*.txt.
### grep -n (string) (filepath)[^1]
The -n modifier for grep makes it so the line number that the string was matched to is printed as well as the contents of that line.
#### Command:
```
grep -n "kilos" travel_guides/berlitz1/WhatToIndia.txt 
```
#### Output:
```
280:        couple of kilos, they’ll ship it for you in air-tight packages.
```
The line is being printed as well as its line number. This command can be useful when we want to know specifically where something is in a file and thus we can reference the line that it is at to get more context.
#### Command:
```
grep -nr "kilos" travel_guides/berlitz1/
```
#### Output:
```
travel_guides/berlitz1//WhereToIndia.txt:901:        separate lots of five kilos each: “three, three, three,” “four, four,
travel_guides/berlitz1//WhatToIndia.txt:280:        couple of kilos, they’ll ship it for you in air-tight packages.
```
Here, we used -nr because we used the filepath of a directory and thus with only -n we would get a message saying that the path is a directory. However, by also using the recursive modifier -r we were able to look into the directory and see that another line, 901 was printed in WhereToIndia.txt. This is interesting as grep did not see this before with the direct file path and only -n but now it found another line with "kilos" in it. By using -r perhaps we can search more deeply for a certain string in the desired filepath.
### grep -i (string) (filepath)[^1]
The -i modifier stands for ignore case so the any lines that contain the string will be printed whether or not the letters are capitalized or not.
## Conclusion
Grep has many useful modifiers that can exapand its already useful default capabilities. By learning more about the different modifiers that we can attach to commands, the better we can use them to our advantage. There are modifiers for almost every command so we just have to learn them and use them. Some useful resources to learn more about commands and their modifiers is man then the command. The command man stands for manual and will output a manual that details modifiers and what a certain command is used for. Additionally there is a lot of documentation online that can help one to understand how a function works. Happy coding!
[^1]: https://qpeng.org/computer/grep.htm
[^2]: https://linuxhandbook.com/grep-search-all-files-directories/#:~:text=You%20can%20make%20grep%20search,grep%20%2Dr%20search_term%20.


