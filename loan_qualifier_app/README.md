# Loan Qualifier 
**This project is a loan qualification organizer. It sifts through multiple bank programs and lets the applicant know which programs suit their needs.**


---

## Technologies

This program was written in Python 3.9.7 and uses the following libraries:<br />
*sys*<br />
*fire*<br />
*questionary*<br />
*csv*<br />
*pathlib*<br />


---

## Installation Guide

To run the program, open up [app.py](app.py)


---

## Usage

Here are the filters that I'm using:

[credit_score_filter](qualifier/filters/credit_score.py)<br />
[debt_to_income_filter](qualifier/filters/debt_to_income.py)<br />
[loan_to_value_filter](qualifier/filters/loan_to_value.py)<br />
[max_loan_size_filter](qualifier/filters/max_loan_size.py)<br />

Here are the calculators I'm using: 
[calculators](qualifier/utils/calculators.py)<br />

Here is a function for file input/output 
[fileio](qualifier/utils/fileio.py)<br />

<br />
Here is where I modified the code to ask whether the user wants to save to a CSV, and to do so if chosen:

```python
def save_qualifying_loans(qualifying_loans):
    answer = questionary.text("Do you want to save? (yes or no)").ask()
    if answer == ("yes"):
        csvpath = Path("my_output.csv")
        with open(csvpath, 'w', newline='') as csvfile:
            csvwriter = csv.writer(csvfile)
            for row in qualifying_loans:
                csvwriter.writerow(row)
    else:
        print ("will not save")
```
<br />
Here's where I edited the code to account for 0 qualifying loans: <br />

```python
   if len(bank_data_filtered) == int(0):
        print("Because no loans were found, you are being exited from the program.")
        sys.exit()
 
    return bank_data_filtered
```

![picture of a tree](tree_picture.png)

---

## Contributors

Shout out to the UC Berkeley Fintech program

---

## License

Anyone can use this
