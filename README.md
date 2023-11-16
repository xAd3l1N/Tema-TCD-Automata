# Tema-TCD-Automata
Mi-am facut un program ce-mi face o parte din tema de la o anumita materie.

from pyautogui import *
import pyautogui
import time
import keyboard
import random
import win32api, win32con

time.sleep(1)

#functie pentru a deschide un nou fisier sheet
def openSheet():
    os.startfile("https://docs.google.com/spreadsheets/u/0/")
        
    time.sleep(2)

    #localizam butonul de creare sheet nou
    x, y = pyautogui.locateCenterOnScreen('tinta.png', confidence=0.8)

    time.sleep(1)

    #creare sheet nou
    pyautogui.click(x, y)

def findAndClick(target):

    print(target)
    x, y = pyautogui.locateCenterOnScreen(target, confidence=0.8)
    
    time.sleep(1)

    pyautogui.click(x, y)
    

#functia ce rezolva problema
def program():
    
        openSheet()
        
        Lines = open('date.txt', 'r').readlines()
        #print(Lines)

        time.sleep(2)

        nrSectiuni = int(Lines[0])
        
        #print("nrSectiuni: ",nrSectiuni)
        
        for _ in range(nrSectiuni):
            pyautogui.typewrite(str(_+1))
            time.sleep(0.01)
            pyautogui.press('down')
            
        for _ in range(nrSectiuni):
            pyautogui.press('up')
            
        pyautogui.press('right')
        
        unit = Lines[1]
        #print(unit)

        es,ei = Lines[2].split()
        #print(es,ei)

        nrVal = len(list(Lines[3].split()))
        #print("nrVal: ",nrVal)
        
        for i in range(3,len(Lines)):
            
            valori = list(Lines[i].split())
            #print(valori)
            
            for j in valori:
                j = int(j)
                j /= 2
                time.sleep(0.01)
                pyautogui.typewrite(str(j).replace(".",","))
                time.sleep(0.01)
                pyautogui.press('down')
            for j in valori:
                pyautogui.press('up')
            pyautogui.press('right')

        pyautogui.press('left')
        time.sleep(0.01)
        pyautogui.keyDown('shift')
        for _ in range(nrVal-1):# -1 because range starts from 0
            #print(_," ",end="")
            time.sleep(0.01)
            pyautogui.press('down')
        #print("")
        for _ in range(int(nrSectiuni)): # not -1 because of graph names
            #print(_," ",end="")
            time.sleep(0.01)
            pyautogui.press('left')
        pyautogui.keyUp('shift')

        findAndClick("insereaza.png")

        for _ in range(5):
            #print(_)
            pyautogui.press('down')
        pyautogui.press('enter')
            
        time.sleep(1.5)

        findAndClick("click2.png")

        time.sleep(1.5)

        findAndClick("click3.png")

        time.sleep(1.5)

        findAndClick("click4.png")

        time.sleep(1.5)

        findAndClick("click5.png")

program()
