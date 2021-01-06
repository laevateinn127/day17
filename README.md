# day17
#!/usr/bin/python 
# coding: utf-8 
# 引入Tkinter庫 
import tkinter as tk
# 操作事件繫結的函式，這些函式中都會對顯示的內容進行更新，因此顯示內容display作為全域性變數 
# 更新顯示內容函式，由按鈕事件觸發，將按鈕內容新增到已顯示內容後 
def updateDisplay(buttonString): 
 content = display.get() 
 if content == "0": 
  content = "" 
 display.set(content + buttonString) # 計算表示式的結果，表示式即為顯示的內容，並將結果顯示出來（需要換行並新增等於號） 
def calculate(): 
 result = eval(display.get()) 
 display.set(display.get() + '= ' + str(result)) # 清空操作，由清空按鈕事件觸發 
def clear(): 
 display.set('0') # 刪除操作，由刪除按鈕事件觸發，刪除前一個字元 
def backspace(): 
 display.set(str(display.get()[:-1])) # 定義主視窗，設定視窗名稱和大小200×320，並設定螢幕座標為(300,300) 
mainUI = tk.Tk() 
mainUI.title('Calculator') 
mainUI.geometry('200x210+300+300') # 設定顯示內容，預設顯示0 
# 這裏使用StringVar屬於Tkinter庫，在介面程式設計的時候，有時需要跟蹤變數值的變化， 
# 以保證值的變更隨時可以顯示在介面上。python無法直接做到，所以定義了一系列新的的物件， 
# 例如StringVar、BooleanVar、DoubleVar、IntVar。 
display = StringVar() 
display.set('0') 
# 新增計算器顯示區域，使用Label，並設定背景色及大小 textLabel = Label(mainUI) 
# 這裏需要注意width寬度的單位，如果你在Label中顯示文字， 
# 那麼這些選項將以文字的單位為定義按鈕的尺寸。 
# 如果你替而代之顯示圖象，那麼按鈕的尺寸將是畫素（或其它的螢幕單位）。 
textLabel.config(bg='grey', width=28, height=3, anchor = SE) 
textLabel['textvariable'] = display 
# 設定顯示區域在Grid佈局中的位置 
textLabel.grid(row=0, column=0, columnspan=4) 
# 新增按鈕並放置到適當的區域 
# 清空按鈕，其中text為按鈕上的文字，fg為按鈕的字型顏色（bg為文字背景的按鈕顏色），width為按鈕寬度 
# command引數為按鈕事件繫結函式，繫結到clear()函式，按鈕按下時觸發 
clearButton = Button(mainUI, text = 'C', fg = 'orange', width = 3, command = clear) 
# 設定清空按鈕的位置，行號為1，列號為0，即第二行第一列 
clearButton.grid(row = 1, column = 0) 
# 其他按鈕位置，由於與清空按鈕類似不再註釋，請自行檢視Grid中的位置，有的按鈕採用lambda來生成匿名函式，原因是需要處理傳入的引數 
Button(mainUI, text = 'DEL', width = 3, command = backspace).grid(row = 1, column = 1) 
Button(mainUI, text = '/', width = 3, command = lambda:updateDisplay('/')).grid(row = 1, column = 2) 
Button(mainUI, text = '*', width = 3, command = lambda:updateDisplay('*')).grid(row = 1, column = 3) 
Button(mainUI, text = '7', width = 3, command = lambda:updateDisplay('7')).grid(row = 2, column = 0) 
Button(mainUI, text = '8', width = 3, command = lambda:updateDisplay('8')).grid(row = 2, column = 1) 
Button(mainUI, text = '9', width = 3, command = lambda:updateDisplay('9')).grid(row = 2, column = 2) 
Button(mainUI, text = '-', width = 3, command = lambda:updateDisplay('-')).grid(row = 2, column = 3) 
Button(mainUI, text = '4', width = 3, command = lambda:updateDisplay('4')).grid(row = 3, column = 0) 
Button(mainUI, text = '5', width = 3, command = lambda:updateDisplay('5')).grid(row = 3, column = 1) 
Button(mainUI, text = '6', width = 3, command = lambda:updateDisplay('6')).grid(row = 3, column = 2) 
Button(mainUI, text = '+', width = 3, command = lambda:updateDisplay('+')).grid(row = 3, column = 3) 
Button(mainUI, text = '1', width = 3, command = lambda:updateDisplay('1')).grid(row = 4, column = 0) 
Button(mainUI, text = '2', width = 3, command = lambda:updateDisplay('2')).grid(row = 4, column = 1) 
Button(mainUI, text = '3', width = 3, command = lambda:updateDisplay('3')).grid(row = 4, column = 2) 
Button(mainUI, text = '=', width = 3, bg = 'orange', height = 3,command = lambda:calculate()).grid(row = 4, column = 3, rowspan = 2) 
Button(mainUI, text = '0', width = 10, command = lambda:updateDisplay('0')).grid(row = 5, column = 0, columnspan = 2) 
Button(mainUI, text = '.', width = 3, command = lambda:updateDisplay('.')).grid(row = 5, column = 2) 
# 進入主迴圈 
mainUI.mainloop() 







