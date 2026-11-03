# Python Units 1 & 3 Practical Test — Set A

Cleaned Python solutions for the questions. Run each code block separately. Question 2 asks for input, so enter the sample values when prompted.

## Section A — Fundamentals

### Q1. Print, escape characters, and multiple assignment

```python
print("Python", "Fundamentals", "Test", sep=" | ", end="!\n")

name, city, year = "Asha", "Surat", 2026
print(f"Name:\t{name}\nCity:\t{city}")
print(f'She said "It\'s {year}"')

a, b = 10, 20
a, b = b, a
print(a, b)
```

### Q2. `input()` and type conversion

```python
item = input("Enter item name: ")
price = float(input("Enter price: "))
raw_qty = input("Enter quantity: ")
print(type(raw_qty))
quantity = int(raw_qty)
print(type(quantity))

amount = price * quantity
print(f"Total for {item}: {amount:.2f}")

try:
    int("25.5")
except ValueError:
    print("ValueError")

try:
    "25" + 5
except TypeError:
    print("TypeError")

print(int(float("25.5")), int(-9.9), -9.9 // 1)
```

### Q3. Variables and data types

```python
vals = [42, 3.5, "Python", True, None]
print([type(v).__name__ for v in vals])

x = 10
x = "ten"
print(type(x).__name__)

print(0.1 + 0.2 == 0.3, round(0.1 + 0.2, 2))
print(True == 1, True + True)
print([bool(v) for v in [0, "", None, [], "False", 5]])
print(isinstance(25, (int, float)))
```

## Section B — Operators

### Q4. Arithmetic operators and precedence

```python
a, b = 17, 5
print(a // b, a % b, -a // b, -a % b)
print((-a // b) * b + (-a % b) == -a)
print(2 + 3 * 4 ** 2 // 5, 2 ** 3 ** 2, 7 // -2)
print(type(10 / 2).__name__, type(10 // 2).__name__)

price, quantity, tax_rate = 250, 3, 0.18
subtotal = price * quantity
tax = subtotal * tax_rate
total = subtotal + tax
print(f"Subtotal: {subtotal}  Tax: {tax:.2f}  Total: {total:.2f}")
```

### Q5. Comparison, logical, and assignment operators

```python
age = 25
has_id = True
has_guardian = False

print(18 <= age <= 60)
can_enter = (age >= 18 and has_id) or has_guardian
print(can_enter)
print("Hello" and "World", "" or "Guest", not 10)

user = ""
print(user or "Guest")

score = 10
score += 5
score *= 2
score //= 4
score **= 2
print(score)
```

## Section C — Strings

### Q6. Indexing, slicing, and immutability

```python
word = "Fundamentals"
print(word[0], word[-1], len(word))
print(word[:3], word[3:], word[::-1], word[::2])

try:
    word[0] = "X"
except TypeError:
    print("TypeError")

try:
    print(word[50])
except IndexError:
    print("IndexError")

print("X" + word[1:])
```

### Q7. Cleaning text with string methods

```python
raw = " pRiYa deSai , Surat , priya@mail.com "
clean = raw.strip()
parts = [part.strip() for part in clean.split(",")]
print(parts)

name, city, email = parts
print(name.title(), city.upper(), email.lower(), sep=" | ")
print(email.endswith(".com"), email.startswith("priya"), email.find("@"), email.find("#"))

try:
    email.index("#")
except ValueError:
    print("ValueError")

print(city.replace("a", "@"))
print(raw.lstrip() == clean, raw.rstrip() == clean)
```

### Q8. String formatting

```python
customer = "Rahul"
item = "Laptop bag"
price = 1450
qty = 2
disc = 0.125
total = price * qty * (1 - disc)

print(f"""
==================
RECEIPT
==================
Customer: {customer}
Item: {item} x {qty}
Discount: {disc:.1%}
Total: Rs.{total:.2f}
==================""")

print("{} bought {} item(s)".format(customer, qty))
print("{customer} paid {total:.1f}".format(customer=customer, total=total))
print("%s bought %d item(s) for %.2f" % (customer, qty, total))
```

## Section D — Lists and Tuples

### Q9. Lists

