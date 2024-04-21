# environment
import turtle
import random

# Set up the screen
screen = turtle.Screen()
screen.bgcolor("black")

# Fireworks class to create a firework effect
class Firework:
    def __init__(self):
        self.t = turtle.Turtle()
        self.t.hideturtle()
        self.t.speed(0)
        self.t.up()

    def launch(self):
        # Random starting point and burst point
        start_x = random.randint(-200, 200)
        burst_y = random.randint(0, 200)
        
        # Launch firework
        self.t.goto(start_x, -200)
        self.t.down()
        self.t.color("white")
        self.t.goto(start_x, burst_y)
        self.t.up()

        # Burst into multiple lines
        self.burst(burst_y)

    def burst(self, burst_y):
        colors = ["red", "blue", "green", "yellow", "orange", "purple"]
        for _ in range(20):
            angle = random.randint(0, 360)
            distance = random.randint(50, 150)
            self.t.goto(burst_y, 0)  # Starting from the burst point
            self.t.setheading(angle)
            self.t.color(random.choice(colors))
            self.t.down()
            self.t.forward(distance)
            self.t.up()

# Main fireworks sequence
fireworks = Firework()

for _ in range(5):  # Create 5 fireworks
    fireworks.launch()

screen.mainloop()  # Keeps the window open
