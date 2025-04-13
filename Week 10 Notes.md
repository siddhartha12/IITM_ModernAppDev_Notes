# L10.1 - Application test
Why?
Does something work as intended
* requirements - specification
* responds correctly to input
* respond within reasonable time
* installation an environment
* usability and correctness

## Static vs Dynamic
statis: code review, correcteness proofs

Dynamic: functional, inputs


## White-box testing
* detailed knowledge of implementatio
* Can examine internal variables, counters
* Tests can be created based on knowledge of internal structure
* pro:
	* more detailed information, better tests
* con
	* can lead to focusing on less important parts because code is known
	* does not encourage clean abstraction

## Black box testing
* only interface are available, not the code
* test on how it looks from outsite
* pro
	* closer to real usage scenario
	* enforces clean abstraction of interface
* con
	* may miss corner cases that would have been obvious if internal strucutre was known

## grey box
* hybrid
* interface as fat as possible
* internal for debuggin and variables etc.

## Regression
* maintain series of tests starting from basic development of code
* regression: loss of functionality introduced by some change in the code

## Coverage:
how much of the code is covered
* every line is executed at least one -100% code coverage
	* does not guarentee correctness
	* may be more complex paths or other conditions cause failure


# L10.2 - levels of testing
# initial requirements gathering
* who are stakeholders?
* funcitonality: each group has different needs
* non functional: front end

### fathering
* extensive discussion with end users
* avois language ambiguity
* capture use cases and examples
* start thinking about test cases and how requirements will be validated

## Units of implementation
* break functional requitrements down to small unit
Unit testing
test each individual unit fo implementation
May be single controllers
Clearly define inputs and expected output
testable in isolation
can each unit be tested without the entire system


# L10.3 - Test generation
## API based testing
* abstraction for system design
* standard representation for APIs
### Use cases
import api definition from standard like openai
generate tests fo rspecific endpoints, scenarios

## Abstract Tests
* Semi