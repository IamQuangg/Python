with open("clean_data.csv", encoding= "utf8") as file:
	data= file.read().split("\n")

header = data[0]
students = data[1:]
# remove last student(empty student)
students.pop()
total_student = len(students)

header = header.split(",")
subject = header[5:]
print(subject)
for i in range(len(students)):
	students[i] = students[i].split(",")

not_take_exam = [0,0,0,0,0,0,0,0,0,0,0]
for s in students:
	for i in range(5,16):
		if s[i]== "-1":
			not_take_exam[i-5] +=1 
