import tkinter
import webbrowser
import random
__author__ = "thrax"
# mama mia fucking spaghetti code

class Gui:
    def __init__(self):
        self.range = "0123456789abcdefghijklmnopqrstuvwxyz"
        self.bg_col = "#111111"
        self.fg_col = "#DDDDDD"
        self.root = tkinter.Tk()
        self.root.configure(bg=self.bg_col)
        self.root.title("LightHopper")
        self.root.minsize(300, 50)
        self.inner = tkinter.Frame(self.root, pady=10, bg=self.bg_col)
        self.welcome = tkinter.Label(self.inner, text="Source URL: ", bg=self.bg_col, fg=self.fg_col)
        self.initial = tkinter.Entry(self.inner, bg=self.bg_col, fg=self.fg_col)
        self.current_url = tkinter.StringVar("")

        self.lower = tkinter.Frame(self.root, pady=30, bg=self.bg_col)
        self.gen_button = tkinter.Button(self.lower, text="Begin", command=lambda: self.begin(self.initial.get()),
                                         bg=self.bg_col, fg=self.fg_col)

        self.inner.pack()
        self.lower.pack()
        self.welcome.grid(row=0, column=0)
        self.initial.grid(row=0, column=1)
        self.gen_button.grid(row=1, column=1)

        #BUTTONS
        self.previous_button = tkinter.Button(self.lower, text="<< Previous",
                                              command=self.previous, bg=self.bg_col, fg=self.fg_col, width=20)
        self.next_button = tkinter.Button(self.lower, text="Next >>",
                                          command=self.next, bg=self.bg_col, fg=self.fg_col, width=20)
        self.open_button = tkinter.Button(self.lower, text="Open Browser", command=self.open_browser,
                                          bg=self.bg_col, fg=self.fg_col, width=20)
        self.rand_button = tkinter.Button(self.lower, text="Random", command=self.random,
                                          bg=self.bg_col, fg=self.fg_col, width=20)

        #LABELS
        self.current_label = tkinter.Label(self.lower, text="Current URL:",
                                           bg=self.bg_col, fg=self.fg_col)
        self.current_url_label = tkinter.Label(self.lower, textvariable=self.current_url,
                                               bg=self.bg_col, fg=self.fg_col)

    def open_browser(self):
        webbrowser.open_new_tab(self.current_url.get())

    def begin(self, current):
        print("Debug", current)
        self.current_url.set(current)
        self.current_url_label = tkinter.Label(self.lower, textvariable=self.current_url,
                                               bg=self.bg_col, fg=self.fg_col)
        self.gen_button.destroy()
        self.previous_button.grid(row=1, column=0)
        self.next_button.grid(row=1, column=1)
        self.open_button.grid(row=2, column=0)
        self.rand_button.grid(row=2, column=1)
        self.current_label.grid(row=0, column=0)
        self.current_url_label.grid(row=0, column=1)

    def random(self):
        url = self.current_url.get()[0:len(self.current_url.get())-6]
        new_id = ""
        for s in random.sample(self.range, 6):
            new_id += s
        self.current_url.set(url+new_id)
        print(self.current_url.get())

    def previous(self):
        final = self.current_url.get()[len(self.current_url.get()) - 1]
        index = self.range.index(final) - 1
        if index < 0:
            index = len(self.range) - 1
        new_url = self.current_url.get()[0:len(self.current_url.get()) - 1] + self.range[index]
        self.current_url.set(new_url)

    def next(self):
        final = self.current_url.get()[len(self.current_url.get()) - 1]
        index = self.range.index(final) + 1
        if index >= len(self.range):
            index = 0
        new_url = self.current_url.get()[0:len(self.current_url.get()) - 1] + self.range[index]
        self.current_url.set(new_url)


mainGui = Gui()
mainGui.root.mainloop()
