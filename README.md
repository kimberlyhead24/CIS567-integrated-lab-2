# CIS567-integrated-lab-2
Poker Dice Game- similar to Yahtzee
# Find highest score
def find_high_score (values):
    high_score = 0

    for num in range(1, 7):
        high_score = max(high_score, check_singles(values, num))
    high_score = max(high_score, check_three_of_kind(values))
    high_score = max(high_score, check_four_of_kind(values))
    high_score = max(high_score, check_five_of_kind(values))
    high_score = max(high_score, check_full_house(values))
    high_score = max(high_score, check_straight(values))
    return high_score

# Add all occurences of goal value
def check_singles(dice, goal):
    score = 0
    for val in dice:
        if val == goal:
            score += val
    return score

# Check for three of a kind (score = 30)
def check_three_of_kind(dice):
    score = 0
    for i in range(3):          
        if dice[i] == dice[i+2]:
            score = 30
    return score

# Check for four of a kind (score = 40)
def check_four_of_kind(dice):
    score = 0
    for i in range(2):  # check i, i+1, i+2, i+3
        if dice[i] == dice[i+3]:
            score = 40
    return score

# Check for five of a kind (score = 50)
def check_five_of_kind(dice):
    score = 0
    if dice[0] == dice[4]:
        score = 50

    return score

# Check for full house (score = 35)
def check_full_house(dice):
    score = 0

    if dice[0] == dice[4]:
        score = 35
    elif dice[0] == dice[2] and dice[3] == dice[4]:
        score = 35
    elif dice[0] == dice[1] and dice[2] == dice[4]:
        score = 35

    return score

# Check for straight (score = 45)
def check_straight(dice):
    score = 0
    if dice == [1, 2, 3, 4, 5] or dice == [2, 3, 4, 5, 6]:
        score = 45
    return score

if __name__ == '__main__':  # Do not modify
    # Fill array with five dice from input
    dice = [int(val) for val in input().split()]

    high_score = 0

    # Place dice in ascending order
    dice.sort()

    # Find high score and output
    high_score = find_high_score(dice)

    print(f'High score: { high_score }')
