# Worksheet Info

Please Read Wiki, Specifically [System Design](https://github.com/COMP-4350-Group-8/admin/wiki/System-Design)

## Worksheet Location

- This document, (with links to our wiki)

## Worksheet 2 Content

### Regression testing

> [!NOTE]
> 
> Describe how do we run regression testing
> 
> - Which Tool is used
> - Link to regression testing script
> - Which tests are executed?
> - Results of regression testing
> - Snapshot of regression testing script execution

#### Flutter:

- Tool: n/a
- Testing Script Link: n/a
- Texts Executed: n/a
- Testing Results: n/a

#### REACT:

- Tool: Vitest
- Testing Script Link: See [CI Workflow](https://github.com/COMP-4350-Group-8/comp4350-project/blob/ec0cfde7accd3c8588fe9cf2534fcb109552cd0a/.github/workflows/ci-workflow.yml#L135)
- Texts Executed:
	- All React tests are run in our CI pipeline; there is no distinction between the normal tests and the regression tests. The tests for the React frontend run quickly enough that there was no need to trim the numbers down for regression tests.
- Testing Results:
	- Test Files  4 passed
	- Tests  13 passed
  	- See [action report (Run REACT Unit Tests)](https://github.com/COMP-4350-Group-8/comp4350-project/actions/runs/11748732119/job/32733457784) for full report.

#### Backend:

- Tool: xUnit.net
- Testing Script Link: $\color{Apricot}{[TODO]}$
- Texts Executed:
	- $\color{Apricot}{[TODO]}$
- Testing Results: $\color{Apricot}{[TODO]}$

$\color{Apricot}{[TODO]}$ (Snapshot of regression testing script execution)

### Testing slowdown

#### Have you been able to keep all unit tests & integration tests in your test plan?

Yes*
#### Have you created more than one test plan depending on type of release?

"No". The closest we have to more than one test plan is how our GitHub workflow works. In our workflow you are able to specify which tests to run, and in what environment. Some of these features may not be in proper state.

### Not testing

#### What have you not tested? 

- Flutter (Client) - N/A (for sprint 2)
- Automated Tests from frontend to backend

#### Current System Diagram.

See [Wiki: System-Design](https://github.com/COMP-4350-Group-8/admin/wiki/System-Design)

#### Testing Coverage

> [!NOTE]
> 
> For each tier of your system, which layers of that tier are:
> 
> - Fully tested (80%+)
> - Mostly tested (20-80%)
> - Somewhat tested (0-20)
> - Not tested
>
> Coverage reports for tested tiers

##### Flutter

n/a

###### Coverage Reports

- n/a

##### REACT

The only parts of our React frontend that are not tested are:

-   `main.jsx` because it has no functionality to test
-   `AddCourse.jsx` because it has only one function which talks to the backend and this function is mocked during testing
-   The link between the frontend and the backend is not covered by automated testing

Everything else in the React frontend is fully tested.

###### Coverage Reports

| File                 | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s |
| -------------------- | ------- | -------- | ------- | ------- | ----------------- |
| All files            | 86.11   | 92.3     | 88.23   | 86.11   |
| src                  | 38.46   | 50       | 50      | 38.46   |
| App.jsx              | 100     | 100      | 100     | 100     |
| main.jsx             | 0       | 0        | 0       | 0       | 1-16              |
| src/components/forms | 100     | 100      | 100     | 100     |
| MarkerForm.jsx       | 100     | 100      | 100     | 100     |
| RaceForm.jsx         | 100     | 100      | 100     | 100     |
| src/components/map   | 100     | 100      | 100     | 100     |
| Gmap.jsx             | 100     | 100      | 100     | 100     |
| src/components/ui    | 100     | 100      | 100     | 100     |
| Card.jsx             | 100     | 100      | 100     | 100     |
| src/pages            | 50      | 75       | 75      | 50      |
| AddCourse.jsx        | 0       | 0        | 0       | 0       | 1-19              |
| CreateRace.jsx       | 100     | 100      | 100     | 100     |
| Home.jsx             | 100     | 100      | 100     | 100     |

##### Backend
Not covered:
- Any Controller classes

###### Coverage Reports

You can see backend coverage report [here](https://htmlpreview.github.io/?https://github.com/COMP-4350-Group-8/admin/blob/main/sprints/sprint-2/coverage-report/backend/index.html)

### Profiler

> [!NOTE]
> 
> Run a profiler on your API while using it,
> - Attempt to visit every endpoint,
> - Which endpoint is the slowest?
> - Is that fixable? Why or why not?

#### Endpoints:

- $\color{Apricot}{[TODO]}$

#### Profiler Output

$\color{Apricot}{[TODO:]}$ (link, image, text, etc.)

### Last dash

#### What issues do you foresee in the next (and final) sprint?

- Flutter implementation
	- Android APK creation - ToS Hurdles
- Security hardening
- Completing rest of features (most)
- Documentation
- Frontend
	- Map rendering

### Show off

> [!NOTE]
> 
> Show off your best work (code, UI, design, connections, nice mocks)
> 
> - Remember da Vinci said, “Simplicity is the ultimate sophistication”.
> - Well refactored code shouldn’t be complicated!
> - Each member should commit their own update (we’ll check the logs!)

#### Owen

- API design
- backend setup and structure
- dockerization and CD to docker hub

#### Robert

- Created Documentation Structre (I have not maintained it well though)
- Setup GitHub Workflows for CI (and some CD) integration.
- Added Repository variables to control GitHub Workflows for CICD
	- Said variables control what is run where & when.
- Flutter Bug; Offical Documentation for a feature in Flutter's API was wrong. All resources I found were not update. In the end I think I found a solution that should be stable (specify relating to the bottom Nav_Bar)

#### Brett

My best work is the tests for the React frontend. I had worked with React in the past but hadn't written tests for a React app before, so it was cool to learn what those tests can look like. I'm particularly happy about the mocks that some tests required, like the mocks for testing form submission [here](https://github.com/COMP-4350-Group-8/comp4350-project/blob/15ae35b0140ec5c58ecc2efa40893376c5c6c674/frontend/react/tests/components/forms/RaceForm.test.jsx#L80) and [here](https://github.com/COMP-4350-Group-8/comp4350-project/blob/15ae35b0140ec5c58ecc2efa40893376c5c6c674/frontend/react/tests/App.test.jsx#L9). Both mocks are used to confirm that the race creation form couldn't be submitted with incomplete data. The first mock is a function which is passed as a prop to the test component and checked later to confirm it wasn't called. The second mock replaces a function in an import so that the tests can complete the form submission flow without triggering the fetch logic.

#### Azat

The most I am proud of is setting up a relational database. I took database almost 5 years ago and everything was on paper. So i had no practical experience in doing databases. MySql is my first database and I am very proud of how it went.

#### Shaun

My best work is the React frontend. It is my first time working on the frontend as well as with react. I'm happy about the front design which was both interactive and user-friendly. I included a Google Maps directly on the site using an iframe so users can explore locations without leaving the page. To keep everything running smoothly, I set up a system to manage the app’s state, which keeps data consistent and updates the interface as users interact with it.
