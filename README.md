import time
import random

# Sample list of products in stock
PRODUCTS = {
    '1': {'name': 'Laptop', 'price': 1500},
    '2': {'name': 'Phone', 'price': 800},
    '3': {'name': 'Headphones', 'price': 150},
    '4': {'name': 'Smartwatch', 'price': 200}
}

class DeliveryService:
    def __init__(self):
        self.cart = []
        self.total = 0
        self.address = ""
    
    def show_products(self):
        print("\nAvailable products:")
        for product_id, details in PRODUCTS.items():
            print(f"{product_id}. {details['name']} - ${details['price']}")
    
    def add_to_cart(self, product_id):
        if product_id in PRODUCTS:
            product = PRODUCTS[product_id]
            self.cart.append(product)
            self.total += product['price']
            print(f"Added {product['name']} to cart. Total: ${self.total}")
        else:
            print("Invalid product ID. Please choose again.")
    
    def input_address(self):
        self.address = input("\nEnter your delivery address: ")
        print(f"Address set to: {self.address}")
    
    def confirm_order(self):
        if not self.cart:
            print("\nYour cart is empty. Please add some items.")
            return False
        if not self.address:
            print("\nNo delivery address provided.")
            return False
        print("\nOrder confirmed!")
        print(f"Total: ${self.total}")
        print(f"Delivery address: {self.address}")
        return True
    
    def deliver(self):
        if self.confirm_order():
            print("\nProcessing your delivery...")
            time.sleep(2)  # Simulate processing time
            print("Your order is out for delivery!")
            time.sleep(2)
            # Simulating random delivery status
            statuses = ["Delivered successfully", "Delivery delayed", "Out for redelivery"]
            status = random.choice(statuses)
            print(f"Delivery Status: {status}")
    
def main():
    service = DeliveryService()
    while True:
        print("\nMenu:")
        print("1. View products")
        print("2. Add product to cart")
        print("3. Input delivery address")
        print("4. Confirm order and deliver")
        print("5. Exit")
        
        choice = input("\nChoose an option: ")
        
        if choice == '1':
            service.show_products()
        elif choice == '2':
            product_id = input("Enter product ID to add to cart: ")
            service.add_to_cart(product_id)
        elif choice == '3':
            service.input_address()
        elif choice == '4':
            service.deliver()
        elif choice == '5':
            print("Exiting the application. Goodbye!")
            break
        else:
            print("Invalid choice. Please choose again.")

if __name__ == "__main__":
    main()

