# ExpNo:10 Implementation of Classical Planning Algorithm

```
Name         : Shivaram M.
Register No. : 212223040195
```

# Algorithm or Steps Involved:
<ol>
  <li>Define the initial state</li>
  <li>Define the goal state</li>
  <li>Define the actions</li>
  <li>Find a <b>plan</b> to reach the goal state</li>
  <li>Print the plan</li>
</ol>

# Example - 1
```
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_Table': {'precondition': {'A': 'Table', 'B': 'B'}, 'effect': {'B': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B']
```
# Example - 2
```
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_C': {'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'}, 'effect': {'B': 'C'}},
    'move_C_to_Table': {'precondition': {'A': 'B', 'B': 'C', 'C': 'C'}, 'effect': {'C': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B', 'move_B_to_C']
```

# Please Prepare Solution or Definition For the method find_plan(initial_state, goal_state, actions)
## Program

```
state = {"At(Home)", "Have(Money)"}
goal = {"Have(Milk)", "Have(Bread)"}

actions = {
    "GoTo(Store)": {
        "pre": {"At(Home)"},
        "add": {"At(Store)"},
        "del": {"At(Home)"}
    },
    "Buy(Milk)": {
        "pre": {"At(Store)", "Have(Money)"},
        "add": {"Have(Milk)"},
        "del": set()
    },
    "Buy(Bread)": {
        "pre": {"At(Store)", "Have(Money)"},
        "add": {"Have(Bread)"},
        "del": set()
    },
    "Return(Home)": {
        "pre": {"At(Store)"},
        "add": {"At(Home)"},
        "del": {"At(Store)"}
    }
}

plan = []
while not goal.issubset(state):
    for act, vals in actions.items():
        if vals["pre"].issubset(state):
            if any(g not in state for g in vals["add"]):
                plan.append(act)
                state = (state - vals["del"]) | vals["add"]
                print(f"Applied {act} → State: {state}")
                break
    else:
        print("No applicable actions remaining — goal not reachable.")
        break

print("\nFinal Plan:")
for i, p in enumerate(plan, 1):
    print(f"{i}. {p}")
```
## Output
<img width="1605" height="960" alt="Screenshot 2025-10-23 at 2 14 51 PM" src="https://github.com/user-attachments/assets/9c8ccd5b-d4cd-4109-ad28-a5a2cb8e9e8c" />
<img width="1206" height="301" alt="output" src="https://github.com/user-attachments/assets/3ed46c9a-ebda-4b27-9115-9f4fb3990b71" />

## Result
A Classic planning algorithm has been implemented successfully in python.
