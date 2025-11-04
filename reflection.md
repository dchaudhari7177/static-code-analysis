1.	Which issues were the easiest to fix, and which were the hardest? Why?
Easiest: The simplest issues to fix were style-related warnings such as missing
docstrings, non–snake_case function names, replacing %-style string formatting with f- strings and unused imports. These required straightforward edits without affecting
functionality.
Hardest: The most challenging issue was handling the global variable (stock_data) warning. Removing it required structural refactoring—passing the dictionary between functions instead of using shared state—so I chose to retain it intentionally for
simplicity.


2.	Did the static analysis tools report any false positives? If so, describe one example.
Yes, Pylint’s global-statement (W0603) warning can be considered a false positive in this context.
The code intentionally used a global variable for maintaining inventory state in a simple script, not a production system.
While it’s generally bad practice, it wasn’t harmful here, so addressing it would add unnecessary complexity.


3.	How would you integrate static analysis tools into your actual software development workflow?
Local Development:
Run tools like ffake8, pylint, and bandit before committing code to catch issues early. Use editor integrations or pre-commit hooks to enforce linting automatically.
Continuous Integration (CI):
Integrate static analysis into CI pipelines (e.g., GitHub Actions or Jenkins).
Set thresholds to block merges if the lint score drops below a certain level or if security warnings appear.


4.	What tangible improvements did you observe in the code quality, readability, or potential robustness after applying the fixes?
The code became cleaner and more readable due to proper naming, consistent formatting, and added docstrings.
 
Using context managers (with open(...)) improved robustness by preventing resource leaks.
Replacing bare excepts with specific exception types improved error clarity and safety. Removing eval() eliminated a potential security risk, making the script safer to run.
Replacing %-style formatting with f-strings (used in logs.append(...) and print statements) improved readability and made the string expressions clearer and less error-prone; f-strings are also more efficient and easier to maintain.
Overall, the code is now easier to maintain, safer, and closer to production-ready quality.
