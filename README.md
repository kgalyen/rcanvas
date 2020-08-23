
<!-- README.md is generated from README.Rmd. Please edit that file -->

![](https://avatars3.githubusercontent.com/u/515326?v=3&s=400)

# Description

`rcanvas` is a bouquet of functions to query your institution’s instance
of the [Canvas LMS.](https://www.canvaslms.com)

# Installation

`rcanvas` is not on CRAN, but can be installed via:

``` r
devtools::install_github("daranzolin/rcanvas")
library(rcanvas)
```

# Setup

Some prep work is required before use. You must first safely stash your
Canvas API token into your operating system’s keyring. This only needs
to be done once.

To obtain the Canvas API token follow this trail in Canvas:

`Canvas -> Account -> Settings -> Approved Integrations -> Add new
token`

You then need to run the following once in the R console:

``` r
set_canvas_token("YOUR_TOKEN_HERE")
```

Do not save your token or the code above in an `.R` file because it
could compromise the security of your token.

Each time you run load the `rcanvas` library you need to set your domain
like this:

``` r
set_canvas_domain("https://canvas.yourdomain.edu")
```

# Functions

The following functions are implemented:

  - `add_enrollments`: Enroll users into a course (or multiple courses)
  - `add_group_users`: Add users to designated groups
  - `add_groups`: Create groups
  - `comment_submission`: comment on submitted content
  - `create_course_folder`: create a folder within a course
  - `create_canvas_course`: create a new course
  - `create_course_content_migration`: migrate content from one course
    to another
  - `create_course_assignment`: create an assignment within a course
  - `get_announcements`: Get announcements for a course
  - `get_course_analytics_data`: Get course analytics data for a course
  - `get_course_gradebook`: Get the gradebook for a course
  - `get_course_items`: Get various course items, e.g. files, modules,
    pages, quizzes, etc.
  - `get_course_list`: List the courses you have permission to view
  - `get_course_user_groups`: Get users in a course and their group
  - `get_discussion_id`: Get the id for a specified discussion
  - `get_discussions_context`: Get the context for a specified
    discussion
  - `get_group_categories`: Get the categories for a specified group
  - `get_group_category`: Get a single group category
  - `get_group_users`: Get users which belong to a group
  - `get_groups_context`: Get the list of active groups in the given
    context that are visible to the user
  - `get_groups_self`: Get the groups which the current user (you)
    belongs to
  - `get_submission_single`: Get a single submission
  - `get_submissions`: Get submissions for a given course and assignment
  - `get_user_items`: Get various user items, e.g. missing submissions,
    page\_views, details, etc.
  - `grade_submission`: Grade a submission
  - `search_courses`: Search all public courses
  - `update_discussion_id`: Update a discussion by ID
  - `upload_course_file`: Upload a file to a course

# Usage

``` r
### Get all courses:
get_course_list()
get_course_list(include = c("teachers", "total_students"))

### Get course analytics data:
get_course_analytics_data(course_id = 20, type = "activity")

### Get course items:
get_course_items(course_id = 20, item = "users", include = "email")

### Get user items
get_user_items(user_id = 365, item = "details")
get_user_items(365, "missing_submissions")

### Get a course gradebook
get_course_gradebook(course_id = 20)

### Get submissions
get_submissions(course_id = 27, type = "assignments", type_id = 2248)
get_submissions(27, "quizzes", 168)

### Comment and grade submnissions
comment_submission(course_id = 27, assignment_id = 2248, 
                   user_id = 4227, comm = "Test comment!")
grade_submission(course_id = 27, assignment_id = 2248, 
                   user_id = 4227, grade = 95)

### Get announcements and discussions
get_announcements(course_id = 27) 
get_announcements(course_id = 27, start_date = "2017-02-01") 
get_discussions_context(4371405, object_type = "courses")
```

-----

# Future Work

  - Additional functions
  - More precise querying
  - More tests
  - Vignette
