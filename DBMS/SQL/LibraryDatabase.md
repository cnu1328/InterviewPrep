# Library Database

<img width="900" alt="image" src="https://github.com/user-attachments/assets/97bac037-4e3c-48cf-af0d-bc6b13a78969">

BOOK
| Book_id | Title | Publisher_Name | Pub_Year |
|---------|------------------|----------------|----------|
| 1 | SQL Fundamentals | Pearson | 2010 |
| 2 | Data Structures | O'Reilly | 2012 |

PUBLISHER
| Name | Address | Phone |
|---------|-------------------|------------|
| Pearson | 123 Main St | 555-1234 |
| O'Reilly| 456 Market St | 555-5678 |

BOOK_AUTHORS
| Book_id | Author_Name |
|---------|----------------|
| 1 | John Doe |
| 2 | Jane Smith |
| 1 | Alice Johnson |

BOOK_COPIES
| Book_id | Branch_id | No_of_copies |
|---------|-----------|--------------|
| 1 | 101 | 5 |
| 2 | 101 | 3 |
| 1 | 102 | 4 |

LIBRARY_BRANCH
| Branch_id | Branch_Name | Address |
|-----------|-------------|--------------|
| 101 | Downtown | 789 Elm St |
| 102 | Uptown | 101 Maple St |

BOOK_LENDING
| Book_id | Branch_id | Card_No | Date_Out | Due_Date |
|---------|-----------|---------|-----------|-----------|
| 1 | 101 | 1001 | 2017-01-15| 2017-01-30|
| 2 | 102 | 1002 | 2017-02-01| 2017-02-15|
| 1 | 101 | 1001 | 2017-02-20| 2017-03-05|

## Easy Questions

1. **Retrieve all book titles from the BOOK table**

```sql

select Title from book;

```

| Title            |
| ---------------- |
| SQL Fundamentals |
| Data Structures  |

2. **2. List all publishers from the PUBLISHER table.**

```sql
select * from publisher;

```

3. **Find all authors from the BOOK_AUTHORS table.**

```sql

select disticnt author_name from authors;

```

4. **Get the total number of book copies in each branch.**

```sql

select branch_id, sum(num_of_copies) as Total_copies
from Book_Copies
group by branch_id;

```

| Branch_id | Total_Copies |
| --------- | ------------ |
| 101       | 8            |
| 102       | 4            |

## Medium Questions

5. **Retrieve the names of all branches where the book titled 'SQL Fundamentals' is available.**

```sql

select LB.branch_name
from Library_Branch LB
join Book_Copies BC
on BC.branch_id = LB.branch_id
join Books B
on BC.book_id = B.book_id
where B.title = 'SQL FUndamentals';

```

| Branch_Name |
| ----------- |
| Downtown    |
| Uptown      |

6. **List the details of all books borrowed in the month of January 2017.**

```sql

select * from Book_Lending
where BL.Date_Out between '2017-01-01' and '2017-01-31';

```

7. **Find the total number of books borrowed by each borrower (Card_No).**

```sql

select card_no, count(*) as Total_Borrowed
from Book_Lending
group by card_no;

```

| Card_No | Total_Borrowed |
| ------- | -------------- |
| 1001    | 2              |
| 1002    | 1              |

8. **Retrieve the details of books published by 'Pearson'**

```sql

select * from Books
where Publisher_name = 'Pearson';

```

| Book_id | Title            | Publisher_Name | Pub_Year |
| ------- | ---------------- | -------------- | -------- |
| 1       | SQL Fundamentals | Pearson        | 2010     |

## Hard Questions

9. **Find the details of branches that have both the books titled 'SQL Fundamentals' and 'Data Structures'.**

```sql

select LB.* from Library_Branch LB
where LB.branch_id IN (
    select BC.branch_id from Book_Copies BC
    join Book B
    on B.book_id = BC.book_id
    where B.Title IN ('SQL Fundamentals', 'Data Structures')
    group by BC.branch_id
    Having count(distinct B.Title) = 2
);

```

| Branch_id | Branch_Name | Address    |
| --------- | ----------- | ---------- |
| 101       | Downtown    | 789 Elm St |

10. **Retrieve book titles with the highest number of copies available branch-wise.**

```sql

select
    BC1.branch_id,
    LB.branch_name,
    B.title,
    BC1.no_of_copies
from Book_Copies BC1
join (
    select
        BC.branch_id,
        BC.book_id,
        BC.no_of_copies
    from Book_Copies BC
    where BC.no_of_copies = (
        Select max(no_of_copies)
        from Book_Copies
        where BC.branch_id = branch_id
    )
) BC2
on BC2.branch_id = BC1.branch_id and BC2.book_id = BC1.book_id
join Libary_Branch LB
on BC1.branch_id = LB.branch_id
join Book B
on BC1.book_id = B.book_id;

```

