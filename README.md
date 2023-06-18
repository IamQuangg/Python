with open("clean_data.csv", encoding= "utf8") as file:
	data= file.read().split("\n")

header = data[0]
students = data[1:]
# remove last student(empty student)
students.pop()

total_student = len(students)

header = header.split(",")
subject = header[5:]

for i in range(len(students)):

	students[i] = students[i].split(",")

not_take_exam = [0,0,0,0,0,0,0,0,0,0,0]

for s in students:

	for i in range(5,16):
	
		if s[i]== "-1":
			not_take_exam[i-5] +=1 
# convert to percentage
for i in range(0,11):

	not_take_exam_percentage[i] = round(not_take_exam[i]*100/total_student, 2)

import matplotlib.pyplot as plt

import numpy 

figure, axis = plt.subplots()

# list from 0-11
y_pos = numpy.arange(len(subject))

# plot the barchart using 2 list
plt.bar(y_pos, not_take_exam_percentage)

# change horizontal category name
plt.xticks(y_pos, subject)

# set limit to vertical axis
axis.set_ylim(0,100)

# label and title
plt.ylabel('Percentage')
plt.title('Số học sinh bỏ thi hoặc không đăng kí')

# Draw number of student on top of each bar
rects = axis.patches

for rect, label in zip(rects, not_take_exam):

    height = rect.get_height()
    
    axis.text(rect.get_x() + rect.get_width() / 2, height + 2, label, ha='center', va='bottom')
![Figure_1](https://github.com/IamQuangg/Python/assets/128073066/4d62feee-bee4-4f37-ac2c-b2ee832afb59)

# show the plot
plt.show()
