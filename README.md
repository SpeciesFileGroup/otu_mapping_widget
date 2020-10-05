# Currently unamed entity name matching project

Inspired by the mapper between OTUs and names in the [Open Tree of Life](https://tree.opentreeoflife.org) project.

# Goals 
* An application agnostic widget
* An efficient interface that facilitates "last-mile" human confirmation of matches between two stacks of "names"

## Approach

* Hooks/initialization exists to populate two stacks of "names", a left "query" and a right "target"
* How names get onto either stack is beyond the scope of this widget, for example the wrapping tool can use fuzzy logic to predict targets for a query set, then only send the predicted targets.  
* Actions within the widget can fire events that in turn could adjust the membership of target and query stacks

# Installation

_TODO_

# Lisence

NCSA, University of Illinois (an MIT derivative).
