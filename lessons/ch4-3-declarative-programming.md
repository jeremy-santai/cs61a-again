# 4.3 Declarative Programming

This section explores SQL as a declarative programming language, contrasting it with procedural approaches. Rather than describing computational steps directly, "statements do not describe computations directly, but instead describe the desired result of some computation."

## 4.3.1 Tables

Tables, also called relations, organize data into fixed columns with named types. Each row represents a record with one value per column. SQL tables can be created and manipulated using select statements:

```sql
create table cities as
  select 38 as latitude, 122 as longitude, "Berkeley" as name union
  select 42, 71, "Cambridge" union
  select 45, 93, "Minneapolis";
```

Multiple tables combine through union operations.

## 4.3.2 Select Statements

Select statements define new tables by projecting existing ones:

```sql
select [column description] from [existing table name]
```

**Where Clauses** filter rows based on conditions:
```sql
select name from cities where latitude > 43;
```

**Order Clauses** sort results:
```sql
select distance, name from distances order by -distance;
```

## 4.3.3 Joins

Joins combine multiple tables by creating rows representing all combinations of input rows. Two tables with m and n rows produce m·n result rows:

```sql
select a.city, b.city, a.temp - b.temp
  from temps as a, temps as b where a.city < b.city;
```

Table aliases clarify column references when tables share names or join with themselves.

## 4.3.4 Interpreting SQL

A functional SQL interpreter requires three components: table representation, text parsing, and statement evaluation. The implementation uses Python's namedtuple for row representation.

The Select class processes queries through execution steps:
```python
class Select:
    def execute(self, env):
        from_rows = join(self.tables, env)
        filtered_rows = filter(self.filter, from_rows)
        ordered_rows = self.sort(filtered_rows)
        return map(self.make_row, ordered_rows)
```

This follows a join-filter-order-project pattern.

**Query Plans**: Different computation sequences produce identical results. Database systems optimize by selecting efficient procedures, potentially yielding substantial performance improvements for large tables.

## 4.3.5 Recursive Select Statements

The with clause generates intermediate tables used in computations:

```sql
with ints(n) as (
  select 5 union
  select n+1 from ints where n < 15
)
select n, n*n from ints where n % 2 = 1;
```

Recursive cases define output rows based on other output rows. Multiple tables can appear in a single with clause, separated by commas.

String concatenation using || enables sentence construction:
```sql
select subject.phrase || " chased " || object.phrase
  from nouns as subject, nouns as object
  where subject.phrase != object.phrase;
```

## 4.3.6 Aggregation and Grouping

Aggregate functions (max, min, count, sum) compute values across multiple rows:

```sql
select max(legs) from animals;
select sum(weight) from animals;
```

The distinct keyword eliminates duplicates in aggregation. The special count(*) counts rows.

**Group By and Having** partition rows into groups and filter them:

```sql
select legs, max(weight) from animals group by legs;
```

The having clause filters groups based on aggregate functions, while where clauses filter individual rows before aggregation for optimal performance.


---

## Same Chapter

- [Ch4 1 Introduction](ch4-1-introduction.md)
- [Ch4 2 Implicit Sequences](ch4-2-implicit-sequences.md)
- [Ch4 4 Logic Programming](ch4-4-logic-programming.md)
- [Ch4 5 Unification](ch4-5-unification.md)
- [Ch4 6 Distributed Computing](ch4-6-distributed-computing.md)
- [Ch4 7 Distributed Data Processing](ch4-7-distributed-data-processing.md)
- [Ch4 8 Parallel Computing](ch4-8-parallel-computing.md)
