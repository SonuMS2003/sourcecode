public class Product {
    static int totalProducts = 0;
    String name;
    double price;
    int quantity;

    Product() {
        name = "Unknown";
        price = 0;
        quantity = 0;
        totalProducts++;
    }

    Product(String name, double price, int quantity) {
        this.name = name;
        this.price = price;
        this.quantity = quantity;
        totalProducts++;
    }

    Product(Product other) {
        this.name = other.name;
        this.price = other.price;
        this.quantity = other.quantity;
        totalProducts++;
    }

    double stockValue() {
        return price * quantity;
    }

    void display() {
        System.out.println(name + " | Rs " + price + " | qty " + quantity);
    }
}switch (choice) {
    case 1:
        System.out.print("Name: ");
        String name = sc.nextLine();
        System.out.print("Price: ");
        double price = sc.nextDouble();
        System.out.print("Quantity: ");
        int quantity = sc.nextInt();
        sc.nextLine();
        if (count == 10) {
            System.out.println("Inventory is full.");
        } else if (price <= 0 || quantity < 0) {
            System.out.println("Error: price must be above 0 and quantity cannot be negative.");
        } else {
            products[count] = new Product(name, price, quantity);
            count++;
            System.out.println("Product added.");
        }
        break;
    case 2:
        if (count == 0) {
            System.out.println("No products yet.");
        } else {
            for (int i = 0; i < count; i++) {
                System.out.print((i + 1) + ". ");
                products[i].display();
            }
        }
        break;
    case 3:
        if (count == 0) {
            System.out.println("No products yet.");
        } else {
            double total = 0;
            for (int i = 0; i < count; i++) {
                total += products[i].stockValue();
            }
            System.out.println("Total stock value: Rs " + total);
        }
        break;
    case 4:
        if (count == 0) {
            System.out.println("No products yet.");
        } else {
            double sum = 0;
            for (int i = 0; i < count; i++) {
                sum += products[i].price;
            }
            double average = sum / count;
            System.out.println("Average price: " + average);
            System.out.println("Rounded down: " + (int) average);
        }
        break;
    case 5:
        System.out.print("Product number: ");
        int num = sc.nextInt();
        System.out.print("Quantity to add: ");
        int extra = sc.nextInt();
        sc.nextLine();
        if (num < 1 || num > count || extra <= 0) {
            System.out.println("Error: invalid product number or quantity.");
        } else {
            products[num - 1].quantity += extra;
            System.out.println("Restocked. New quantity: " + products[num - 1].quantity);
        }
        break;
    case 6:
        System.out.print("Product number: ");
        int n = sc.nextInt();
        sc.nextLine();
        if (n < 1 || n > count) {
            System.out.println("Error: invalid product number.");
        } else if (count == 10) {
            System.out.println("Inventory is full.");
        } else {
            Product copy = new Product(products[n - 1]);
            copy.name = copy.name + " (copy)";
            products[count] = copy;
            count++;
            System.out.println("Product duplicated.");
        }
        break;
    case 0:
        System.out.println("Goodbye!");
        break;
}
