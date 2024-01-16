## NL2SQL Project

This project presents **sqlcoder-34b-alpha** performance, a Text-2-SQL model for instruction-based generation of SQL code from natural language queries. In this repository I release the training thanks to different prompt strategy of **SQLCODER:15B** language model and the **34B** version. I also use **LLama2** for several examples.

This project has been trained on a server with 380GB of RAM and is powered by 2 NVIDIA Tesla V100 GPUs, each with 32GB of memory.

### Examples from sqlcoder-34b-alpha

#### Prompt:

```
"Below is an instruction that describes a task, paired with an input that provides further context. Write a response that appropriately completes the request.

### Instruction:\nFor model volvo, how many cylinders does the car with the least accelerate have?

### Input:\nCREATE TABLE CARS_DATA (cylinders VARCHAR, Id VARCHAR, accelerate VARCHAR); CREATE TABLE CAR_NAMES (MakeId VARCHAR, Model VARCHAR)

### Response:"
```
#### Output:

```sql
SELECT T2.cylinders
FROM CAR_NAMES AS T1 JOIN CARS_DATA AS T2 ON T1.MakeId = T2.MakeId
WHERE T1.Model = "volvo"
ORDER BY T2.accelerate LIMIT 1
```