| Branch_id | Branch_Name | Title            | No_of_copies |
| --------- | ----------- | ---------------- | ------------ |
| 101       | Downtown    | SQL Fundamentals | 5            |
| 102       | Uptown      | Data Structures  | 4            |

11. **Display the publisher names whose books are not available in any branch.**

```sql

select P.name
from Publisher P
where not exists (
    select Book.book_id
    from Book B
    join Book_Copies BC
    on B.book_id = BC.book_id
    where B.publisher_name = P.name
);

```

| Name     |
| -------- |
| O'Reilly |

12. **Display the book names which are available only in 'Bangalore' but not in 'Mangalore'.**

```sql
-- First Query
select B.title
from Book B
where B.book_id IN (
    select BC.book_id
    from Book_Copies BC
    join Library_Branch LB
    on BC.branch_id = LB.branch_id
    where LB.branch_name = 'Bangalore'

) and B.book_id Not IN (
    select BC.book_id
    from Book_Copies BC
    join Library_Branch LB
    on BC.branch_id = LB.branch_id
    where LB.branch_name = 'Mangalore'
);

-- Second query - Optimized due to explicit joins and conditions

select B.Title
from Book B
join Book_Copies BC_Banglore
on BC_Banglore.book_id = B.book_Id
join Library_Branch LB_Banglore
on BC_Banglore.branch_id = LB_Banglore.branch_id and LB_Banglore.branch_name = "Bangalore"
where B.book_id not in (
    select B_Mang.book_id
    from Book B_Mang
    join Book_Copies BC_Mang
    on BC_Mang.book_id = B_Mang.book_id
    join Library_Branch LB_Mang
    on LB_Mang.branch_id = BC_Mang.branch_id and LB_Mang.branch_name = "Mangalore"
);

```

| Title            |
| ---------------- |
| SQL Fundamentals |

## More Questions (Various Difficulties)

13. **Retrieve the names of all authors who have written more than one book.**

```sql

select author_name
from Book_Authors
group by author_name
having count(book_Id) > 1;

```

| Author_Name |
| ----------- |
| John Doe    |

14. **Retrieve the titles and publication years of all books published before 2015.**

```sql

select title, pub_year
from Book
where pub_year < 2015;

```

| Title            | Pub_Year |
| ---------------- | -------- |
| SQL Fundamentals | 2010     |
| Data Structures  | 2012     |

15. **Find the details of the book that has been borrowed the most.**

```sql

select B.book_id, B.Title, count(BL.book_id) as Borrow_Count
from Book
join Book_Lending BL
on B.book_id = BL.book_id
group by B.book_id, B.Title
order by Borrow_Count desc
limit 1;

```

## Advanced Queries (Combining Multiple Concepts)

16. **Retrieve the names of all authors along with the titles of the books they have written.**

```sql

select BA.Author_name, B.Title
from Book_Author BA
join Book B
on B.book_id = BA.book_id;

```

17. **Find the average number of copies of books per branch.**

```sql

select branch_id, AVG(no_of_copies)
from Book_Copies
group by branch_id;

```

18. **Retrieve the names and addresses of branches that have more than 10 copies of any book.**

```sql

select LB.branch_name, LB.Address
from Library_Branch LB
join Book_Copies BC
on BC.branch_id = LB.branch_id
where BC.num_of_copies > 10;

```

19. **List all books along with their publisher names and publication years, ordered by publication year.**

```sql

select * from Book
order by Pub_year;

```

20. **Find the total number of books available in the 'Downtown' branch.**

```sql
-- First Query

select LB.branch_name, sum(BC.num_of_copies) as Total_Books
from Library_Branch LB
join Book_Copies BC
on BC.branch_id = LB.branch_id
where LB.branch_name = "Downtown"
group by LB.branch_name

-- Second Query

select sum(BC.num_of_copies) as Total_Books
from Book_Copies BC
join Library_Branch LB
on LB.branch_id = BC.branch_id
where LB.branch_name = "Downtown";


```

## Combining All Levels

21. **List all books published by 'O'Reilly' and their publication years.**

```sql

select B.* from Book
where publisher_name = "O'Reilly";

```

22. **Retrieve the number of distinct publishers.**

```sql

select count(distinct P.Name) from publisher P;

```

23. **List all branches where books were borrowed in June 2017.**

```sql

select distinct LB.branch_name, LB.Address
from Library_Branch LB
join Book_Lender BL
on BL.branch_id = LB.branch_id
where BL.Date_Out between "2017-06-01" and "2017-06-30";

```

