# Weather-API

from tkinter import *
from tkinter import ttk
import requests

def data_get():
    city = city_name.get()
    data = requests.get("https://api.openweathermap.org/data/2.5/weather?q="+city+"&appid=ada516de7408b967ed3882bc30df6f14").json()
    w_lable1.config(text=data["weather"][0]["main"])
    wb_lable1.config(text=data["weather"][0]["description"])
    temp_lable1.config(text=str(int(data["main"]["temp"]-273.15)))
    pressure_lable1.config(text=data["main"]["pressure"])


win = Tk()
win.title("Mishra PRYJ")
win.config(bg= "blue")
win.geometry("500x570")


name_lable = Label(win,text ="Mishra Weather App",font = ("This new Roman",30,"bold"))
name_lable.place(x=25,y=50,height=50,width=450)

list_name = ["Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh", "Goa", "Gujarat",
             "Himachal Pradesh", "Jammu and Kashmir", "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh",
             "Maharashtra", "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha", "Punjab", "Rajasthan", "Sikkim",
             "Tamil Nadu", "Telangana", "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
             "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli", "Daman and Diu", "Lakshadweep",
             "National Capital Territory of Delhi", "Puducherry"]
city_name = StringVar()
com = ttk.Combobox(win,text ="Mishra Weather App",values = list_name,font = ("This new Roman",20,"bold"),textvariable=city_name)
com.place(x=25,y=120,height=50,width=450)

w_lable = Label(win,text ="Weather Climate",font = ("This new Roman",20))
w_lable.place(x=25,y=260,height=50,width=210)
w_lable1 = Label(win,text ="",font = ("This new Roman",20))
w_lable1.place(x=250,y=260,height=50,width=210)

wb_lable = Label(win,text ="Weather Description",font = ("This new Roman",17))
wb_lable.place(x=25,y=330,height=50,width=210)
wb_lable1 = Label(win,text ="",font = ("This new Roman",17))
wb_lable1.place(x=250,y=330,height=50,width=210)

temp_lable = Label(win,text ="Temprature",font = ("This new Roman",20))
temp_lable.place(x=25,y=400,height=50,width=210)
temp_lable1 = Label(win,text ="",font = ("This new Roman",20))
temp_lable1.place(x=250,y=400,height=50,width=210)


pressure_lable = Label(win,text ="Pressure",font = ("This new Roman",20))
pressure_lable.place(x=25,y=470,height=50,width=210)
pressure_lable1 = Label(win,text ="",font = ("This new Roman",20))
pressure_lable1.place(x=250,y=470,height=50,width=210)

done_button = Button(win,text ="Done",font = ("This new Roman",20,"bold"),command=data_get)
done_button.place(y=190,height=50,width=100,x=200)


win.mainloop()









# OR

import requests

api_key = '30d4741c779ba94c470ca1f63045390a'

user_input = input("Enter city: ")

weather_data = requests.get(
    f"https://api.openweathermap.org/data/2.5/weather?q={user_input}&units=imperial&APPID={api_key}")

if weather_data.json()['cod'] == '404':
    print("No City Found")
else:
    weather = weather_data.json()['weather'][0]['main']
    temp = round(weather_data.json()['main']['temp'])

    print(f"The weather in {user_input} is: {weather}")
    print(f"The temperature in {user_input} is: {temp}ºF")








# OR


from tkinter import *
from tkinter import ttk
import requests


def data_get():
    city = city_name.get()
    api_key = "ada516de7408b967ed3882bc30df6f14"
    base_url = "https://api.openweathermap.org/data/2.5/weather"
    complete_url = f"{base_url}?q={city}&appid={api_key}"
    response = requests.get(complete_url)

    if response.status_code == 200:
        data = response.json()
        w_label1.config(text=data["weather"][0]["main"])
        wb_label1.config(text=data["weather"][0]["description"])
        temp_label1.config(text=str(int(data["main"]["temp"] - 273.15)))
        pressure_label1.config(text=data["main"]["pressure"])
    else:
        w_label1.config(text="N/A")
        wb_label1.config(text="N/A")
        temp_label1.config(text="N/A")
        pressure_label1.config(text="N/A")
        print("City Not Found")


# Setting up the main window
win = Tk()
win.title("Mishra Weather App")
win.config(bg="blue")
win.geometry("500x570")

