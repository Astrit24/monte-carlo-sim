import random

def rollTwoDice():

  return random.randint(1,6)


# The number of squares on the board
num_squares = 40

# A list to contain the total value rolled.
counters=[0]*num_squares

# A variable to hold the current position
current_Position = 0

# Set the number of rolls
num_Rolls = 10**4

# Print a message
print("Enter the number of dice throws: ")

counter_jail = 0
# Roll the dice
for i in range(num_Rolls):
 
  d1 = rollTwoDice()
  d2 = rollTwoDice()
  total_Value= d1+d2

  # Move the player to the next position
  current_Position = current_Position + total_Value
  
  if current_Position==31:
      current_Position=11
      counter_jail +=1


  # If the player has moved past last square, wrap board around.
  if current_Position >= num_squares:
    current_Position = current_Position - num_squares

  counters[current_Position] = counters[current_Position] + 1.

for i in range(len(counters)):
  counters[i] = counters[i] / float(num_Rolls)

print(f"Times sent to jail: {counter_jail} ({counter_jail/sum(counters)}%)")

print(f"Least likely to land on Spot {counters.index(min(counters))} {(counters.index(min(counters)))/sum(counters)}% of the lands)")
   
print(f"Most likely to land on Spot {counters.index(max(counters))} {(counters.index(max(counters)))/sum(counters)}% of the lands)")


