# Sprint 1 Worksheet (Group 8)

## Repositories

-   Administration Repo: [admin](https://github.com/COMP-4350-Group-8/admin)
-   Product Repo: [comp4350-project](https://github.com/COMP-4350-Group-8/comp4350-project)

## Testing Plan

[Testing Plan](https://github.com/COMP-4350-Group-8/admin/wiki/Testing-Plan)

## Unit/integration/acceptance test

We did not complete any user stories during this sprint, so our tests reflect that. We have tests in our backend and in our React frontend. Our React tests verify which elements are rendered, the navigation between pages works, and the logic relating to the current implementation of the note creation for races. The main.jsx file is missing from the tests because it just renders the App component and doesn't have any logic.

### Coverage Report

#### Frontend - Flutter

No tests, so no coverage to report.

#### Frontend - React

| File           | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s |
| -------------- | ------- | -------- | ------- | ------- | ----------------- |
| All files      | 85.71   | 100      | 100     | 85      |
| src            | 25      | 100      | 100     | 25      |
| App.jsx        | 100     | 100      | 100     | 100     |
| main.jsx       | 0       | 100      | 100     | 0       | 7-10              |
| src/pages      | 100     | 100      | 100     | 100     |
| CreateRace.jsx | 100     | 100      | 100     | 100     |
| Home.jsx       | 100     | 100      | 100     | 100     |

#### Backend - ASP.NET
See [Backend Coverage](https://htmlpreview.github.io/?https://github.com/COMP-4350-Group-8/admin/blob/main/sprints/sprint-1/coverage-report/index.html)

## Testing importance

### Unit Tests

-   [backend/Tests/RaceTests.cs (Cont_GetRace)](https://github.com/COMP-4350-Group-8/comp4350-project/blob/cd2df183810581ee2abfae6d20ca133c722871aa/backend/Tests/RaceTests.cs#L40). This test verifies that trying to get a race that does not exist will return a not found error result.
-   [backend/Tests/RaceTests.cs (Add_Race)](https://github.com/COMP-4350-Group-8/comp4350-project/blob/cd2df183810581ee2abfae6d20ca133c722871aa/backend/Tests/RaceTests.cs#L57). This test verifies that adding an empty race will result in an exception.
-   [frontend/react/tests/pages/CreateRace.test.jsx ("should render the note form")](https://github.com/COMP-4350-Group-8/comp4350-project/blob/cd2df183810581ee2abfae6d20ca133c722871aa/frontend/react/tests/pages/CreateRace.test.jsx#L18). This test verifies that the form to add notes to a race renders correctly.

### Integration Tests

-   [backend/Tests/RaceTests.cs (Calculate_Result_Full)](https://github.com/COMP-4350-Group-8/comp4350-project/blob/cd2df183810581ee2abfae6d20ca133c722871aa/backend/Tests/RaceTests.cs#L91). This test verifies that race results are calculated correctly.
-   [frontend/react/tests/pages/CreateRace.test.jsx ("should add a note to the list when the user clicks the Add Note button")](https://github.com/COMP-4350-Group-8/comp4350-project/blob/cd2df183810581ee2abfae6d20ca133c722871aa/frontend/react/tests/pages/CreateRace.test.jsx#L36). This test verifies that a note can be added to the list of notes.
-   [frontend/react/tests/pages/Home.test.jsx ("should render the Start Race button")](https://github.com/COMP-4350-Group-8/comp4350-project/blob/cd2df183810581ee2abfae6d20ca133c722871aa/frontend/react/tests/pages/Home.test.jsx#L18). This test verifies navigation between the Home and Create Race pages.

### Acceptance Tests

We have not completed any user stories, so we do not have any acceptance tests.

## Reproducible environments

See [Start Recipe Shop](StartRecipeShop.pdf)
