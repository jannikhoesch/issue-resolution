# Report for assignment 4

## Project

Name: Toga

URL: https://github.com/beeware/toga

Toga is a cross platform GUI toolkit. It consists of a library of base components with a shared interface to simplify platform-agnostic GUI development.

## Onboarding experience

Our initial plan was to continue with the same project that we worked on during the previous assignment. However, while searching for issues, we realized that the project lacks a lot of documentation and that the current issues were either too small or too complex to fix within the scope of this assignment. We therefore decided to look for different repositories and finally selected the Toga repository, because of its extensive documentation and beginner-friendly usability for contribution. The setup of the project was quite straight-forward and we could easily find issues to work on with the label filtering on GitHub. A contributor's guide was included which went through each step to set up the development environment with detailed descriptions. 

We finally decided to choose an issue that was both well described and seemed appropriate to work on in the scope of this assignment. After completing the issue, we submitted a pull request to the Toga repository and began working on a second issue since we had some time left. When we received feedback on the pull request, we returned to the first issue and made some adjustments so that it could be approved to the actual project.

## Effort spent

The time spent by each person during this project is presented in the table below.

|     | Jannik | Harald | Zyad | Karin | Amanda |
| --- | :----: | :----: | :--: | :---: | :----: |
| 1. Plenary discussions/meetings          |3h |2h| | |2h|
| 2. Discussions within parts of the group |3h 30min |4h| | |3h 30min|
| 3. Reading documentation                 |2h |2h 30min | | |2h|
| 4. Configuration and setup               |30min |1h | | |1h|
| 5. Analyzing code/output                 |3h |4h50min| | |3h|
| 6. Writing documentation                 |1h 30min |1h | | |2h 30min| 
| 7. Writing code                          |5h 30min |3h 40min| | |5h|
| 8. Running code                          |1h 30min |1h 20min| | |1h|
| Total:                                   |20h |20h 20min| | |20h|

For setting up tools and libraries (step 4), enumerate all dependencies
you took care of and where you spent your time, if that time exceeds
30 minutes.

## Overview of issue(s) and work done.

### Issue #2144

Title: Configurable text line height in Canvas

URL: https://github.com/beeware/toga/issues/2144

Our fork: https://github.com/Heroldpls/toga-2144

#### Summary: 
The `write_text` and`measure_text` methods in Canvas support multiple lines but lack control over line spacing. Adding a`line_height` argument, similar to CSS, would allow users to specify spacing as a multiple of the font size for better text layout control.

#### Scope (functionality and code affected): 
To solve this issue, both the interface layer and implementation layer were changed. The interface consists of the core which forms the API for the different types of widgets that can be created. The Canvas widget was changed by adding a parameter line_height into the methods write_text and measure_test in the Canvas class.

The implementation layer consists of the different backends and thereby contains the platform-specific implementation of each widget. The Canvas widget is supported by Windows, MacOS, GTK, Android and IOS so therefore each of these backends needed to be changed so that the line height functionality for the Canvas could be implemented in each backend. 

### Issue #2145

Title: Configurable text line height in Label

URL: https://github.com/beeware/toga/issues/2145

Our fork: https://github.com/jannikhoesch/toga-2145

#### Summary:
The Label widget accepts multiple lines, but there's no way to control their spacing. Add a line_height style with the same meaning as in CSS to allow custom spacing between lines in a Label.

#### Scope (functionality and code affected):
To add a line height functionality in the Label widget, the interface- and implementation layer had to be changed here as well. In contrast to the Canvas widget (#2144), the Label widget does not have line height support from the native layer (the lowest layer) which uses the widget toolkit from the user's system. In this case the interface layer was changed by adding a method for setting the line height to the Style class. In the Windows backend, the reqiured height was manually calculated, the Label size was changed accordingly and then the Label text was manually written out. 


## Requirements for the new feature or requirements affected by functionality being refactored

Optional (point 3): trace tests to requirements.

## Code changes

### Patch

(copy your changes or the add git command to show them)

```git diff 01152b56b9607a5cc1dabb9e94970cc589baff01 c61fb7e643c1fb361b34c8b184731cfad1570968```  
(The second one is the most recent commit, have have to be updated)

Optional (point 4): the patch is clean.  
This point should be fulfilled.

Optional (point 5): considered for acceptance (passes all automated checks).  
[Pull Request](https://github.com/beeware/toga/pull/3217)

## Test results

Overall results with link to a copy or excerpt of the logs (before/after
refactoring).

Before: [Logs](logs_before)

After: [Logs](logs_after)


## UML class diagram and its description

### Key changes/classes affected

#### Core API - Canvas:
![classes_canvas](https://github.com/user-attachments/assets/fd89b88f-3903-46b6-a68f-579c1ca343ec)

#### Backend - Windows:
![classes_windows](https://github.com/user-attachments/assets/4599bf39-775a-4073-9195-c8398f44fbb5)

Optional (point 1): Architectural overview.

Optional (point 2): relation to design pattern(s).

## Overall experience

### What are your main take-aways from this project? What did you learn?
One of our main takeaways from this project is the importance of good documentation. The repository that we worked on during this assignment had significantly better documentation than the previous project that we worked on. This made the setup easier and it also helped answering several questions that rised along the way. 

Futhermore, we gained experience of working with different backend implementations and saw how platform-specific constraints can have an impact. We also noticed that problems that seem similar may require different approaches. The second issue that we worked on had a very similar request as the first one but for a Label widget instead of a Canvas widget, but since they had different native layer support, they had to be implemnted very differently.

### How did you grow as a team, using the Essence standard to evaluate yourself?
We still evaluate ourselves to be in the "In Place"-state according to the Essence standard. We have become much more comfortable using Git but there are still times where we have to think more about what we do and therefore do we not believe that we are on the next step yet. However, while reflecting on the course, we do see a clear improvement in both our skills and teamwork since the begining of the course.

### Optional (point 6): How would you put your work in context with best software engineering practice?

We focus on the most relevant alphas from the SEMAT kernel: 
#### 1.	Opportunity
Switching from the unmaintained project that we used for the previous assignment to the well-maintained toga project was a good choice in terms of delivering a value with our work. The toga project serves a purpose to many users and implementing a new feature - even a small one like in our case - has a bigger impact than solving big issues in not used projects.
#### 2.	Stakeholders
The stakeholders of the project are both the maintainers and the users of toga. In the issue description the maintainer mentioned that the first issue we worked on would be less complex than the second issue but less helpful for most users and the second issue would be more complex to implement but also more helpful for the users. While we wanted to solve an issue that would deliver value for more users, we first started with the simpler one to at least get something done.
#### 3.	Requirements
The issue descriptions were quite detailed and made it easy to understand the functional requirements. During our work we also mostly focused on these functional requirements. To be more professional we could have also defined non-functional requirements before we started with the implementation.
#### 4.	Software System
The whole software system was well maintained with extensive documentation. To contribute to the project the pull request had to pass CI tests that extensively tested both the core API and the different backends. While the support for a variety of backends is very well integrated some backends (e.g. textual) were less supported and missed certain functionality so that we could not implement our feature into them.

Optional (point 7): Is there something special you want to mention here?
