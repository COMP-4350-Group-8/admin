# Worksheet Info

## Worksheet Location

- This document, or in our wiki

## Worksheet 2 Draft

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
- Testing Script Link: $\color{Apricot}{[TODO]}$
- Texts Executed:
	- $\color{Apricot}{[TODO]}$
	- $\color{Apricot}{[TODO]}$
	- $\color{Apricot}{[TODO]}$ etc.
- Testing Results: $\color{Apricot}{[TODO]}$

$\color{Apricot}{[TODO]}$ (Snapshot of regression testing script execution)

#### Backend:

- Tool: xUnit.net
- Testing Script Link: $\color{Apricot}{[TODO]}$
- Texts Executed:
	- $\color{Apricot}{[TODO]}$
	- $\color{Apricot}{[TODO]}$
	- $\color{Apricot}{[TODO]}$ etc.
- Testing Results: $\color{Apricot}{[TODO]}$

$\color{Apricot}{[TODO]}$ (Snapshot of regression testing script execution)

### Testing slowdown

#### Have you been able to keep all unit tests & integration tests in your test plan?

Yes*
#### Have you created more than one test plan depending on type of release?

"No". The closest we have to more than one test plan is how our GitHub workflow works. In our workflow you are able to specify which tests to run, and in what environment. Some of these features may not be in proper state.

### Not testing

#### What have you not tested? 

- Flutter (Client)
- Automated Tests from frontend to backend
- $\color{Apricot}{[TODO]}$

#### Current System Diagram.

$\color{Apricot}{[TODO]}$

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

- $\color{Apricot}{[TODO]}$

###### Coverage Reports

- $\color{Apricot}{[TODO]}$

##### Backend

- $\color{Apricot}{[TODO]}$

###### Coverage Reports

- $\color{Apricot}{[TODO]}$

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

$\color{Apricot}{[Answer:]}$

#### Robert

- Created Documentation Structre (I have not maintained it well though)
- Setup GitHub Workflows for CI (and some CD) integration.
- Added Repository variables to control GitHub Workflows for CICD
	- Said variables control what is run where & when.
- Flutter Bug; Offical Documentation for a feature in Flutter's API was wrong. All resources I found were not update. In the end I think I found a solution that should be stable (specify relating to the bottom Nav_Bar)

#### Brett

$\color{Apricot}{[Answer:]}$

#### Azat

Figuring out the relations in the database and setting them up

#### Shaun

$\color{Apricot}{[Answer:]}$