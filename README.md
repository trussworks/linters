# linters
Open source custom Truss linters that can be shared across projects.


## List of Linters
### ATO linter:
Truss developed a linter to ensure our code follows security authorization to operate guidelines. 

Since this linter is being used in the MyMove project, to run it from that repository:
```golang
go install ./cmd/...
ato-linter ./pkg/...
```
### AppContext Linter:
For our Go applications we want to manage calls to the database, only certain directories and files should be making direct calls to the database using `pop.Connection`, while the majority of our Go files will receive the context from those DB calls only (`appContext`).

This linter catches when `pop.Conneciton` is passed into a struct of a file that we do not need to make a direct DB call in. This is done to remind engineers that `appContext` can be passed into the function as the first parameter instead.
Currently this linter is being implemented in the MyMove repository, and can be run with:
```golang
go install ./cmd/...
appcontext ./pkg/...
```