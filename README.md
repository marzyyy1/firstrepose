# firstrepose
from _typeshed import Self
from tkinter import*
import math
import tkinter.messagebox 

root = Tk()
root.title("Scientific Calculator")
root.resizable(width=False, height = False)
root.geometry("400x492+460+40")


Mainframe = Frame(root, bd=20, pady=2, relief =RIDGE)
calFrame = Frame(root, bd=20, pady=2, relief =RIDGE)
calFrame.grid()

class calc():
    def _init_(first):
       first.sum = 0
       first.current = ""
       first.input_value = True
       first.check_total = False
       first.op = ""
       first.result = False

    def inputnumber (first,num):
        first.result = False
        intialnum = txtResult.get()
        secondnum = str(num)
        if first.input_value:
            first.current = secondnum
            first.input_value = False
        else:
            if secondnum == '.':
                if secondnum in intialnum:
                    return
            first.current = intialnum + secondnum
        first.display(first.current)

def display(first,value):
    txtResult.delete(0,END)
    txtResult.insert(0,value)

def valid_function(first):
    if first.op == "add":
        first.total += first.current
    if first.op == "sub":
        first.total -= first.current
    if first.op == "multi":
        first.total *= first.current
    if first.op == "divide":
        first.total /= first.current
    first.input_value = True
    first.check_sum = False
    first.display (first.total)

def operation(first,op):
    first.current = float(first, op)
    if first.check_sum:
        first.valid_function()
    elif not first.result:
        first.total = first.current
        first.input_value = True
    first.check_sum = True
    first.op = op
    first.result = False

def sum(first):
    first.result = False
    first.current = -(float(txtResult.get()))


added_value = calc()

txtResult = Entry(calFrame, font = ("arial",16,"bold"),bg="darkgreen", bd=30, width=26, justify=RIGHT)
txtResult.grid(row=0, column=0, columnspan= 4, pady=1)
txtResult.insert(0, "0")

numbericButton = "789456123"
i = 0
btn = []
for j in range(2,5):
    for q in range(3):
        btn.append(Button(calFrame, width=6, height=2, font=("arial",16,"bold"),bd=4,
        text=numbericButton[i]))
        btn[i].grid(row =j, column=q, pady=1)
        btn[i]["command"] = lambda X = numbericButton[i]:added_value.inputnumber
        i+= 1

btn0=Button(calFrame, text="0", width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey").grid(row = 5, column=0, pady=1)

btnDiv=Button(calFrame, text="/", width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey")
COMMAND = lambda: added_value.operation("div").grid(row = 5, column=3, pady=1)

btnMult=Button(calFrame, text="*", width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey")
COMMAND = lambda: added_value.operation("mult").grid(row = 4, column=3, pady=1)

btnSub=Button(calFrame, text="-", width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey")
COMMAND = lambda: added_value.operation("sub").grid(row = 3, column=3, pady=1)


btnAdd=Button(calFrame, text="+", width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey")
COMMAND = lambda: added_value.operation("add").grid(row = 2, column=3, pady=1)
           

btnPM=Button(calFrame, text=chr(177), width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey").grid(row = 1, column=3, pady=1)

btnBack=Button(calFrame, width = 6,height=2, font=("arial",16,"bold",),bd=4, text="<=" ,
bg="grey").grid(row = 1, column=0, pady=1)

btnClearEntry=Button(calFrame, text=chr(67) + chr(69), width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey").grid(row = 1, column=1, pady=1)

btnClear=Button(calFrame, text=chr(67), width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey").grid(row = 1, column=2, pady=1)

btnEquals=Button(calFrame, text=chr(61), width = 6,height=2, font=("arial",16,"bold",),bd=4, 
bg="grey").grid(row = 5, column =5)
