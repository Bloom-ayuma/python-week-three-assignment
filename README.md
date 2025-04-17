# python-week-three-assignment
1. Create a function named calculate_discount(price, discount_percent) that calculates the final price after applying a discount. The function should take the original price (price) and the discount percentage (discount_percent) as parameters. If the discount is 20% or higher, apply the discount; otherwise, return the original price.
2. Using the calculate_discount function, prompt the user to enter the original price of an item and the discount percentage. Print the final price after applying the discount, or if no discount was applied, print the original price.

def calculate_discount(price, discount_percent):
    if discount_percent >= 20:
        discount_amount = (discount_percent / 100) * price
        return price - discount_amount
    else:
        return price

def add_tax(price, tax_percent):
    tax_amount = (tax_percent / 100) * price
    return price + tax_amount

def format_currency(amount):
    return f"${amount:,.2f}"

def main():
    while True:
        try:
            # Get original price
            original_price = float(input("💰 Enter the original price of the item: $"))
            if original_price < 0:
                print("❌ Price cannot be negative. Try again.")
                continue

            # Get discount percentage
            discount = float(input("🔻 Enter the discount percentage: "))
            if discount < 0 or discount > 100:
                print("❌ Discount must be between 0 and 100. Try again.")
                continue

            # Calculate price after discount
            discounted_price = calculate_discount(original_price, discount)

            if discount >= 20:
                print(f"✅ Discount of {discount}% applied.")
            else:
                print("⚠️ Discount less than 20%. No discount applied.")

            # Ask about tax
            apply_tax = input("💸 Do you want to add tax? (yes/no): ").strip().lower()
            if apply_tax == "yes":
                tax_percent = float(input("🧾 Enter the tax percentage: "))
                if tax_percent < 0:
                    print("❌ Tax can't be negative. Try again.")
                    continue
                final_price = add_tax(discounted_price, tax_percent)
            else:
                final_price = discounted_price

            print(f"\n💵 Final price: {format_currency(final_price)}\n")
            break

        except ValueError:
            print("🚫 Invalid input. Please enter numbers only.")

if __name__ == "__main__":
    main()
