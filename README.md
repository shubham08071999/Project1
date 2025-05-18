# Project1
# restaurant Management system

# Cafe menu
menu = {
    "coffee": 50,
    "tea": 30,
    "sandwich": 100,
    "cake": 80
}

# Initialize order and total
order = {}
total = 0

def display_menu():
    print("\n--- Menu ---")
    for item, price in menu.items():
        print(f"{item.capitalize()}: ₹{price}")

def take_order():
    global order, total
    while True:
        display_menu()
        choice = input("\nEnter your choice (or 'done' to finish ordering): ").lower()
        if choice == 'done':
            break
        elif choice in menu:
            quantity = int(input("Enter quantity: "))
            if choice in order:
                order[choice] += quantity
            else:
                order[choice] = quantity
            print(f"Added {quantity} {choice}(s) to your order.")
        else:
            print("Invalid choice. Please choose a valid option.")

def view_order():
    global order, total
    print("\n--- Your Order ---")
    total = 0
    for item, quantity in order.items():
        price = menu[item] * quantity
        print(f"{item.capitalize()}: {quantity} x ₹{menu[item]} = ₹{price}")
        total += price
    print(f"\nTotal: ₹{total}")

def confirm_order():
    view_order()
    confirm = input("\nConfirm your order? (yes/no): ").lower()
    if confirm == 'yes':
        print("Order confirmed. Thank you!")
        payment()
    else:
        print("Order cancelled.")

def payment():
    global total
    print(f"\nPlease pay ₹{total}.")
    amount = int(input("Enter amount paid: "))
    if amount >= total:
        print(f"Change: ₹{amount - total}")
        print("Thank you for your payment!")
    else:
        print("Insufficient payment. Please try again.")

def main():
    take_order()
    confirm_order()

if __name__ == "__main__":
    main()