24. **Find the names of all borrowers who have borrowed books from both 'Downtown' and 'Uptown' branches.**

```sql

select BL.card_no
from Book_Lending BL
join Library_Branch LB
on BL.branch_id = LB.branch_id
where LB.branch_name IN ("Uptown", "Downtown")
group by BL.card_no
having count(distinct LB.branch_name) = 2;

-- or

select card_no
from Book_Lending
where branch_id IN (101, 103)
group by card_no
having count(distinct branch_id) = 2;

```

25. **Find the titles of books that have never been borrowed.**

```sql

select B.title
from Book B
LEFT JOIN Book_Lenders BL
on B.book_id = BL.book_id
where BL.book_id is NULL;


-- or

select B.title
from Book B
where not exists (
    select 1
    from Book_Lending BL
    where B.book_id = BL.book_id
);

```

26. **List all books and the number of times each book has been borrowed.**

```sql

select B.title, count(BL.book_Id) as Borrow_Count
from Book B
join Book_Lending BL
on B.book_id = BL.book_id
group by B.title;

```

| Title            | Borrow_Count |
| ---------------- | ------------ |
| SQL Fundamentals | 2            |
| Data Structures  | 1            |

28. **Find the names of all branches that do not have any copies of the book titled 'Data Structures'.**

```sql

select LB.branch_name
from Library_Branch LB
left join Book_Copies BC
on LB.branch_id = BC.branch_id and BC.book_id = (
    select B.book_id
    from Book B
    where B.Title = "Data Structures"
)
where BC.book_id is NULL;

-- or

select LB.branch_name
from Library_Branch LB
where LB.branch_id NOT IN (
    select BC.branch_id
    from Book_Copies BC
    join Book B
    on B.book_id = BC.book_id
    where B.Title = "Data Structures"
);

```

29. **Retrieve the branch details that have both books titled 'SQL Fundamentals' and 'Data Structures'.**

```sql

select LB.Branch_id, LB.Branch_Name, LB.Address
from Library_Branch LB
where LB.branch_id IN (
    Select BC.branch_id
    from Book_Copies BC
    join Book B
    on B.book_id = BC.book_id
    where B.Title IN ("SQL Fundamentals", "Data Structures")
    group by BC.branch_id
    having count(distinct B.Title) = 2
);

-- or

SELECT LB.Branch_id, LB.Branch_Name, LB.Address
FROM LIBRARY_BRANCH LB
JOIN BOOK_COPIES BC1 ON LB.Branch_id = BC1.Branch_id
JOIN BOOK B1 ON BC1.Book_id = B1.Book_id
JOIN BOOK_COPIES BC2 ON LB.Branch_id = BC2.Branch_id
JOIN BOOK B2 ON BC2.Book_id = B2.Book_id
WHERE B1.Title = 'SQL Fundamentals'
AND B2.Title = 'Data Structures';

```

30. **Find the authors who have written books that are available in more than one branch.**

```sql

select distinct BA.author_name
from Book_Authors BA
join Book B
on B.book_id = BA.book_id
join Book_Copies
on BC.book_id = B.book_id
group by BA.author_name, B.book_id
having count(distinct BC.branch_id) > 1;

-- or

select distinct BA.author_name
from Book_Authors BA
join Book_Copies BC
on BA.book_id = BC.book_id
group by BA.author_name, BA.book_id
having count(distinct BC.branch_id) > 1

```

31. **Retrieve the titles of all books along with the total number of copies available across all branches.**

```sql

select B.Title, sum(no_of_copes) as Total_Copies
from Book B
join Book_Copies BC
on B.book_id = BC.book_id
group by B.Title;

```

32. **Find the branches that have at least one book published after 2015.**

```sql

select distinct LB.branch_name
from Library_Branch LB
join Book_Copies BC
on LB.branch_id = BC.branch_id
join Book B
on B.book_id = BC.branch_id
where B.pub_year > 2015;

```

33. **List all books along with the names of their publishers, ordered by publisher name.**

```sql

select B.*
from Book B
order by B.publisher_name;

```

34. **Retrieve the list of all books published by 'Pearson' along with their authors' names.**

```sql

select B.*, BA.author_name
from Book B
join Book_Author BA
on B.book_id = BA.book_id
where B.publisher_name = "Pearson";
```

35. **Find the book titles that have been borrowed by all borrowers.**

```sql

select B.title
from Book B
join Book_Lending BL
on B.book_Id = BL.book_id
group by B.title
having count(distinct card_no) = (
    select count(distinct card_no)
    from Book_Lending
);

```

36. **Retrieve the average number of books borrowed per month in 2017.**

