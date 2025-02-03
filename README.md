Project : Railway Ticket Booking System


Implementation: 
Steps for Implementing Railway Ticket Booking System 
1. Create a Data Structure 
o Use a pandas DataFrame to store train details, including train names, available seats 
(Sleeper, AC), and ticket prices. 
2. Check Seat Availability 
o Implement a function to check if the requested number of seats is available in the 
selected train and class. 
3. Book Tickets 
o If seats are available, reduce the available count. 
o Generate a unique PNR number for the booking. 
o Calculate the total fare based on the number of seats and class price. 
o Display booking confirmation. 
4. Enhancements  
o Include passenger details (name, age, gender, etc.). 
o Allow users to select source and destination stations. 
o Implement date and time selection for travel. 
o Introduce dynamic pricing based on demand. 
o Add a waiting list system when seats are full. 
o Create a cancellation and refund system. 
o Implement a graphical user interface (GUI) for better user experience. 
Code: 
import pandas as pd 
import random 
# Sample train data 
train_data = { 
'Train': ['Shatabdi Express', 'Rajdhani Express', 'Garib Rath', 'Duronto Express'], 
'Sleeper Seats': [168, 150, 200, 120], 
'AC Seats': [50, 75, 60, 40], 
'Sleeper Price': [500, 700, 300, 600], 
'AC Price': [1200, 1500, 800, 1000] 
} 
# Create a DataFrame 
trains = pd.DataFrame(train_data) 
# Function to check seat availability 
def check_availability(train, class_type, num_seats): 
if train in trains['Train'].values: 
index = trains[trains['Train'] == train].index[0] 
 
 
 
        if class_type == 'Sleeper': 
            if trains.loc[index, 'Sleeper Seats'] >= num_seats: 
                return True 
            else: 
                return False 
        elif class_type == "AC": 
            if trains.loc[index, 'AC Seats'] >= num_seats: 
                return True 
            else: 
                return False 
        else: 
            print("Invalid class type.") 
            return False 
    else: 
        print("Train not found.") 
        return False 
 
# Function to book tickets 
def book_tickets(train, class_type, num_seats): 
    if check_availability(train, class_type, num_seats): 
        index = trains[trains['Train'] == train].index[0] 
        if class_type == 'Sleeper': 
            trains.loc[index, 'Sleeper Seats'] -= num_seats 
            price = trains.loc[index, 'Sleeper Price'] 
        elif class_type == "AC": 
            trains.loc[index, 'AC Seats'] -= num_seats 
            price = trains.loc[index, 'AC Price'] 
         
        # Generate a random PNR number 
        pnr_number = ''.join(random.choices('123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ', k=10)) 
 
        print("Tickets booked successfully!") 
        print("PNR Number:", pnr_number) 
        print("Total fare:", price * num_seats) 
    else: 
        print("Booking failed. Seats not available.") 
 
# Example usage: 
book_tickets('Shatabdi Express', 'AC', 2) 
book_tickets('Rajdhani Express', 'Sleeper', 5) 
 
print("\nUpdated Train Availability: \n", trains) # Railway-Ticket-Booking-System

