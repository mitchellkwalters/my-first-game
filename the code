

from random import *
from tkinter import *
spawnrate1 = 80
spawnrate2 = 90
spawnrate3 = 99
battlefield = [ 0 for i in range (40)]


class Enemy():
    def __init__(self):
        health_check = randint(0,100)
        if health_check < spawnrate1:
            self.health = 1
        elif health_check < spawnrate2:
            self.health = 2
        elif health_check < spawnrate3:
            self.health = 3
        else:
            self.health = 4
        self.position = 0
    def move(self):
        battlefield.insert((self.position + 5), battlefield.pop(self.position))
        self.position = self.position + 5


class Defender():
    def __init__(self):
        self.kill_count = 0
    def column_strike(self,column):
        for i in range (8):
            if battlefield[(i*5) + int(column)] != 0:
                battlefield[ (i*5) + int(column)].health -= 1
                if  battlefield[ (i*5) + int(column)].health == 0:
                    battlefield[ (i*5) + int(column)] = 0
                    self.kill_count +=1
        move_team()
        spawn()
        for item in range(8):
            column_count = 0 + item
            for i in range(5):
                if battlefield[i+(column_count *5) ] != 0:
                    label = Label(text = battlefield[i+(column_count *5)].health)
                    label.grid(column = i, row = item)
                else:
                    label = Label(text = '_')
                    label.grid(column = i, row = item)
        print('I just attacked')

def get_battlefield():
    battlefield_display = []
    print ('___________________')
    print ('___________________')
    print ('___________________')
    for i in range(len(battlefield)):
        if battlefield[i] == 0:
            battlefield_display.append(0)
        else:
            battlefield_display.append(battlefield[i].health)
    lower = 0
    upper = 5
    for i in range(8):
        print (battlefield_display[lower:upper])
        lower += 5
        upper +=5

def spawn():
    for i in range (5):
        spawn_check = randint(0,100)
        if spawn_check < 20:
            battlefield[i] = Enemy()
            battlefield[i].position = i
    ###makes sure at least one enemy is spawned
    if battlefield[:5] == [0,0,0,0,0]:
            spawn()

def move_team():
    for i in reversed(battlefield):
        if i != 0:
            i.move()

def get_move():
    move = input('Which column shall I strike?')
    mitchell.column_strike((int(move)-1))

mitchell = Defender()

def check_lose_condition():
    for i in range(5):
        if battlefield[i+35] != 0:
            get_battlefield()
            print ('The castle has been lost.')
            print ('You have slain ' + str(mitchell.kill_count) + ' enemies.')
            break


def column_strike_0():
    mitchell.column_strike(0)
def column_strike_1():
    mitchell.column_strike(1)
def column_strike_2():
    mitchell.column_strike(2)
def column_strike_3():
    mitchell.column_strike(3)
def column_strike_4():
    mitchell.column_strike(4)

root = Tk()
root.title('The Defense of Valaria')
root.geometry("250x250")


for item in range(8):
            column_count = 0 + item
            for i in range(5):
                if battlefield[i+(column_count *5) ] != 0:
                    label = Label(text = battlefield[i+(column_count *5)].health)
                    label.grid(column = i, row = item)
                else:
                    label = Label(text = '_')
                    label.grid(column = i, row = item)
button1 = Button(root, text = 'x', command = column_strike_0)
button1.grid(column = 0, row = 9)

button2 = Button(root, text = 'x', command = column_strike_1)
button2.grid(column = 1, row = 9)

button3 = Button(root, text = 'x', command = column_strike_2)
button3.grid(column = 2, row = 9)

button4 = Button(root, text = 'x', command = column_strike_3)
button4.grid(column = 3, row = 9)

button5 = Button(root, text = 'x', command = column_strike_4)
button5.grid(column = 4, row = 9)


spawn()
get_battlefield()
root.mainloop()
