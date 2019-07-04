# MyMP3Player
import pygame
import tkinter as tkr
import os
from tkinter import *
from mutagen.id3 import ID3



#window creation

player=tkr.Tk() 

#edit window
player.title ("Music Player")
player.geometry("250x350")

#playlist
os.chdir("C:/songs")
songlist=os.listdir()

listbox=Listbox(player,height=20,width=40)

#space for songs
playlist=tkr.Listbox(player,highlightcolor="blue",selectmode=tkr.SINGLE)
print(songlist)
for item in songlist:
    pos=0
    listbox.insert(pos,item)
    
    pos+=1





pygame.init()
pygame.mixer.init()


#event
def Play():
   
    pygame.mixer.music.load(listbox.get(tkr.ACTIVE))
    var.set(playlist.get(tkr.ACTIVE))
    pygame.mixer.music.play()
    pygame.mixer.music.set_volume(w.get())
    print(pygame.mixer.music.get_volume())
    print(w.get())
    
def ExitPlayer():
    pygame.mixer.music.stop()

def Pause():
    pygame.mixer.music.pause()

def Unpause():
    pygame.mixer.music.unpause()

def Next_song():
    global pos
    pos+=1
    pygame.mixer.music.load(songlist[pos])
    pygame.mixer.music.play()

def Previous_song():
    global pos
    pos-=1
    pygame.mixer.music.load(songlist[pos])
    pygame.mixer.music.play()
    
    

    


    
label=Label(player,text='Music Player')

    

button1=tkr.Button(player,activebackground="green",bg="pink",text="PLAY",command= Play)

button2= tkr.Button(player,activebackground="red",text="STOP",bg="blue",command=ExitPlayer)

button3=tkr.Button(player,activebackground="yellow",text="PAUSE",bg="purple",command=Pause)

button4= tkr.Button(player,activebackground="green",text="UNPAUSE",bg="pink",command=Unpause)

nextbutton=tkr.Button(player,bg="green",text='Next',command=Next_song)

previousbutton=tkr.Button(player,bg="yellow",text='Previous',command=Previous_song)
w = tkr.Scale(player, from_=0, to=1,resolution=0.1,orient="horizontal")
place = tkr.Scale(player,orient="horizontal") 


#song name
var=tkr.StringVar()
songtitle=tkr.Label(player,textvariable=var)



#place widgets
label.pack()
listbox.pack()
button1.pack(fill='x')
button2.pack(fill='x')
button3.pack(fill='x')
button4.pack(fill='x')
nextbutton.pack(fill='x')
previousbutton.pack(fill='x')
w.pack(fill='x')
place.pack(fill='x')
songtitle.pack()

player.mainloop()

