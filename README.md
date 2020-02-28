# College_Scores

def main ():

    def calc_average_sat(reading,math,writing):
        average = (reading + math + writing)/3
        return average

    def calc_percentage(place,s_tudent):
        ranking = place/s_tudent
        return ranking

    # create loop until user wants to quit
    status = input("Press enter to view the admission status. ")

    while status != "yes":
        name = input("Please enter applicant's name: ")

    
    # applicants submit three test scores
        critical_reading = int(input("What is your Critical Reading score? "))
        mathematics = int(input("What is your Mathematics score? "))
        writing_sat = int(input("What is your Writing SAT score? "))
        # average the test scores
        average_sat = calc_average_sat(critical_reading,mathematics,writing_sat)

        # enter the rank in graduating class
        rank = float(input("What is your rank in your class? "))

        # enter the number of students in the graduating class
        students = float(input("How many students are in the graduating class? "))

        # find percentage in their class
        percentage = calc_percentage(rank,students)
        
        # an impossible number = refused admission
        # 0 = deny
        # 1 = accept
        state = -1
        if critical_reading < 200 or mathematics < 200 or writing_sat < 200:
            state = 0
        elif critical_reading > 800 or mathematics > 800 or writing_sat > 800:
            state = 0

        # any test score is 800 = acceptance
        elif critical_reading == 800 or mathematics == 800 or writing_sat == 800:
            state = 1

        # test score below 300 = refused accpetance
        elif critical_reading < 300 or mathematics < 300 or writing_sat < 300:
            state = 0


        # test score is averaging above 650 + top quarter of their graduating class
        # = acceptance
        elif average_sat > 650 and percentage < 0.25:
            state = 1


        # any two test scores is below 400 + bottom quarter of class
        # = refused admissions
        elif average_sat < 450 or percentage > 0.75:
            state = 0
        elif percentage < .00:
            state = 0

                
        # use if-elif-else: they are on waiting list
        if state == 1:
            print("Accept")

        elif state == 0:
            print("Reject")

        else:
            print("Waitlist")

        # calculate is student is accepted
        # display the results
main()
