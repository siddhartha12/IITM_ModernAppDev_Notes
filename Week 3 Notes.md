# L3.1 - Overview of MVC
# L3.2 - Views
## View
User interface:
* Screen
* Audio
* Vibration
* Motor

User Interaction Inputs:
* Keyboard
* touch
* voice
* buttons*

User Interaction:
* Determined by hardware constraints
* Different target devices possible
* User agent informtion

Types of Vies:
* Fully static
* Partly Dynamic (Eg: Wiki)
* Mostly Dynamic (Amazon, Netflix etc)

Output:
* HTML
* dynamic images
* JSON/XML

# L3.3 - User Interface Design

* Design for interaction with user
* Goals:
	* Simple
	* Efficient
* Aesthetics
* Accessibility

Systematic process:
* Functionality requirements
* User and task analysis
* Prototyping
* Testing

# L3.4 - Usability Heuristics
Jakob Neilsen's heuristics for design
https://www.nngroup.com/articles/ten-usability-heuristics/

## 1. Visibility of system status
Design should always keep users informed about what is going on, through appropriate feedback within a reasonable amount of time

## 2. Match between system and the real world
The design should speak the users' language. Use words, phrases, and concepts familiar to the user, rather than internal jargon. Follow real-world conventions, making information appear in a natural and logical order.

## 3. User control and freedom
Users often perform actions by mistake. They need a clearly marked "emergency exit" to leave the unwanted action without having to go through an extended process.

## 4. Consistency and Standards
Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform and industry conventions.

## 5. Error Prevention
Good error messages are important, but the best designs carefully prevent problems from occurring in the first place. Either eliminate error-prone conditions, or check for them and present users with a confirmation option before they commit to the action.

## 6. REcognition rather than recall
Minimize the user's memory load by making elements, actions, and options visible. The user should not have to remember information from one part of the interface to another. Information required to use the design (e.g. field labels or menu items) should be visible or easily retrievable when needed.

## 7. Flexibility and Efficiency of Use

Shortcuts — hidden from novice users — may speed up the interaction for the expert user so that the design can cater to both inexperienced and experienced users. Allow users to tailor frequent actions.

## 8. Aesthetic and Minimalist Design
Interfaces should not contain information that is irrelevant or rarely needed. Every extra unit of information in an interface competes with the relevant units of information and diminishes their relative visibility.


## 9.Help Users Recognize, Diagnose, and Recover from Errors
Error messages should be expressed in plain language (no error codes), precisely indicate the problem, and constructively suggest a solution.

## 10. Help and Documentation
It’s best if the system doesn’t need any additional explanation. However, it may be necessary to provide documentation to help users understand how to complete their tasks.

# L3.5 - Tools p1
## Wireframes
* visual guide to structure
* Informationdesign
* Navigation desing
* User interface design
**Example** LucidChart

# L3.6 - Tools p2

## Programmatic HTML: PyHTML
* Composable function - each function generates a specific output
```
import pyhtml as h

t = h.html(
	h.head(
		h.title("Test Page")
	)
	h.body(
		h.h1("This is a title")
		h.div('This is a title')
		h.div(
			h.h2('inside titel')
			h.p('some text in a paragraph')
		)
	)
)

print(t.render())
```

More complex

```
def f_table(ctx):
	return(
		tr(
			td(cell) for cell in row
		) for row in ctx['table']
	)
```

## Templates
* Standard template text
* Placeholders/Variables
* Basic (very limited) programmability
* Examples:
	* Python
	* Jinja2
	* Genshi
	* Mako

# L3.7 - Accessibility
* Various forms of disability or impairment

## Standards
Interplay between many components of a page
* Web content
* User-Agent: Browsers, mobile browsers, speech orientic, assistive devices etc
* Authoring tools: word processor complier 

## Principles
### Operable:
* Provide text alternative for non-text content
* Provide captions and other alternatives for multimedia
* Create content that can be presented in different ways, including by assistive technologies, without losing meaning
* Make it easier for user to see and hear content
* Make ir easeir to use inputs other than keyboard

### Understandable
* Make text readable adn understandable
* make content appear and operatein predictable ways
* Help users avoid and correct mistakes

### Robust:
* maximize compatibility with current and future user tools
* 