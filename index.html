# pos_system.py
import tkinter as tk
from tkinter import messagebox
from escpos.printer import Serial  # For Bluetooth printing
import datetime

# --------------------------
# Sample Data
# --------------------------
tables = {
    "Table 1": {"status": "Free", "order": [], "total": 0},
    "Table 2": {"status": "Free", "order": [], "total": 0},
    "Table 3": {"status": "Free", "order": [], "total": 0},
    "Table 4": {"status": "Free", "order": [], "total": 0},
}

menu_items = {
    "Burger": 120,
    "Pizza": 250,
    "Coke": 50,
    "Fries": 80
}

sales_history = []

# --------------------------
# Functions
# --------------------------
def open_tables():
    table_window = tk.Toplevel(root)
    table_window.title("Tables")
    
    row = 0
    col = 0
    for table_name, data in tables.items():
        frame = tk.Frame(table_window, bd=2, relief="raised", padx=10, pady=10)
        frame.grid(row=row, column=col, padx=10, pady=10)

        # Status color
        color = "green" if data["status"] == "Free" else ("orange" if data["status"] == "Running" else "blue")
        tk.Label(frame, text=table_name, bg=color, width=15, height=2).pack(pady=5)

        # Total
        tk.Label(frame, text=f"Total: ₹{data['total']}").pack(pady=5)

        # Buttons
        tk.Button(frame, text="ADD ORDER", command=lambda t=table_name: add_order(t)).pack(pady=2)
        tk.Button(frame, text="BILL", command=lambda t=table_name: bill_table(t)).pack(pady=2)

        col += 1
        if col > 2:
            col = 0
            row += 1

def add_order(table_name):
    table = tables[table_name]
    order_window = tk.Toplevel(root)
    order_window.title(f"Add Order - {table_name}")

    tk.Label(order_window, text="Select Item").pack()
    item_var = tk.StringVar(order_window)
    item_var.set(list(menu_items.keys())[0])
    tk.OptionMenu(order_window, item_var, *menu_items.keys()).pack()

    tk.Label(order_window, text="Quantity").pack()
    qty_var = tk.IntVar(order_window)
    qty_var.set(1)
    tk.Entry(order_window, textvariable=qty_var).pack()

    def add_to_order():
        item = item_var.get()
        qty = qty_var.get()
        price = menu_items[item]
        table["order"].append({"item": item, "qty": qty, "price": price})
        table["total"] += price * qty
        table["status"] = "Running"
        messagebox.showinfo("Added", f"{qty} x {item} added to {table_name}")
        order_window.destroy()

    tk.Button(order_window, text="Add", command=add_to_order).pack(pady=5)

def bill_table(table_name):
    table = tables[table_name]
    if not table["order"]:
        messagebox.showwarning("Billing", "No order to bill!")
        return

    bill_window = tk.Toplevel(root)
    bill_window.title(f"Bill - {table_name}")

    total_label = tk.Label(bill_window, text="")
    total_label.pack()

    text = ""
    for o in table["order"]:
        text += f"{o['item']} x {o['qty']} = ₹{o['qty']*o['price']}\n"
    total_text = f"\nGRAND TOTAL: ₹{table['total']}"
    total_label.config(text=text + total_text)

    def confirm_payment():
        # Save to sales history
        sales_history.append({
            "table": table_name,
            "order": table["order"],
            "total": table["total"],
            "time": datetime.datetime.now()
        })

        # Print bill via Bluetooth printer
        try:
            printer = Serial(devfile='COM5', baudrate=9600)  # Replace COM5 with your printer
            printer.text("POS BILL\n")
            printer.text(f"{table_name}\n")
            printer.text(f"Time: {datetime.datetime.now().strftime('%Y-%m-%d %H:%M')}\n\n")
            for o in table["order"]:
                printer.text(f"{o['item']} x{o['qty']} = ₹{o['qty']*o['price']}\n")
            printer.text(f"\nGRAND TOTAL: ₹{table['total']}\n")
            printer.cut()
        except Exception as e:
            messagebox.showerror("Printer Error", str(e))

        # Reset table
        table["order"] = []
        table["total"] = 0
        table["status"] = "Free"
        bill_window.destroy()
        messagebox.showinfo("Payment", "Payment Confirmed and Bill Printed!")

    tk.Button(bill_window, text="Confirm & Print", command=confirm_payment).pack(pady=5)
    tk.Button(bill_window, text="Cancel", command=bill_window.destroy).pack(pady=5)

# --------------------------
# Placeholder Functions
# --------------------------
def open_inventory():
    messagebox.showinfo("Inventory", "Inventory screen placeholder")

def open_sales_report():
    messagebox.showinfo("Sales Report", "Sales Report screen placeholder")

# --------------------------
# Main Window
# --------------------------
root = tk.Tk()
root.title("POS System")
root.geometry("300x400")

tk.Button(root, text="Tables", width=20, height=2, command=open_tables).pack(pady=10)
tk.Button(root, text="Inventory", width=20, height=2, command=open_inventory).pack(pady=10)
tk.Button(root, text="Sales Report", width=20, height=2, command=open_sales_report).pack(pady=10)

root.mainloop()
