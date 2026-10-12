# ESEP Grade Calculator

This repository contains a small Go library for calculating a final course grade from three grade categories: assignments, exams, and essays.

## What the project does

The library stores grades in separate lists and then computes a weighted final grade. The current implementation uses the following weighting:

- Assignments: 50%
- Exams: 35%
- Essays: 15%

After calculating the weighted numeric result, it converts that value to a letter grade:

- 90 or above: A
- 80 to 89: B
- 70 to 79: C
- 60 to 69: D
- below 60: F

## Project structure

- `grade-calculator/go.mod` — Go module definition
- `grade-calculator/grade_calculator.go` — core grade calculation logic
- `grade-calculator/grade_calculator_test.go` — unit tests for the grade logic

## Requirements

- Go 1.24 or later

## Getting started

From the project root, run:

```bash
cd grade-calculator
go test ./...
```

To also generate a coverage report:

```bash
cd grade-calculator
go test -coverprofile=coverage.txt ./...
```

## Using the calculator

The package is currently defined with the package name `esepunittests`, while the module path is `esep/grade-calculator`.

Example usage:

```go
package main

import (
    "fmt"
    esepunittests "esep/grade-calculator"
)

func main() {
    gradeCalculator := esepunittests.NewGradeCalculator()

	gradeCalculator.AddGrade("open source assignment", 80, esepunittests.Assignment)
	gradeCalculator.AddGrade("exam 1", 81, esepunittests.Exam)
	gradeCalculator.AddGrade("essay on ai ethics", 85, esepunittests.Essay)

	finalGrade := gradeCalculator.GetFinalGrade()
}
```

### Grade types

The calculator accepts the following grade categories:

- `esepunittests.Assignment`
- `esepunittests.Exam`
- `esepunittests.Essay`