name_label = Label(win, text="Mishra Weather App", font=("Times New Roman", 30, "bold"), bg="blue", fg="white")
name_label.place(x=25, y=50, height=50, width=450)

list_name = ["Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh", "Goa", "Gujarat",
             "Himachal Pradesh", "Jammu and Kashmir", "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh",
             "Maharashtra", "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha", "Punjab", "Rajasthan", "Sikkim",
             "Tamil Nadu", "Telangana", "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
             "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli", "Daman and Diu", "Lakshadweep",
             "National Capital Territory of Delhi", "Puducherry"]
city_name = StringVar()
com = ttk.Combobox(win, values=list_name, font=("Times New Roman", 20, "bold"), textvariable=city_name)
com.place(x=25, y=120, height=50, width=450)

# Labels for displaying the weather information
w_label = Label(win, text="Weather Climate", font=("Times New Roman", 20), bg="blue", fg="white")
w_label.place(x=25, y=260, height=50, width=210)
w_label1 = Label(win, text="", font=("Times New Roman", 20), bg="blue", fg="white")
w_label1.place(x=250, y=260, height=50, width=210)

wb_label = Label(win, text="Weather Description", font=("Times New Roman", 17), bg="blue", fg="white")
wb_label.place(x=25, y=330, height=50, width=210)
wb_label1 = Label(win, text="", font=("Times New Roman", 17), bg="blue", fg="white")
wb_label1.place(x=250, y=330, height=50, width=210)

temp_label = Label(win, text="Temperature (°C)", font=("Times New Roman", 20), bg="blue", fg="white")
temp_label.place(x=25, y=400, height=50, width=210)
temp_label1 = Label(win, text="", font=("Times New Roman", 20), bg="blue", fg="white")
temp_label1.place(x=250, y=400, height=50, width=210)

pressure_label = Label(win, text="Pressure (hPa)", font=("Times New Roman", 20), bg="blue", fg="white")
pressure_label.place(x=25, y=470, height=50, width=210)
pressure_label1 = Label(win, text="", font=("Times New Roman", 20), bg="blue", fg="white")
pressure_label1.place(x=250, y=470, height=50, width=210)

# Button to trigger the weather data retrieval
done_button = Button(win, text="Get Weather", font=("Times New Roman", 20, "bold"), command=data_get)
done_button.place(y=190, height=50, width=200, x=150)

win.mainloop()






# 12/07/2024

# main.py

from tkinter import *
from tkinter import ttk
from urllib import request
import json

def data_get():
    city = city_name.get()
    api_key = "ada516de7408b967ed3882bc30df6f14"
    url = f"https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}"
    
    try:
        with request.urlopen(url) as response:
            data = json.loads(response.read())
            
            # Update labels with weather information
            w_lable1.config(text=data["weather"][0]["main"])
            wb_lable1.config(text=data["weather"][0]["description"])
            temp_lable1.config(text=str(int(data["main"]["temp"]-273.15)))
            pressure_lable1.config(text=data["main"]["pressure"])
    
    except Exception as e:
        print(f"Error fetching data: {e}")
        # Optionally, show an error message to the user
        w_lable1.config(text="Error fetching data")
        wb_lable1.config(text="")
        temp_lable1.config(text="")
        pressure_lable1.config(text="")

win = Tk()
win.title("Mishra PRYJ")
win.config(bg="blue")
win.geometry("500x570")

name_label = Label(win, text="Mishra Weather App", font=("Times New Roman", 30, "bold"))
name_label.place(x=25, y=50, height=50, width=450)

list_name = ["Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh", "Goa", "Gujarat",
             "Himachal Pradesh", "Jammu and Kashmir", "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh",
             "Maharashtra", "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha", "Punjab", "Rajasthan", "Sikkim",
             "Tamil Nadu", "Telangana", "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
             "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli", "Daman and Diu", "Lakshadweep",
             "National Capital Territory of Delhi", "Puducherry"]

city_name = StringVar()
com = ttk.Combobox(win, text="Mishra Weather App", values=list_name, font=("Times New Roman", 20, "bold"), textvariable=city_name)
com.place(x=25, y=120, height=50, width=450)

w_label = Label(win, text="Weather Climate", font=("Times New Roman", 20))
w_label.place(x=25, y=260, height=50, width=210)
w_lable1 = Label(win, text="", font=("Times New Roman", 20))
w_lable1.place(x=250, y=260, height=50, width=210)

