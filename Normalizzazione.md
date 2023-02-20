---
tag: computer-science
subjects: [ dbms ]
---

# Prima forma
## Definizione
> [!CHECK]
> - Nessuna riga duplicata
> - Valore minimo per cella
> - Valore atomico per cella

## Esempio
| Consumer   | Order                    |
| ---------- | ------------------------ |
| Bob Jones  | Burger, Fries, Coke      |
| Fred Jones | Nuggets, Fries, Lemonade |
| Bob Jones  | Burger, Fries, Coke      |

### Nessuna riga duplicata 
| Order Id | Consumer   | Order                    |
| ------- | ---------- | ------------------------ |
| 1       | Bob Jones  | Burger, Fries, Coke      |
| 2       | Fred Jones | Nuggets, Fries, Lemonade |
| 3       | Bob Jones  | Burger, Fries, Coke      |

### Valore minimo per cella
| Order Id | Consumer   | Order    |
| ------- | ---------- | -------- |
| 1       | Bob Jones  | Burger   |
| 1       | Bob Jones  | Fries    |
| 1       | Bob Jones  | Coke     |
| 2       | Fred Jones | Nuggets  |
| 2       | Fred Jones | Fries    |
| 2       | Fred Jones | Lemonade |
| 3       | Bob Jones  | Burger   |
| 3       | Bob Jones  | Fries    |
| 3       | Bob Jones  | Coke     |

### Valore atomico per cella
| Order Id | Name | Surname | Order    |
| ------- | ---- | -------- | -------- |
| 1       | Bob  | Jones    | Burger   |
| 1       | Bob  | Jones    | Fries    |
| 1       | Bob  | Jones    | Coke     |
| 2       | Fred | Jones    | Nuggets  |
| 2       | Fred | Jones    | Fries    |
| 2       | Fred | Jones    | Lemonade |
| 3       | Bob  | Jones    | Burger   |
| 3       | Bob  | Jones    | Fries    |
| 3       | Bob  | Jones    | Coke     |

# Seconda forma
## Definizione
> [!CHECK]
> - No dipendenza parziale

## Esempio
| Student Id | Course Id | Course Fee |
| ---------- | --------- | ---------- |
| 1          | 1         | 100        |
| 1          | 2         | 200        |
| 2          | 2         | 200        |

### No dipendenza parziale
#### Tabella Student Courses
| Student Id | Course Id |
| ---------- | --------- |
| 1          | 1         |
| 1          | 2         |
| 2          | 2         |

#### Tabella Courses Fees
| Course Id | Course Fee |
| --------- | ---------- |
| 1         | 100        |
| 2         | 200        | 


# Terza forma
## Definizione
> [!CHECK]
> - Dipendenze non transitive

## Esempio
| Tournament      | Year | Winner    | Winners' Birthday |
| --------------- | ---- | --------- | ----------------- |
| Grey Tournament | 2050 | Joe Biden | 20-10-2030        |
| Attack on Tesla | 2030 | Xi Xining | Ieri              |

### Dipendenze non transitive
#### Tournament Results
|Tournament      | Year | Winner    |
| --------------- | ---- | --------- |
| Grey Tournament | 2050 | Joe Biden |
| Attack on Tesla | 2030 | Xi Xining |
 
#### Winners Data
| Winner    | Winners' Birthday |
| --------- | ----------------- |
| Joe Biden | 20-10-2030        |
| Xi Xining | Ieri              |
