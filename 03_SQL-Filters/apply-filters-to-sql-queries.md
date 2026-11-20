# Apply Filters to SQL Queries

**Tools:** SQL  **Concepts:** `WHERE`, `AND`, `OR`, `NOT`, `LIKE`, date/time filtering  **Source:** Google Cybersecurity Professional Certificate

---

## 📋 Project Description

I'm a security professional at a large organization, and I'm investigating potential security issues involving login attempts and employee machines. In this project, I used SQL filters on the organization's `log_in_attempts` and `employees` tables. I pulled the records needed to look into suspicious logins and to find the employee machines that need security updates.

---

## 1. Retrieve after-hours failed login attempts

A potential security incident happened after business hours, so I needed every **failed** login attempt made **after 18:00**.

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = FALSE;
```

**How it works:**
- `login_time > '18:00'` keeps only attempts after 6:00 PM.
- `success = FALSE` keeps only failed attempts. A value of `0` means the same thing.
- `AND` requires **both** conditions to be true, so the results are failed logins that happened after hours.

---

## 2. Retrieve login attempts on specific dates

A suspicious event happened on **2022-05-09**, so I pulled every login attempt from that day and the day before.

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

**How it works:**
- `login_date = '2022-05-09'` matches attempts on the day of the event.
- `login_date = '2022-05-08'` matches attempts on the day before.
- `OR` returns records that match **either** condition, so both days are included.

---

## 3. Retrieve login attempts outside of Mexico

The team found that the suspicious activity **did not** come from Mexico, so I filtered for login attempts from every other country.

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

**How it works:**
- The `country` column stores Mexico as both `MEX` and `MEXICO`.
- `LIKE 'MEX%'` matches any value that **starts with** "MEX". The `%` wildcard stands for any number of characters, so both spellings are caught.
- `NOT` flips the condition and returns every record that **doesn't** match, which means all countries except Mexico.

---

## 4. Retrieve employees in Marketing (East building)

The team needed to update the machines of **Marketing** employees in the **East** building.

```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

**How it works:**
- `department = 'Marketing'` keeps only Marketing employees.
- Office values look like `East-170` or `North-434`, so `office LIKE 'East%'` matches any office that starts with "East".
- `AND` requires **both** conditions, so the results are Marketing employees in the East building.

---

## 5. Retrieve employees in Finance or Sales

A different security update was needed for machines in the **Sales** and **Finance** departments.

```sql
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';
```

**How it works:**
- Each employee belongs to only one department, so `AND` would return nothing.
- `OR` returns employees in **either** department, so everyone in Finance and everyone in Sales is included.

---

## 6. Retrieve all employees not in IT

The **Information Technology** department already had one update, so every other department still needed it.

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

**How it works:**
- `department = 'Information Technology'` would match only IT employees.
- `NOT` reverses it and returns every employee **outside** IT.
- An equivalent version is `WHERE department <> 'Information Technology'`.

---

## 📝 Summary

I used SQL filters to support two security investigations and three machine-update tasks. For the login investigation, I combined conditions with `AND` and `OR` to filter by time, date, and success status. I also used `NOT` with `LIKE` and the `%` wildcard to exclude login attempts from Mexico. For the employee updates, I used the same operators to pull exactly the groups of machines that needed patching. Being precise like this lets a security team act quickly without sorting through irrelevant records.

---

## 🛠️ Skills Demonstrated
- Writing SQL queries with `SELECT`, `FROM`, and `WHERE`
- Combining conditions with `AND` and `OR`
- Excluding records with `NOT`
- Pattern matching with `LIKE` and the `%` wildcard
- Filtering by dates and times
- Using SQL to support security investigations and patch management
