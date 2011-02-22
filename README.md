# Ledger.tmbundle

Ledger.tmbundle is a TextMate bundle for working with [ledger](https://github.com/jwiegley/ledger) documents.

It is a work in progress, but has support for the following functions:

 - Current Balance (Non Virtualized)
 - Current Balance (Virtualized)
 - Net Worth
 - Distribute Income
 - Expense Report

To activate these commands, use ^⌘L and you'll get a menu to choose the command.

It also has a tab completed Snippet to enter a new ledger entry, `ent`

## Workflow

This bundle abides by my workflow, which heavily uses the concept of virtual transactions and accounts. If you are unfamiliar with this concept, please read the PDF manual for ledger.

When you get income, you should run the "Distribute Income" command by selecting the to: and from: accounts in your ledger entry, and activating the command. You will then get prompts to assign income to each "virtual bucket" until the balance reaches zero, or you cancel the operation. If you cancel the operation, the remaining balance will be assigned to the "Income:Unassigned:Salary" bucket.

When you spend money, the balance of these virtual buckets will slowly rise to zero. If the balance of a bucket is already zero, or makes it go over zero, you will need to balance the output. You must have money in your "Income:Unassigned:Salary" bucket. Here is a simple example of an entry like this:

	2011/02/18 * McDonalds
		Expenses:Dining					$6.51
		Liabilities:American Express
		(Income:Unassigned:Salary)		-$6.51
		(Expenses:Dining)				-$6.51

In this example, I bought something from McDonalds, but didn't have money in my Dining bucket. So I take it out of "Income:Unassigned:Salary".

You can see balances of your virtual buckets by running the "Current Balances" command. This will tell you how much money in each bucket you have left.

If you'd like to see how much you have actually spent, run the "Current Balances - Non Virtualized"

These commands are works in progress, so please file issues if you find problems. Currently, they will only display total values, you cannot choose a date range yet.

# Notes

Make sure that the `ledger` command is located in the PATH shell variable in the TextMate preferences.

Some of these files (Syntaxes and Preferences) were borrowed from [Benjamin Cullen-Kerney](https://github.com/bak/Ledger.tmbundle).