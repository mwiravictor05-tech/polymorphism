#include <iostream>
using namespace std;

// Base class
class Shape {
public:
    virtual void area() {
        cout << "Area calculation not defined for generic shape." << endl;
    }
};

// Derived class Rectangle
class Rectangle : public Shape {
private:
    double length, width;

public:
    Rectangle(double l, double w) {
        length = l;
        width = w;
    }

    void area() override {
        cout << "Area of Rectangle: " << length * width << endl;
    }
};

// Derived class Circle
class Circle : public Shape {
private:
    double radius;

public:
    Circle(double r) {
        radius = r;
    }

    void area() override {
        cout << "Area of Circle: " << 3.142 * radius * radius << endl;
    }
};

// Test class
class PolymorphismTest {
public:
    static void run() {
        int choice;
        Shape* shapePtr;

        cout << "Choose shape (1 = Rectangle, 2 = Circle): ";
        cin >> choice;

        if (choice == 1) {
            double l, w;
            cout << "Enter length and width: ";
            cin >> l >> w;
            shapePtr = new Rectangle(l, w);
        }
        else if (choice == 2) {
            double r;
            cout << "Enter radius: ";
            cin >> r;
            shapePtr = new Circle(r);
        }
        else {
            shapePtr = new Shape();
        }

        // Demonstrating polymorphism
        shapePtr->area();

        delete shapePtr;
    }
};

int main() {
    PolymorphismTest::run();
    return 0;
}
