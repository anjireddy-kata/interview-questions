# Q1: Agent and Call Assignment
Write a program to assign the calls to the available agents. Agents will have a skill level based on their proficiency. The call also contains the priority. 
The highest priority calls required to be assigned to the agents.

### Agent 
| Agent Code  | Skill Level  |
|---|---|
| A1  |  1 |
| A2  |  4 |
| A3  |  5 |

### Calls 
| Call  | Priority  |
|---|---|
| C1  |  10 |
| C2  |  4 |
| C3  |  5 |

Ans: Priority Queues with a Simple Assignment Algorithm.

# Q2: Write a program to store the menu options and play the selected menu option. A menu option has to be extracted at millisecond latency, and a menu may have max of two additional options.

Ans: Binary Search Tree 

# Q3 : Write a program to identify potential fraudulent callers by matching phone numbers against known blacklists.
Ans: Hashmap

# Q4: Given an expression containing numeric operands with addition and subtraction operators, evaluate it. Assume that the expression is valid and may contain sub-expressions enclosed in opening and closing braces.
Input: s = -10+(5+(12+8)-2)+1 Output: 14

# Q5: Implement a simple spell checker with auto completion of words
Ans: Tries required to be used here.

# Q6: Find total ways to reach the n’th stair from the bottom. 
Given a staircase, find the total number of ways to reach the n'th stair from the bottom of the stair when a person can only climb either 1 or 2 or 3 stairs at a time.

Total ways to reach the 3rd stair are 4

1 step + 1 step + 1 step
1 step + 2 steps 
2 steps + 1 step 
3 steps

# Q7: implementation of the Round Robin call assignment algorithm

```
class Agent:
    def __init__(self, name):
        self.name = name

class Task:
    def __init__(self, name):
        self.name = name

class RoundRobinScheduler:
    def __init__(self, agents, time_quantum):
        self.agents = agents
        self.time_quantum = time_quantum
        self.agent_queue = agents.copy()
        self.task_queue = []

    def enqueue_task(self, task):
        self.task_queue.append(task)

    def schedule_tasks(self):
        while self.task_queue:
            if not self.agent_queue:
                print("All agents are busy. Waiting for next time quantum.")
                continue
            
            current_agent = self.agent_queue.pop(0)
            current_task = self.task_queue.pop(0)
            
            print(f"Agent {current_agent.name} is processing Task {current_task.name}")
            
            if len(self.task_queue) > 0:
                self.agent_queue.append(current_agent)
            
            if len(self.agent_queue) < len(self.agents):
                self.agent_queue.append(self.agents[len(self.agent_queue)])

if __name__ == "__main__":
    agents = [Agent("A"), Agent("B"), Agent("C")]
    scheduler = RoundRobinScheduler(agents, time_quantum=2)

    tasks = [Task("T1"), Task("T2"), Task("T3"), Task("T4")]
    for task in tasks:
        scheduler.enqueue_task(task)
    
    scheduler.schedule_tasks()

```

# Q8: BST: Employed to organize and search for loan records based on customer IDs or loan amounts

# Q9: Hashmaps: store and retrieve customer account information quickly based on account numbers or customer IDs.

# Q10: Tries:  Utilized to quickly search for potentially fraudulent patterns in large datasets.

# Q11: Graphs: Used to model and analyze the relationships between different accounts and transactions to identify suspicious patterns.

# Q12: Heap: Used to prioritize and manage loan approval requests based on factors such as credit score and loan amount.

# Q13: Quadtree / Octree: Utilized for efficient spatial indexing of ATM and branch locations, allowing for fast retrieval based on geographic proximity.

# Q 14: Graphs: Used to model relationships between assets and to optimize portfolio diversification.
# Q15: Decision Trees: Utilized to build credit scoring models that assess the creditworthiness of applicants based on various factors.

# Q16: Linked Lists: Employed to maintain a chronological record of account transactions and generate account statements.