wb_label = Label(win, text="Weather Description", font=("Times New Roman", 17))
wb_label.place(x=25, y=330, height=50, width=210)
wb_lable1 = Label(win, text="", font=("Times New Roman", 17))
wb_lable1.place(x=250, y=330, height=50, width=210)

temp_label = Label(win, text="Temperature", font=("Times New Roman", 20))
temp_label.place(x=25, y=400, height=50, width=210)
temp_lable1 = Label(win, text="", font=("Times New Roman", 20))
temp_lable1.place(x=250, y=400, height=50, width=210)

pressure_label = Label(win, text="Pressure", font=("Times New Roman", 20))
pressure_label.place(x=25, y=470, height=50, width=210)
pressure_lable1 = Label(win, text="", font=("Times New Roman", 20))
pressure_lable1.place(x=250, y=470, height=50, width=210)

done_button = Button(win, text="Done", font=("Times New Roman", 20, "bold"), command=data_get)
done_button.place(y=190, height=50, width=100, x=200)

win.mainloop()



# Other Method:
# wth.py

from tkinter import *
from tkinter import ttk
import requests

def data_get():
    city = city_name.get()
    data = requests.get("https://api.openweathermap.org/data/2.5/weather?q="+city+"&appid=ada516de7408b967ed3882bc30df6f14").json()
    w_lable1.config(text=data["weather"][0]["main"])
    wb_lable1.config(text=data["weather"][0]["description"])
    temp_lable1.config(text=str(int(data["main"]["temp"]-273.15)))
    pressure_lable1.config(text=data["main"]["pressure"])


win = Tk()
win.title("Mishra PRYJ")
win.config(bg= "blue")
win.geometry("500x570")


name_lable = Label(win,text ="Mishra Weather App",font = ("This new Roman",30,"bold"))
name_lable.place(x=25,y=50,height=50,width=450)

list_name = ["Andhra Pradesh", "Arunachal Pradesh", "Assam", "Bihar", "Chhattisgarh", "Goa", "Gujarat",
             "Himachal Pradesh", "Jammu and Kashmir", "Jharkhand", "Karnataka", "Kerala", "Madhya Pradesh",
             "Maharashtra", "Manipur", "Meghalaya", "Mizoram", "Nagaland", "Odisha", "Punjab", "Rajasthan", "Sikkim",
             "Tamil Nadu", "Telangana", "Tripura", "Uttar Pradesh", "Uttarakhand", "West Bengal",
             "Andaman and Nicobar Islands", "Chandigarh", "Dadra and Nagar Haveli", "Daman and Diu", "Lakshadweep",
             "National Capital Territory of Delhi", "Puducherry"]
city_name = StringVar()
com = ttk.Combobox(win,text ="Mishra Weather App",values = list_name,font = ("This new Roman",20,"bold"),textvariable=city_name)
com.place(x=25,y=120,height=50,width=450)

w_lable = Label(win,text ="Weather Climate",font = ("This new Roman",20))
w_lable.place(x=25,y=260,height=50,width=210)
w_lable1 = Label(win,text ="",font = ("This new Roman",20))
w_lable1.place(x=250,y=260,height=50,width=210)

wb_lable = Label(win,text ="Weather Description",font = ("This new Roman",17))
wb_lable.place(x=25,y=330,height=50,width=210)
wb_lable1 = Label(win,text ="",font = ("This new Roman",17))
wb_lable1.place(x=250,y=330,height=50,width=210)

temp_lable = Label(win,text ="Temprature",font = ("This new Roman",20))
temp_lable.place(x=25,y=400,height=50,width=210)
temp_lable1 = Label(win,text ="",font = ("This new Roman",20))
temp_lable1.place(x=250,y=400,height=50,width=210)


pressure_lable = Label(win,text ="Pressure",font = ("This new Roman",20))
pressure_lable.place(x=25,y=470,height=50,width=210)
pressure_lable1 = Label(win,text ="",font = ("This new Roman",20))
pressure_lable1.place(x=250,y=470,height=50,width=210)

done_button = Button(win,text ="Done",font = ("This new Roman",20,"bold"),command=data_get)
done_button.place(y=190,height=50,width=100,x=200)


win.mainloop()
