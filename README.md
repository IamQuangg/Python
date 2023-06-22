# Set up data
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
# calculate mean score 
	import matplotlib.pyplot as plt 
	import numpy as np 

	x = np.arange(12)
	y = np.arange(12)
	print(x)

	fig , axis = plt.subplots()
	plt.bar(x, average)
	plt.xticks(x,y)
	axis.set_ylim(0,10)
	axis.set_ylabel('Điểm trung bình')
	rects = axis.patches
	labels = average
	for rect, label in zip(rects, average):
   	 height = rect.get_height()
    	axis.text(rect.get_x() + rect.get_width() / 2, height + 0, label, ha='center', va='bottom')
 
	plt.title('')
	plt.show()
 ![Figure_2](https://github.com/IamQuangg/Python/assets/128073066/caa27304-1b50-4219-9759-190661382b2a)
 # Điểm trung bình theo độ tuổi 
	fig , axis = plt.subplots()
	plt.bar(x, num_of_student_per_age_group)
	plt.plot(x, average_of_student_per_age_group, color = 'red', marker = 'o')
	plt.xticks(x,y)
	axis.set_ylim(0,70000)
	age_lable =[17,18,19,20,21,22,23,24,25,26,">26"]
	plt.xticks(x, age_lable)
	axis.set_ylabel('Số học sinh')
	axis.set_xlabel('Tuổi')
	# right side tick
	axis2 = axis.twinx()
	axis2.tick_params('y',colors ='red')
	axis2.set_ylim(0,10)
	axis2.set_ylabel("Điểm trung bình")
	
	rects = axis.patches
	labels = [2, 66327, 4463, 1396, 767, 384, 300, 223, 177, 109, 296]
	for rect, label in zip(rects, num_of_student_per_age_group):
	    height = rect.get_height()
	    axis.text(rect.get_x() + rect.get_width() / 2, height + 0, label, ha='center', va='bottom')
	 
	plt.title('Điểm trung bình theo độ tuổi')
	plt.show()
![mean_score](https://github.com/IamQuangg/Python/assets/128073066/dfd3f5a6-90fd-4d3b-814f-de0abbd0129a)
