# The Sql Surgeons Project 1

Cas van Ruijven [Cas van Ruijven](https://github.com/casvanruijven/the_sql_surgeons_project_1)\
Nathan Riggle [Nathan Riggle](https://github.com/nathanriggle/SQL_Project1)\
Max Weaver [Max Weaver](https://github.com/MaxWeaver7/SQL-Project-One)\
Sam Holtzclaw [Sam Holtzclaw](https://github.com/holtzclawsam/SQL-Su)\
Jack Beal [Jack Beal](https://github.com/Jhbeal03/MIST)

## Description
This gym database is designed to manage a fitness center's operations, including memberships, classes, employee schedules, and equipment usage. It tracks membership payments, attendance at classes, feedback, and requests for equipment maintenance. Employees can manage classes, supervise others, and receive feedback from members. The database supports data storage related to these activities and does not handle more advanced business processes like payroll or marketing.

![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/Gym%20database%20model.png)

- Employee: Stores employee details, including their supervisor and certification level.
- Member: Contains member information like contact details and the date they joined.
- Membership: Tracks the type of membership, price, and access level.
- Payments: Logs payment records, linking members to their membership plans.
- Class and Class_Schedule: Tracks fitness classes, including schedule details and employee instructors.
- Feedback: Records feedback given by members about classes or employees.
- Equipment and Equipment_Usage: Monitors gym equipment and its usage in classes, with associated maintenance requests.
- Attendance: Captures class attendance information for members.
- Maintenance_Request: Logs equipment maintenance needs.

## Data Dictionary

#### Member
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| member_id        | INT            | Unique identifier for each member (Primary Key) |
| first_name       | VARCHAR(45)    | Member’s first name                          |
| last_name        | VARCHAR(45)    | Member’s last name                           |
| date_of_birth    | DATE           | Member’s date of birth                       |
| email            | VARCHAR(45)    | Contact email for the member                 |
| phone_number     | VARCHAR(45)    | Member’s contact number                      |
| join_date        | DATE           | Date when the member joined                  |

#### Membership
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| membership_id    | INT            | Unique identifier for each membership (Primary Key) |
| membership_name   | VARCHAR(45)    | Name of the membership plan                   |
| price            | DECIMAL(6,2)   | Cost of the membership                        |
| duration         | INT            | Duration of the membership in months         |
| access_level     | INT            | Level of access granted by the membership     |

#### Employee
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| employee_id      | INT            | Unique identifier for each employee (Primary Key) |
| first_name       | VARCHAR(45)    | Employee’s first name                        |
| last_name        | VARCHAR(45)    | Employee’s last name                         |
| specialization    | VARCHAR(45)    | Area of expertise for the employee            |
| certification_level | INT          | Level of certification held by the employee   |
| email            | VARCHAR(45)    | Contact email for the employee               |
| phone_number     | VARCHAR(45)    | Employee’s contact number                    |
| supervised_by    | INT            | Employee ID of the supervisor                 |

#### Class
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| class_id         | INT            | Unique identifier for each class (Primary Key) |
| class_name       | VARCHAR(45)    | Name of the class                            |
| description      | VARCHAR(255)   | Description of the class                     |
| intensity_level   | INT            | Intensity level of the class                 |
| max_capacity     | INT            | Maximum number of participants allowed       |
| duration         | INT            | Duration of the class in minutes             |

#### Class_Schedule
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| class_schedule_id | INT            | Unique identifier for each class schedule (Primary Key) |
| employee_id      | INT            | ID of the employee conducting the class      |
| class_id         | INT            | ID of the class scheduled                    |
| start_date_time  | DATETIME       | Date and time when the class starts         |
| end_date_time    | DATETIME       | Date and time when the class ends           |
| location         | VARCHAR(45)    | Location where the class is held             |

#### Attendance
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| attendance_id    | INT            | Unique identifier for each attendance record (Primary Key) |
| class_schedule_id | INT            | ID of the scheduled class                    |
| member_id        | INT            | ID of the member attending                   |
| ShowedUp         | TINYINT        | Indicator of whether the member showed up (1 for Yes, 0 for No) |

#### Payments
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| payment_id       | INT            | Unique identifier for each payment (Primary Key) |
| member_id        | INT            | ID of the member making the payment         |
| membership_id    | INT            | ID of the membership being paid for         |
| payment_date     | DATE           | Date when the payment was made              |
| payment_amount   | DECIMAL(5,2)   | Amount paid                                  |
| payment_method    | VARCHAR(45)    | Method of payment (e.g., Credit Card, Cash) |

#### Feedback
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| feedback_id      | INT            | Unique identifier for each feedback entry (Primary Key) |
| member_id        | INT            | ID of the member providing feedback         |
| employee_id      | INT            | ID of the employee receiving feedback       |
| class_id         | INT            | ID of the class related to the feedback     |
| feedback_text    | VARCHAR(255)   | Text of the feedback provided                |
| rating           | INT            | Rating given by the member (e.g., 1 to 5)   |
| feedback_date    | DATE           | Date when the feedback was submitted         |

#### Equipment
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| equipment_id     | INT            | Unique identifier for each piece of equipment (Primary Key) |
| equipment_name   | VARCHAR(45)    | Name of the equipment                        |
| purchase_date    | DATE           | Date when the equipment was purchased       |
| maintenance_due_date | DATE       | Date when the next maintenance is due      |
| status           | VARCHAR(45)    | Current status of the equipment (e.g., Good, Needs Repair) |
| location         | VARCHAR(45)    | Location of the equipment within the facility |

#### Equipment_Usage
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| equipment_id     | INT            | ID of the equipment used                    |
| class_schedule_id | INT            | ID of the class schedule using the equipment |
| (Composite Key)  |                | Combination of equipment_id and class_schedule_id serves as the primary key |

#### Maintenance_Request
| Column Name      | Data Type      | Description                                  |
|------------------|----------------|----------------------------------------------|
| maintenance_request_id | INT      | Unique identifier for each maintenance request (Primary Key) |
| equipment_id     | INT            | ID of the equipment requiring maintenance    |
| request_date      | DATE           | Date when the maintenance request was made  |
| request_status    | VARCHAR(45)    | Current status of the maintenance request    |
| completed_date    | DATE           | Date when the maintenance was completed      |

## Queries

| Database information                   | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |
|----------------------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| **Multiple table join**                |    x    |    x    |    x    |    x    |    x    |    x    |         |         |         |          |
| **Subquery**                           |         |         |         |         |         |         |         |         |         |          |
| **Group by, Aggregation**              |    x    |    x    |         |    x    |    x    |    x    |         |         |    x    |          |
| **Date functions**                     |         |    x    |    x    |         |         |         |         |         |         |          |
| **Join**                               |    x    |    x    |    x    |    x    |    x    |    x    |         |         |         |          |
| **Simple queries**                     |         |         |         |         |         |         |    x    |    x    |    x    |    x     |


#### Query 1: Total Pending Maintenance Requests Per Equipment (Complex)
```{sql}
SELECT 
    e.equipment_name, 
    COUNT(mr.maintenance_request_id) AS pending_requests
FROM 
    Equipment e
JOIN 
    Maintenance_Request mr ON e.equipment_id = mr.equipment_id
WHERE 
    mr.request_status = 'Pending'
GROUP BY 
    e.equipment_name
ORDER BY 
    pending_requests DESC;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/1.png)\
This query identifies the total number of pending maintenance requests for each piece of equipment. By providing a clear overview of pending requests, it allows managers to prioritize their focus on equipment that requires immediate maintenance attention.

#### Query 2: Average Time Taken to Complete Maintenance by Equipment (Complex)
```{sql}
SELECT 
    e.equipment_name, 
    AVG(DATEDIFF(mr.completed_date, mr.request_date)) AS avg_days_to_complete
FROM 
    Equipment e
JOIN 
    Maintenance_Request mr ON e.equipment_id = mr.equipment_id
WHERE 
    mr.request_status = 'Completed'
GROUP BY 
    e.equipment_name
ORDER BY 
    avg_days_to_complete ASC;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/2.png)\
This query calculates the average time taken to complete maintenance tasks for each type of equipment. By analyzing completion times, managers can assess the efficiency of their maintenance processes and identify opportunities for improvement.

#### Query 3: How long request has been submitted (Complex)
```{sql}
SELECT
    equipment_name,
	DATEDIFF(CURRENT_DATE, request_date) AS DateDiff_between_request_today
FROM 
    Maintenance_Request mr
JOIN 
    Equipment e ON mr.equipment_id = e.equipment_id
WHERE
	request_status regexp 'pending'
ORDER BY 
    DATEDIFF(CURRENT_DATE, request_date) DESC;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/3.png)\
This query shows the time elapsed since maintenance requests were made for each piece of equipment. A manager would use this to track delayed maintenance, ensuring equipment is repaired quickly to minimize downtime and improve member satisfaction.

#### Query 4: Revenue Generated by Memberships (Complex)
```{sql}
SELECT 
    m.membership_name,
    SUM(p.payment_amount) AS total_revenue
FROM 
    Payments p
JOIN 
    Membership m ON p.membership_id = m.membership_id
GROUP BY 
    m.membership_name;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/4.png)\
This query aggregates the total revenue generated by each type of membership. Understanding revenue contributions from different memberships enables managers to evaluate the effectiveness of their pricing strategies and make informed decisions about promotions or changes to membership offerings.

#### Query 5: Employee Performance Based on Class Feedback Ratings (Average Rating, Total Feedback) (Complex)
```{sql}
SELECT 
    CONCAT(e.first_name, ' ', e.last_name) AS Name, 
    AVG(f.rating) AS average_rating,
    COUNT(f.feedback_id) AS feedback_count
FROM 
    Feedback f
JOIN 
    Employee e ON e.employee_id = f.employee_id
GROUP BY 
    Name;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/5.png)\
This query evaluates employee performance through average feedback ratings and counts, helping identify top performers and those needing improvement. It aids in improving customer satisfaction and fostering staff development.

#### Query 6: (Complex)
```{sql}
SELECT 
    c.class_name,
    SUM(a.ShowedUp) AS total_showed_up,
    c.max_capacity,
    (SUM(a.ShowedUp) / c.max_capacity) * 100 AS utilization_percentage
FROM 
    Class c
LEFT JOIN 
    Class_Schedule cs ON c.class_id = cs.class_id
LEFT JOIN 
    Attendance a ON cs.class_schedule_id = a.class_schedule_id
GROUP BY 
    c.class_name, c.max_capacity;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/6.png)\
This query calculates the attendance figures and utilization percentage for each class compared to its maximum capacity. By analyzing these metrics, managers can determine class popularity and make necessary adjustments to scheduling or capacity to better align with member interest.

#### Query 7: List of All Pending Maintenance Requests (Simple)
```{sql}
SELECT 
    maintenance_request_id, 
    equipment_id, 
    request_date 
FROM 
    Maintenance_Request
WHERE 
    request_status = 'Pending';
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/7.png)\
This query provides a comprehensive list of all pending maintenance requests, detailing the request ID, equipment ID, and request date. This information is crucial for managers to monitor ongoing issues and ensure that necessary maintenance is addressed promptly.

#### Query 8: List of All Completed Maintenance Requests
```{sql}
SELECT 
    maintenance_request_id, 
    equipment_id, 
    completed_date 
FROM 
    Maintenance_Request
WHERE 
    request_status = 'Completed';
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/8.png)\
This query retrieves information about all completed maintenance requests, including the maintenance request ID, equipment ID, and completion date. This data helps managers track maintenance history and evaluate the effectiveness of maintenance operations.

#### Query 9: Count of Maintenance Requests by Status (Simple)
```{sql}
SELECT 
    COUNT(maintenance_request_id) AS total_requests, 
    request_status
FROM 
    Maintenance_Request
GROUP BY 
    request_status;
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/9.png)\
This query counts the total number of maintenance requests grouped by their status. By understanding the distribution of request statuses, managers can identify trends and areas requiring attention, ensuring efficient maintenance operations.

#### Query 10: Count of Technicians by Specialization (Simple)
```{sql}
SELECT COUNT(equipment_id) AS total_active_equipment
FROM Equipment
WHERE status = 'Good';
```
![Gym Database Model](https://github.com/casvanruijven/the_sql_surgeons_project_1/blob/main/10.png)\
This query counts the number of active equipment items that are in good condition. By knowing how much operational equipment is available, managers can plan effectively for maintenance and usage, ensuring that resources are utilized efficiently.# SQL_Project1
