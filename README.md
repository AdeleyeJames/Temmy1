import time

def kick_ball():
    ball = "O"
    spaces = 0

    print("Getting ready to kick the ball...\n")

    for _ in range(10):
        print(" " * spaces + ball)
        spaces += 1
        time.sleep(0.2)  # Adding a delay to simulate movement

    print("\nGoal!")

kick_ball(
    <br>
    %time% %date% %location%
