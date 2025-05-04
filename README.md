# airbnb-clone-project
## Description
The Airbnb Clone Project is a comprehensive, real-world application designed to simulate the development of a robust booking platform like Airbnb. It involves a deep dive into full-stack development, focusing on backend systems, database design, API development, and application security. This project enables learners to understand complex architectures, workflows, and collaborative team dynamics while building a scalable web application.
## Technology Stack
- Django Web Framework
Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.
- PostgreSQL
PostgreSQL is a powerful, open source object-relational database system with over 35 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance.
- GraphQL
GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.
## Team Roles
- Software architect
An architect is an expert-level software engineer who makes executive software design decisions on behalf of an app development team. You will need one if you deal with a software product with complex requirements or legacy software that calls for profound changes. A software architect decides which services and databases should communicate together, how integrations should work, and how to ensure that the product is secure and stable.
- Software developer
A software developer does the actual job and codes an application. And just like an app features a front end and a back end, there are front-end and back-end developers. Back-end developers, in turn, implement the core of an app—its algorithms and business logic. Experienced back-end developers not only write code but also do the tasks of an architect—for example, devise an app architecture or design and implement the necessary integrations.
- DevOps engineer
Even in Agile environments, development and operations teams can be siloed. DevOps engineers serve as a link between the two teams, unifying and automating the software delivery process and helping strike a balance between introducing changes quickly and keeping an application stable. Working together with software developers, system administrators, and operational staff, DevOps engineers oversee and facilitate code releases on a CI/CD basis.
## Database Design

### 1. **User**

Represents a person who uses the platform — either a guest or a property owner.

**Key Fields:**

* `id`: unique identifier
* `name`: full name
* `email`: contact email
* `role`: `'guest' | 'host'` (or both)
* `created_at`: account creation date

**Relationships:**

* A **user can own** multiple **properties**.
* A **user can make** multiple **bookings**.
* A **user can leave** multiple **reviews**.
* A **user can make** **payments**.

---

### 2. **Property**

Represents a place that can be booked (e.g., apartment, hotel room, house).

**Key Fields:**

* `id`: unique identifier
* `title`: name or title of the property
* `location`: address or geolocation data
* `description`: details about the property
* `owner_id`: references the `User` who owns it

**Relationships:**

* A **property belongs to** one **user (host)**.
* A **property can have** multiple **bookings**.
* A **property can have** multiple **reviews**.

---

### 3. **Booking**

Represents a reservation made by a user for a specific property.

**Key Fields:**

* `id`: unique identifier
* `property_id`: the `Property` being booked
* `user_id`: the `User` who made the booking
* `start_date`: booking start
* `end_date`: booking end

**Relationships:**

* A **booking belongs to** one **user (guest)**.
* A **booking belongs to** one **property**.
* A **booking has one** **payment**.

---

### 4. **Review**

Represents feedback left by a user about a property.

**Key Fields:**

* `id`: unique identifier
* `property_id`: the reviewed property
* `user_id`: who left the review
* `rating`: score (e.g., 1 to 5)
* `comment`: optional text feedback

**Relationships:**

* A **review belongs to** one **user**.
* A **review belongs to** one **property**.

---

### 5. **Payment**

Tracks payment transactions for bookings.

**Key Fields:**

* `id`: unique identifier
* `booking_id`: references the related booking
* `amount`: total paid
* `status`: `'pending' | 'completed' | 'failed'`
* `paid_at`: timestamp

**Relationships:**

* A **payment belongs to** one **booking**.
* A **payment is indirectly tied to** one **user** (via booking).
