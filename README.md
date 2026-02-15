# Gym Management System: ER Model Design

## 📝 Project Scenario
A large gym chain currently uses a manual, card-based system to manage members and sessions. This has led to human errors, such as members registering for overlapping sessions or sessions exceeding capacity. This project proposes a **Conceptual Data Model** to digitize their operations.

---

## 🏗️ The Entity-Relationship Model

### 1. Entities & Attributes
The system is built around four primary entities:

* **Gymnasium**: 
    * `Name` (Primary Key/Identifier)
    * `Address`
    * `Phone Number`
* **Member**: 
    * `Member_ID` (Primary Key/Identifier)
    * `Last Name`, `First Name`
    * `Address`
    * `Date of Birth`
    * `Gender`
* **Session**: 
    * `Session_ID` (Primary Key/Identifier)
    * `Type of Sport`
    * `Schedule`
    * `Max_Capacity` (Constrained to 20)
* **Coach**: 
    * `Coach_ID` (Primary Key/Identifier)
    * `Last Name`, `First Name`
    * `Age`
    * `Specialty`

---

### 2. Relationships & Cardinalities

| Relationship | Description | Cardinality |
| :--- | :--- | :--- |
| **Registration** | A Member registers at one Gymnasium; a Gymnasium hosts many Members. | **1:N** |
| **Attendance** | A Member can attend multiple Sessions; a Session can hold up to 20 Members. | **M:N** |
| **Instruction** | A Session is led by up to 2 Coaches; a Coach can lead multiple Sessions. | **M:N** |

---

## 📊 Logical Flow

1.  **Gymnasium (1)** ─── < Registers > ─── **(N) Member**
2.  **Member (M)** ─── < Attends > ─── **(N) Session**
3.  **Coach (M)** ─── < Leads > ─── **(N) Session**

---

## 💡 Proposed Solution
By implementing this model into an RDBMS (like SQL), the owner can solve existing issues through:
* **Validation Rules**: Automatically preventing a 21st member from joining a session.
* **Conflict Checking**: Ensuring a member's schedule does not overlap across different sport types.
* **Data Integrity**: Linking coaches to their specific specialties and assigned sessions.
