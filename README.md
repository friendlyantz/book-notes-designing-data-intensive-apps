* [Web version](https://friendlyantz.github.io/book-notes-designing-data-intensive-apps/)
{:toc}

# Notes on Book Designing Data-Intensive Applications

I am starting the above book and will be going through 1 chapter a week 
If anybody wants to discuss / draw diagrams / write some markdown notes, on a weekly basis for 60mins - get amogst.

## WEEKLY GOAL

- to recap and structurise the knowledge that was discovered in a chapter
- explain a chapter like 'I am 5 years old'
- draw diagrams
- take notes of important concepts
You have to actively contribute / participate

## Format

I was thinking about pairing format with the following setup

- 1 driver in a hot seat drawing / coding / writing notes - not asking questions
- 1 co-pilot who tells the driver what to do
- reest of the club commetee discussing with co-pilot what to note, record as an important takeaway / summary

## ALTERNATIVE:

- just to watch this BookCLub playlist(1-2hrs/chapter) -> https://www.youtube.com/watch?v=JqDAEH_2t6M&list=PLmp4AHm0u1g0Adn8HwWIe-G_xTn_jqOvf
- AND this summray of each chapter (15mins/chapter) -> https://www.youtube.com/watch?v=PdtlXdse7pw&list=PL4KdJM8LzAMecwInbBK5GJ3Anz-ts75RQ

## PS

This is a fantastic and very easy read I find.

---

# Part I: Foundations of Data Systems

--- 

# Ch 1: Relible, Scalable and Maintanable Apps

--- 

### Data-intensive vs Compute-Intensive
> CPU is rarely a limit these days. 
> usually it is:
> 	- amount of data
> 	- complexity of data
> 	- speed at which it is changing

---

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/c3749b37-7609-4ab9-b301-a3fca7ab9cbd)

---

### Thinking about Data Systems
- Boundaries between data systems(DBs, Caches, queues) are becoming blurred

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/8b78b6a8-fd07-40af-ba77-1bcec699255d)

---
 ![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/c3813031-48a2-4d5e-ab69-819aad5fab62)
---

- role of Software Engineer now also includes DataSystem designer (Arch?)
	- We have to address:
		- keeping data correct and complete during storm
		- providing consistent performance to clients, when sys is degraded
		- how to scale to handle increased load
		- what is a good API for this service?
	- factors:
		- team skill / exp
		- legacy sys
		- time-pressure
		- risk appetite
		- regulatory
		- etc etc
	- Note: what is legacy? assumptions/conventions w/o data

---

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/196bac3a-4fea-4371-ae52-71a51182f043)

## Reliability
- fault-tolerant (aka resilient)
- fault vs failure
- Define scope of faults - we can't tackle them all (i.e diff region? alien invasion?)
- Essentially we build reliable sys from unreliable parts (i.e. my Mec*ano kit)
- we need to deliberatly trigger faults (i.e. kill processe w/o warning). Many bugs are due to poor error handling
- Netflix Chaos Monkey
- we prever tolerating faults over preventing faults

---

### Hardware Faults
-1st response: add redundancy - as it is well understood
	until recently hardware redundancy was sufficient, but it changes with the rise of flexibility and elasticity priorities, over single machine reliability
	Hence the move is towards systems that can tolerate the loss of machines, by using software fault-tolerance techniques (in preference OR in addition to hardware redundancy)
 
### Software Errors
### Human Error

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/31e08bf2-6550-4e52-bfc9-2e469b1c4852)

## Scalability

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/0c4d021a-85d4-4012-8f2d-41b8a3976c76)

## Maintainability

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/382f7bda-fcdd-43b4-9544-29db78ca0cf6)
##### Simplicity - managing complexity
- Explosion of the state space
	accidental complexity vs essential complexity
##### Evolvability - making changes easy

---

> Your solution will be custom

# Ch 2: Data Models and Query lang-s

### Abstraction

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/829e820c-d544-47de-b7be-84256ff54c60)
![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/4e4b0d9d-ad5c-4fcc-902e-3d2382d8d483)

### Relational Model

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/833609bd-b0d3-4e14-ae43-d56b9cbe5224)

### Document based Model

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/d3304e6b-8ba8-4a6b-b633-55d58b45573f)

### Graph model

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/0620b913-b7a0-4af4-8909-6e5e0efc5720)
![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/a02a3a7a-793a-411c-9903-69fd5ca63c8d)

---

**Data Storage** and **Data Retrieval** - Data model and it's quering go hand-in-hand

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/59657b85-580a-4a01-bb98-024734b130f7)
![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/07a93a33-d1b7-44be-9b8d-b6637922fec6)

## Ch 3: Storage and Retrieval

### Which DB to use?

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/b3455ff3-42e6-450a-819a-ce5edc4cd7c5)
![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/de80ac88-b499-46cd-af09-8a718ccbb684)

### DB Indexing

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/e8744b3d-5485-4ea7-b869-817f1f6feecf)

#### Extra on DB indexing

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/52d50a5b-6002-417f-a5c7-13170ee35906)

### LSM-Trees - Log Short Merge and SSTables (Sorted String)

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/0c5937b2-c89b-4564-87ae-6ae10fa2f9db)
![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/db580ed1-d2c1-4d95-a312-3045309e8148)

### B-Trees Index

![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/b2b28fd5-2dc6-4c49-894f-5886eb5dc3a4)
![image](https://github.com/friendlyantz/friendlyantz/assets/70934030/b8b07f34-56ca-46bc-b09b-3b4b1104dbcf)

# Ch 4: Encoding and Evolution

# Part II: Distributed Data

# Ch 5: Replication

# Ch 6: Partitioning
