## Directories and file creation




1. Open your terminal by typing ctrl+Alt+t
2. Lets create a directory in which our tutorial will be held. 

        mkdir letsPractice
        
3. Great job for your first trial! Now we want to create 4 subdirectories in letsPractice (previously created).
 - There is many ways to do this step ;
 
        mkdir letsPractice/dir1 letsPractice/Dir1
        
**Notice** that linux is a case sensitive that way dir1 is considered different to Dir1.

 - Change your location to letsPractice directory == enter to this directory ;
 
        cd letsPractice 
        
 - then ;
 
        mkdir Directory3 dir5
    
4. *kudos*  your 4 directoris  were created successefully.  if you want to check and **print out** just type ;

        ls 
        
5. Oups! it looks messy and not well organized. Just let us change some names ; 

        mv dir1 Dir2	
        
   - Instead of typing and executing every single command one by one we merely used "**&&**" symbol to run both commands simultaneously. 
      
        mv dir5 Dir3 && mv Directory3 Dir4


6. Please check again using the command **list** to print out your directories. 

7. Move to Dir1 then type; 

        touch my_1st_file 
        
 - then type this command and write this citation in your first file 
 " Success isn’t about the end result, it’s about what you learn along the way. " ;
 
        open my_1st_file 
        
 **here** you just created your first file then you opened it via a text editor. Linux give you many choises in text editing, other than creating a file then write in it, simply you can create and read and write directly *via your terminal*. 
 
 8. One of the most popular text editors like Vim and gedit is *nano*; 
 
        nano file2.txt 
        
  - When you press enter, You'll be in nano's window where you can write or just paste those lines; 
  
        Without continual growth and progress, such words as improvement, achievement, and success have no meaning.
        
  - press ctrl+x then save and exit 

**Congratulations for your first tutorial.**
 * By the end of this tutorial you'll have an organisation looks to this one:

```bash
letsPractice/
├── Dir1
│   ├── file2.txt
│   └── my_testFile
├── Dir2
├── Dir3
└── Dir4
```

