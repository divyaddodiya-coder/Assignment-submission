# Assignment-submission

Project is an interactive learning application designed to explore how different cultures represent and construct numbers. It combines mathematics and linguistics to teach users global numeral systems such as Roman, Mayan, Chinese, Yoruba, and Babylonian.
The platform includes a numeral system library, a bi-directional conversion engine, and an Olympiad-style practice zone for pattern recognition and problem-solving.
Python implementations of Roman, Mayan, and Yoruba converters, along with a pattern-puzzle generator, demonstrate the system’s functionality.
The project helps learners understand numeral structures, identify cultural patterns, and practice analytical reasoning in a hands-on, intuitive way.

#Introduction
This project focuses on creating an interactive learning application that teaches users how different cultures across the world represent and understand numbers. The goal is to go beyond traditional mathematics and bring together both linguistic logic and numerical structure. The app acts as a bridge between culture, language, and  mathematics.
#Problem Statement
Across cultures, numeral systems differ widely in structure, base, linguistic logic, and symbolic representation. However:

Students have limited digital tools to study these systems.

Existing resources rarely combine linguistic reasoning with mathematical logic.

There are almost no platforms offering interactive, Olympiad-style puzzles related to numeral patterns.

Thus, learners lack an engaging environment to explore numerical concepts globally in a structured, interactive manner.

#Proposed Solution
A Global Numeral Systems Explorer App that:

Provides a curated library of numeral systems.

Converts Arabic numbers into various cultural numeral formats.

Converts cultural numeral expressions back to Arabic digits.

Offers pattern-based puzzles inspired by Linguistics Olympiad reasoning.

#Core Features A. Numeral System Library
Explains rules, structure, morphology, and examples for Roman, Mayan, Yoruba, etc.

B. Converter Engine

Bi-directional conversion between Arabic digits and cultural numeral systems.

C. Practice Zone

Olympiad-style puzzles for pattern discovery + number construction.

# Code Implementation
Below is the actual Python code that implements the core logic of your assignment.


# ------------------------
# Roman Numeral Converter
# ------------------------

roman_map = {
    'M': 1000, 'CM': 900, 'D': 500, 'CD': 400,
    'C': 100, 'XC': 90, 'L': 50, 'XL': 40,
    'X': 10, 'IX': 9, 'V': 5, 'IV': 4, 'I': 1
}

def int_to_roman(num):
    result = ""
    for symbol, value in roman_map.items():
        while num >= value:
            result += symbol
            num -= value
    return result


def roman_to_int(s):
    i, result = 0, 0
    while i < len(s):
        if i+1 < len(s) and s[i:i+2] in roman_map:
            result += roman_map[s[i:i+2]]
            i += 2
        else:
            result += roman_map[s[i]]
            i += 1
    return result


# Demo
print("Roman for 58 =", int_to_roman(58))
print("Arabic for LVIII =", roman_to_int("LVIII"))


# ------------------------
# Mayan Numeral Converter
# ------------------------

def mayan_digit(n):
    bars = n // 5
    dots = n % 5
    return bars * "-----\n" + dots * "• "


def int_to_mayan(num):
    levels = []
    while num > 0:
        levels.append(num % 20)
        num //= 20
    
    mayan_representation = ""
    for digit in reversed(levels):
        mayan_representation += mayan_digit(digit) + "\n---\n"
    return mayan_representation


# Demo
print("Mayan for 27:\n")
print(int_to_mayan(27))




# ------------------------
# Yoruba Numeral Constructor
# ------------------------

yoruba_numbers = {
    0: "odo",
    1: "ọ̀kan",
    2: "méjì",
    3: "mẹ́ta",
    4: "mẹ́rin",
    5: "márùn",
    10: "mẹ́wàá",
    20: "ogún"
}

def yoruba_number(n):
    if n in yoruba_numbers:
        return yoruba_numbers[n]
    if n > 20:
        return f"ogún lé {yoruba_numbers[n-20]}"
    if 10 < n < 20:
        return f"mẹ́wàá lé {yoruba_numbers[n-10]}"
    return "Number not implemented"


# Demo
print("Yoruba for 21 =", yoruba_number(21))





# ------------------------
# Pattern Puzzle Generator
# ------------------------

import random

def number_pattern_puzzle():
    sequence = [random.randint(1, 9)]

    # Generate pattern: +2 or ×2
    rule = random.choice(["+2", "*2"])

    for _ in range(4):
        if rule == "+2":
            sequence.append(sequence[-1] + 2)
        else:
            sequence.append(sequence[-1] * 2)

    print("Sequence:", sequence[:-1])
    print("Your task: Predict the next number.")
    print("Correct answer:", sequence[-1])

# Demo
number_pattern_puzzle()


#Conclusion

This project successfully demonstrates how mathematical and linguistic concepts can be blended into an interactive learning environment. The included Python code provides real functionality for numeral conversion and pattern-based analysis, laying the foundation for a full educational application.