```
import tkinter as tk
 
def updateDisplay(buttonString): 
 content = display.get() 
 if content == "0": 
  content = "" 
 display.set(content + buttonString)  
def calculate(): 
 result = eval(display.get()) 
 display.set(display.get() + '= ' + str(result))  
def clear(): 
 display.set('0')
def backspace(): 
 display.set(str(display.get()[:-1]))
mainUI = tk.Tk() 
mainUI.title('Calculator') 
mainUI.geometry('200x210+300+300')
display = StringVar() 
display.set('0') 

textLabel.config(bg='grey', width=28, height=3, anchor = SE) 
textLabel['textvariable'] = display 

textLabel.grid(row=0, column=0, columnspan=4) 

clearButton = Button(mainUI, text = 'C', fg = 'orange', width = 3, command = clear) 

clearButton.grid(row = 1, column = 0) 
 
Button(mainUI, text = 'DEL', width = 3, command = backspace).grid(row = 1, column = 1) 
Button(mainUI, text = '/', width = 3, command = lambda:updateDisplay('/')).grid(row = 1, column = 2) 
Button(mainUI, text = '*', width = 3, command = lambda:updateDisplay('*')).grid(row = 1, column = 3) 
Button(mainUI, text = '7', width = 3, command = lambda:updateDisplay('7')).grid(row = 2, column = 0) 
Button(mainUI, text = '8', width = 3, command = lambda:updateDisplay('8')).grid(row = 2, column = 1) 
Button(mainUI, text = '9', width = 3, command = lambda:updateDisplay('9')).grid(row = 2, column = 2) 
Button(mainUI, text = '-', width = 3, command = lambda:updateDisplay('-')).grid(row = 2, column = 3) 
Button(mainUI, text = '4', width = 3, command = lambda:updateDisplay('4')).grid(row = 3, column = 0) 
Button(mainUI, text = '5', width = 3, command = lambda:updateDisplay('5')).grid(row = 3, column = 1) 
Button(mainUI, text = '6', width = 3, command = lambda:updateDisplay('6')).grid(row = 3, column = 2) 
Button(mainUI, text = '+', width = 3, command = lambda:updateDisplay('+')).grid(row = 3, column = 3) 
Button(mainUI, text = '1', width = 3, command = lambda:updateDisplay('1')).grid(row = 4, column = 0) 
Button(mainUI, text = '2', width = 3, command = lambda:updateDisplay('2')).grid(row = 4, column = 1) 
Button(mainUI, text = '3', width = 3, command = lambda:updateDisplay('3')).grid(row = 4, column = 2) 
Button(mainUI, text = '=', width = 3, bg = 'orange', height = 3,command = lambda:calculate()).grid(row = 4, column = 3, rowspan = 2) 
Button(mainUI, text = '0', width = 10, command = lambda:updateDisplay('0')).grid(row = 5, column = 0, columnspan = 2) 
Button(mainUI, text = '.', width = 3, command = lambda:updateDisplay('.')).grid(row = 5, column = 2) 
 
mainUI.mainloop()
#!/usr/bin/python 
# coding: utf-8 
# 引入Tkinter庫 
# 操作事件繫結的函式，這些函式中都會對顯示的內容進行更新，因此顯示內容display作為全域性變數 
# 更新顯示內容函式，由按鈕事件觸發，將按鈕內容新增到已顯示內容後
# 計算表示式的結果，表示式即為顯示的內容，並將結果顯示出來（需要換行並新增等於號）
# 清空操作，由清空按鈕事件觸發
 # 刪除操作，由刪除按鈕事件觸發，刪除前一個字元
# 定義主視窗，設定視窗名稱和大小200×320，並設定螢幕座標為(300,300)
  # 設定顯示內容，預設顯示0 
# 這裏使用StringVar屬於Tkinter庫，在介面程式設計的時候，有時需要跟蹤變數值的變化， 
# 以保證值的變更隨時可以顯示在介面上。python無法直接做到，所以定義了一系列新的的物件， 
# 例如StringVar、BooleanVar、DoubleVar、IntVar。
# 新增計算器顯示區域，使用Label，並設定背景色及大小 textLabel = Label(mainUI) 
# 這裏需要注意width寬度的單位，如果你在Label中顯示文字， 
# 那麼這些選項將以文字的單位為定義按鈕的尺寸。 
# 如果你替而代之顯示圖象，那麼按鈕的尺寸將是畫素（或其它的螢幕單位）。
# 設定顯示區域在Grid佈局中的位置
# 新增按鈕並放置到適當的區域 
# 清空按鈕，其中text為按鈕上的文字，fg為按鈕的字型顏色（bg為文字背景的按鈕顏色），width為按鈕寬度 
# command引數為按鈕事件繫結函式，繫結到clear()函式，按鈕按下時觸發
# 設定清空按鈕的位置，行號為1，列號為0，即第二行第一列
# 其他按鈕位置，由於與清空按鈕類似不再註釋，請自行檢視Grid中的位置，有的按鈕採用lambda來生成匿名函式，原因是需要處理傳入的引數
# 進入主迴圈
```
