# 1.TASK 2: STOCK PORTFOLIO TRACKER

# Hardcoded dictionary of stock prices
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOGL": 2800,
    "AMZN": 3200,
    "MSFT": 230
}

def get_stock_portfolio():
    portfolio = {}
    while True:
        stock_name = input("Enter stock name (or 'done' to finish): ").upper()
        if stock_name.lower() == 'done':
            break
        if stock_name not in stock_prices:
            print("Stock not found. Please try again.")
            continue
        try:
            quantity = int(input("Enter quantity: "))
            if quantity <= 0:
                print("Quantity must be a positive integer.")
                continue
        except ValueError:
            print("Invalid quantity. Please try again.")
            continue
        portfolio[stock_name] = quantity
    return portfolio

def calculate_total_investment(portfolio):
    total_investment = 0
    print("\nStock Portfolio:")
    print("----------------")
    for stock, quantity in portfolio.items():
        stock_value = stock_prices[stock] * quantity
        total_investment += stock_value
        print(f"{stock}: {quantity} shares x ${stock_prices[stock]} = ${stock_value}")
    return total_investment

def save_portfolio(portfolio, total_investment):
    with open("portfolio.txt", "w") as f:
        f.write("Stock Portfolio:\n")
        f.write("----------------\n")
        for stock, quantity in portfolio.items():
            stock_value = stock_prices[stock] * quantity
            f.write(f"{stock}: {quantity} shares x ${stock_prices[stock]} = ${stock_value}\n")
        f.write(f"\nTotal Investment: ${total_investment}")
    print("Portfolio saved to portfolio.txt")

def main():
    print("Available stocks:")
    for stock, price in stock_prices.items():
        print(f"{stock}: ${price}")
    portfolio = get_stock_portfolio()
    total_investment = calculate_total_investment(portfolio)
    print(f"\nTotal Investment: ${total_investment}")
    save = input("Save portfolio to file? (yes/no): ").lower()
    if save == 'yes':
        save_portfolio(portfolio, total_investment)

if __name__ == "__main__":
    main()

---------------------------------

# 2.TASK 4: BASIC CHATBOT

def get_response(user_input):
    # Convert user input to lowercase for case-insensitive matching
    user_input = user_input.lower()

    # Define predefined replies
    if user_input == "hello":
        return "Hi!"
    elif user_input == "how are you":
        return "I'm fine, thanks!"
    elif user_input == "bye":
        return "Goodbye!"
    else:
        return "I didn't understand that. Please try again!"

def chatbot():
    print("Welcome to the chatbot! Type 'bye' to exit.")
    
    while True:
        user_input = input("You: ")
        response = get_response(user_input)
        print("Chatbot: ", response)
        
        if user_input.lower() == "bye":
            break

# Run the chatbot
chatbot()

-------------------------------
# 3.TASK 3:TASK AUTOMATION WITH PYTHON SCRIPT

import os
import shutil

# Define source and destination folders
source_folder = '/path/to/source/folder'
destination_folder = '/path/to/destination/folder'

# Create the destination folder if it doesn't exist
if not os.path.exists(destination_folder):
    os.makedirs(destination_folder)

# Move all .jpg files from source to destination
for filename in os.listdir(source_folder):
    if filename.endswith(".jpg"):
        source_file = os.path.join(source_folder, filename)
        destination_file = os.path.join(destination_folder, filename)
        shutil.move(source_file, destination_file)
        print(f"Moved {filename} to {destination_folder}")


---------------------------------
