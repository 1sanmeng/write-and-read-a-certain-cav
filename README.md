# write-and-read-a-certain-cav
#this code can write a csv file through the given list. After finished, i wrote a code to read through the csv file and print what i used the file content  to get the output.I think this is quite interesting.Keep learning.
import os
import csv
def write(folder,file,content):
    os.chdir(os.path.dirname(os.path.abspath(__file__)))#this one is so important,cuz we input '.'(this will direct to cwd,but cwd might not be as same as the dir we wanna write,so this code will change our dir to make sure we are in the right dir)
    os.makedirs(folder,exist_ok=True)
    with open(file,'w') as f:
        writer=csv.writer(f)
        writer.writerows(content)
    print('all done')
def read(file_name):
    with open(file_name) as r:
        reader=csv.DictReader(r)#this is to get the dic that we want
        for row in reader:
            print(f'a {row["color"]} {row["name"]} is {row["type"]}')#can not use the same qutation mark
to_be_write=[['name','color', 'type'],
    ['carnation','pink','annual'],
    ['daffodil','yellow','perennial'],
    ['iris','blue','perennial'],
    ['poinsettia','red','perennial'],
    ['sunflower', 'yellow','annual']]
write('.','encyclopedia_csv',to_be_write)
read('encyclopedia_csv')