```python
items = ["Amit", "Priya", "Rahul", "Sneha"]
items.append("Vikram")
items.extend(["Neha", "Karan"])
items.insert(1, "Zoya")
items.remove("Rahul")

last = items.pop()
items[0] = "Aman"
print(items)
print(last, len(items))

list1 = ["a", "b"]
list1.append(["c", "d"])
list2 = ["a", "b"]
list2.extend(["c", "d"])
print(list1, len(list1))
print(list2, len(list2))

try:
    print(items[50])
except IndexError:
    print("IndexError")

try:
    items.remove("Nobody")
except ValueError:
    print("ValueError")

try:
    [].pop()
except IndexError:
    print("IndexError")
```

### Q10. Tuples

```python
t = (10, 20, 20, 30, 40)
print(t[0], t[-1], t[1:3])
print(t.count(20), t.index(30))

x = (5)
y = (5,)
print(type(x).__name__, type(y).__name__)

try:
    t[0] = "yellow"
except TypeError:
    print("TypeError")

try:
    t.append(99)
except AttributeError:
    print("AttributeError")

try:
    t.index(1000)
except ValueError:
    print("ValueError")

data = ([1, 2, 3], "hello")
data[0].append(4)
print(data)

new_t = ("yellow",) + t[1:]
print(new_t)
```

## Section E — Sets and Dictionaries

### Q11. Sets

```python
nums = [4, 7, 4, 9, 7, 7, 2, 9]
s = set(nums)
print(sorted(s), len(nums), len(s))

s.add(11)
s.discard(99)
s.remove(2)
print(sorted(s))

try:
    s.remove(1000)
except KeyError:
    print("KeyError")

s1 = {1, 2, 3, 4, 5}
s2 = {4, 5, 6, 7}
print(sorted(s1 | s2), sorted(s1 & s2))
print(sorted(s1 - s2), sorted(s2 - s1), sorted(s1 ^ s2))
print(type({}).__name__, type(set()).__name__)
print(9 in s, 9 not in s1)

try:
    bad_set = {[1, 2], [3, 4]}
except TypeError:
    print("TypeError")
```

### Q12. Dictionaries

```python
d = {
    "name": "Rahul",
    "age": 20,
    "course": "Python",
    "marks": [80, 85, 90],
    "address": {"city": "Ahmedabad", "country": "India"},
}

print(d["name"], d.get("phone"), d.get("phone", "Not found"))
d["age"] = 21
d["grade"] = "A"
print(d["age"], len(d))

removed = d.pop("course")
print(removed, d.pop("zzz", "none"))
del d["marks"]
print(list(d.keys()))

print(d["address"]["city"])
print("name" in d, "Rahul" in d, "Rahul" in d.values())

for key, value in d.items():
    print(key, "->", value)

try:
    print(d["email"])
except KeyError:
    print("KeyError")

dup = {"name": "first", "x": 1, "name": "second"}
print(dup)
```

## Section F — Integrated Mini Program

### Q13. Student marks report

```python
records = [
    ("Asha", "Python", 78),
    ("Asha", "SQL", 82),
    ("Asha", "Excel", 71),
    ("Ravi", "Python", 55),
    ("Ravi", "SQL", 61),
    ("Ravi", "Excel", 49),
    ("Meena", "Python", 92),
    ("Meena", "SQL", 88),
    ("Meena", "Excel", 95),
    ("Karan", "Python", 64),
    ("Karan", "SQL", 70),
    ("Karan", "Excel", 58),
]

courses = set()
scores = {}
for who, course, marks in records:
    courses.add(course)
    if who not in scores:
        scores[who] = []
    scores[who].append(marks)
print(sorted(courses))

averages = {}
for who, marks_list in scores.items():
    avg = sum(marks_list) / len(marks_list)
    averages[who] = avg
    if avg >= 75:
        grade = "A"
    elif avg >= 60:
        grade = "B"
    else:
        grade = "C"
    print(f"{who:<8} avg={avg:.1f} grade={grade}")

top_student = max(averages, key=averages.get)
overall_avg = sum(averages.values()) / len(averages)
print(f"Top: {top_student} | Overall average: {overall_avg:.2f}")

above_overall = [who for who, avg in averages.items() if avg > overall_avg]
print("Above overall:", above_overall)

all_marks = [marks for _, _, marks in records]
extremes = (min(all_marks), max(all_marks))
print(extremes, type(extremes).__name__)

# A set stores unique courses, a dictionary maps students to data, lists hold marks, and a tuple stores the two extremes.
```

