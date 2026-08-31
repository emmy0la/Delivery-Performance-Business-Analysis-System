# GIFT II: Delivery Status Management System

## Python-Based Logistics Tracking and Business Analysis Project

A Python-based delivery management system that validates delivery records, applies operational business rules, processes multiple deliveries, evaluates delivery performance, assigns priorities, recommends actions, and generates business-focused reports.

Built as part of the **SmartBizCrux Technologies Python Study Group GIFT II (Group Integrated Functional Task)** project.

> *This project was completed in a team-learning environment. Each team member developed and tested an individual solution while working within the same project requirements.*

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Business Scenario](#business-scenario)
3. [Business Problem](#business-problem)
4. [Project Objectives](#project-objectives)
5. [Solution Workflow](#solution-workflow)
6. [Delivery Business Rules](#delivery-business-rules)
7. [Core Functions](#core-functions)
8. [Sample Delivery Report](#sample-delivery-report)
9. [Bonus Analysis Results](#bonus-analysis-results)
10. [Summary Report](#summary-report)
11. [Testing Strategy](#testing-strategy)
12. [Python Concepts Demonstrated](#python-concepts-demonstrated)
13. [Project Structure](#project-structure)
14. [How to Run](#how-to-run)
15. [What This Project Demonstrates](#what-this-project-demonstrates)
16. [Key Learning Outcome](#key-learning-outcome)
17. [Acknowledgement](#acknowledgement)
18. [Author](#author)

---

## Project Overview

Delivery operations generate large amounts of information every day. If delivery records are not properly validated and processed, businesses can struggle to identify delays, prioritize critical deliveries, and monitor operational performance.

This project demonstrates how Python can be used to transform raw delivery information into structured operational insights.

The system processes fictional logistics records and answers practical questions such as:

- Which deliveries are on time?
- Which deliveries are delayed?
- Which deliveries require urgent attention?
- How many deliveries have been completed or cancelled?
- Which delivery has remained open the longest?
- What percentage of deliveries are currently on time?

The project moves beyond writing individual Python statements and demonstrates how programming concepts can be combined to solve a business problem.

---

## Business Scenario

The fictional company, **SmartLogistics**, needs a simple system for monitoring customer deliveries.

The logistics team receives information such as:

| Field | Example |
|-------|---------|
| Delivery ID | DEL001 |
| Customer Name | Daniel Okafor |
| Delivery Location | Lagos |
| Delivery Status | In Transit |
| Days Since Order | 4 |
| Expected Delivery Days | 5 |
| Package Weight | 3.5 kg |
| Delivery Attempts | 1 |

The system must validate the information, apply business rules, classify delivery performance, assign priority, recommend an action, and generate a structured report.

---

## Business Problem

Poorly processed delivery data can result in:

- Incorrect delivery classifications
- Missed delays
- Poor prioritization
- Incorrect operational reporting
- Difficulty identifying deliveries requiring intervention
- Inconsistent decision-making

The objective was therefore to build a **reusable Python solution** that converts delivery records into meaningful operational information.

---

## Project Objectives

The system was designed to:

1. Store delivery information
2. Validate delivery records
3. Process individual delivery records
4. Determine delivery performance
5. Assign delivery priority
6. Recommend operational actions
7. Process multiple delivery records
8. Demonstrate `for` and `while` loops
9. Demonstrate local and global variable scope
10. Generate delivery reports
11. Perform additional business analysis
12. Summarize the results for decision-making

---

## Solution Workflow

Raw Delivery Data
↓
Data Validation
↓
Individual Delivery Processing
↓
Business Rule Evaluation
↓
Multiple Delivery Processing
↓
Performance Analysis
↓
Priority Assignment
↓
Recommended Action
↓
Delivery Report
↓
Bonus Analysis
↓
Summary Report



The solution separates different responsibilities into reusable functions. This makes the code easier to understand, test, debug, and reuse.

---

## Running Code

The following screenshots show the system successfully running and generating delivery reports.

### Delivery Report Output

![Delivery Report](screenshots/delivery_report.png)

*Figure 1: Sample delivery report showing validated delivery information, performance analysis, priority assignment, and recommended action.*

---

## Delivery Business Rules

### Delivery Statuses

| Status | Meaning |
|--------|---------|
| Order Received | Order has been received but processing has not started |
| Processing | Order is being prepared for dispatch |
| Dispatched | Package has left the warehouse or seller |
| In Transit | Package is moving toward the customer |
| Delivered | Package has reached the customer |
| Delayed | Expected delivery period has passed |
| Cancelled | Delivery has been cancelled |

### Delivery Performance Rules

| Condition | Performance |
|-----------|-------------|
| Delivered | Completed |
| Cancelled | Cancelled |
| Days Since Order <= Expected Days | On Time |
| Days Since Order > Expected Days | Delayed |

### Priority Rules

| Condition | Priority |
|-----------|----------|
| Delayed + 2 or more attempts | Urgent |
| Delayed + at least 1 attempt | High |
| On Time + at least 1 attempt | Normal |
| On Time + 0 attempts | Low |

### Recommended Actions

| Priority | Recommended Action |
|----------|-------------------|
| Urgent | Contact Customer and Escalate Delivery |
| High | Investigate Delivery Delay |
| Normal | Continue Delivery Process |
| Low | Monitor Delivery |

---

## Core Functions

### 1. Delivery Performance

```python
def check_delivery_performance(
    delivery_status,
    days_since_order,
    expected_delivery_days
):
    if delivery_status == "Cancelled":
        return "Cancelled"
    elif delivery_status == "Delivered":
        return "Completed"
    elif days_since_order <= expected_delivery_days:
        return "On Time"
    else:
        return "Delayed"
```

### 2. Delivery Priority

```python
def determine_delivery_priority(
    delivery_performance,
    delivery_attempts
):
    if delivery_performance == "Delayed" and delivery_attempts >= 2:
        return "Urgent"
    elif delivery_performance == "Delayed" and delivery_attempts >= 1:
        return "High"
    elif delivery_performance == "On Time" and delivery_attempts >= 1:
        return "Normal"
    else:
        return "Low"
```

### 3. Recommended Action

```python
def recommend_delivery_action(delivery_priority):
    if delivery_priority == "Urgent":
        return "Contact Customer and Escalate Delivery"
    elif delivery_priority == "High":
        return "Investigate Delivery Delay"
    elif delivery_priority == "Normal":
        return "Continue Delivery Process"
    else:
        return "Monitor Delivery"
```

### 4. Delivery Validation

| Field                  | Validation Rule                    |
|------------------------|------------------------------------|
| Delivery ID            | Cannot be empty                    |
| Customer Name          | Cannot be empty                    |
| Delivery Location      | Cannot be empty                    |
| Delivery Status        | Must be an accepted status         |
| Days Since Order       | Must be >= 0                       |
| Expected Delivery Days | Must be > 0                        |
| Package Weight         | Must be > 0                        |
| Delivery Attempts      | Must be >= 0                       |

The function returns VALID or INVALID.

## Sample Delivery Record

The initial test record contains:

Delivery ID: DEL001
Customer Name: Daniel Okafor
Delivery Location: Lagos
Delivery Status: In Transit
Days Since Order: 4
Expected Delivery Days: 5
Package Weight: 3.5 kg
Delivery Attempts: 1
