import json 
import requests
import csv 

# reading file
with open("/Users/angelikabaloy/Desktop/Data Science/schacon.repos.json", 'r') as file:
    data = json.load(file)

print(data[0])

# name / html_url / updated_at / visibility 

list = []

for i in data[0:5]:
    name = i['name']
    html = i['html_url']
    update = i['updated_at']
    visibility = i['visibility']

    list.append(f"{name},{html},{update},{visibility}")

for i in list:
    print(i) 