```sql

select extract(MONTH from Date_out) as Month,
count(book_id) / 12.0 as Avg_Borrow
from Book_Lending
where extract(Year from Date_out) = 2017
group by EXTRACT(MONTH FROM Date_Out);

```

37. **List all publishers and the number of books they have published.**

```sql

select P.publisher_Name, count(B.book_Id) as Total_Books
from Publisher P
join Book B
on P.publisher_name = B.publisher_name
group by P.publisher_name;

-- or

select B.publisher_name, count(B.book_Id)
from Book B
group by B.publisher_name;

```

38. **Find the books that have the highest and lowest number of copies in a single branch.**

```sql

select B.title
from Book B
join Book_Copies BC
on BC.book_id = B.book_id
where BC.number_of_copies = (select Max(number_of_copies) from Book_Copies)
or BC.number_of_copies = (select Min(number_of_copies) from Book_Copies);

```

39. **Retrieve the details of books published in each year along with the number of books published in that year.**

```sql

select B.pub_year, Count(B.book_Id) as Num_Books, Group_Concat(B.title) as Titles
from Book B
group by B.Pub_year

```

40. **List the branches along with the total number of books borrowed from each branch in 2017.**

```sql

select LB.branch_name, sum(BL.book_Id)
from Library_Branch LB
join Book_Lending BL
on LB.branch_id = BL.branch_Id
where Extract(Year from Date_out) = 2017
group by LB.branch_name;
```

41. **Retrieve the list of books that have been borrowed by the most number of distinct borrowers.**

```sql

select B.title from
Book B
join Book_Lending BL
on B.book_Id = BL.book_id
group by B.title
order by count(distinct BL.card_no) desc
limit 1;
```

42. **Find the names of all borrowers who have borrowed books from the 'Downtown' branch but not from the 'Uptown' branch.**

```sql

select BL.card_no
from Book_Lending BL
join Library_Branch LB
on BL.branch_id = LB.branch_id and LB.branch_name = "Downtown"
where BL.card_no not in (
    select BL1.card_no
    from Book_Lending BL1
    join Library_Branch LB1
    on BL1.branch_id = LB1.branch_id and LB1.branch_name = "UPtown";
)

```

43. **Retrieve the list of books along with their authors and the number of times they have been borrowed.**

```sql

select B.Title, BA.author_name, count(BL.book_id) as Book_Count
from Book B
join Book_Authors BA
on BA.book_id = B.book_id
Left join Book_Lending BL
on B.book_Id  BL.book_id
group by B.titl, BA.author_name;

```

44. **Find the names of borrowers who have borrowed the same book more than once.**

```sql

select card_no, count(book_id)
from Book_Lending
group by card_no, book_id
having count(book_id) > 1;

```

45. **Retrieve the details of books that have never been borrowed.**

```sql

select B.*
from Book B
left join Book_Lending BL
on B.book_id = BL.book_id
where BL.book_id is Null

```

46. **Find the branches that have the maximum and minimum number of book copies.**

```sql

select LB.branch_name, sum(BC.num_of_copies) as Total_sum
from Library_Branch LB
join Book_Copies BC
on BC.branch_id = LB.branch_id
group by LB.branch_name
having sum( BC.num_of_copies) = (
    select Max(Total)
    from (
        select sum(BC.num_of_copies) as Total
        from Book_Copies BC
        group by BC.branch_id
    ) as T1
)
or
sum(BC.num_of_copies) = (
    select Min(Total)
    from (
        select sum(BC.num_of_copies) as Total
        from Book_copies BC
        group by BC.branch_id
    ) as T2
);

```

47. **Retrieve the list of borrowers along with the total number of books they have borrowed in 2017.**

```sql

select BL.card_no, sum(BL.book_id) as Books_Borrowed
from Book_Lending BL
where Extract(Year from Date_out) = 2017
group by BL.card_no;


```

48. **List the books along with their authors that have been borrowed by the borrower with Card_No '1001'.**

```sql

select B.title, BA.author_name
from Book B
join Book_Author BA
on BA.book_id = B.book_id
join Book_Lending BL
on BL.book_id = B.book_id
where BL.card_no = '1001';
```

49. **Find the branches that have books borrowed by more than 100 distinct borrowers in 2017.**

```sql

select LB.branch_name
from Library_Branch LB
join Book_Lending BL
on BL.branch_Id = LB.branch_id
where Extract(Year from BL.Date_out) = 2017
group by LB.branch_name
having count(distinct BL.card_no) > 100;
```

50. **Retrieve the list of books that have been borrowed in every month of the year 2017.**

```sql

select B.Title from Books B
join Book_Lending BL
on BL.book_id = B.book_id
where Extract(Year from BL.date_out) = 2017;
group by B.Title
having count(distinct Extract(Month from BL.date_out))  = 12;

```
