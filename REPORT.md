\# TP2 Report — Group 3: DevOps \& NetOps



\## Part 1 — Python Environment and uv



\- Inspected the global Python environment using `scripts/inspect\_env.py`.

\- Inspected the project virtual environment using `uv run python scripts/inspect\_env.py`.

\- Global Python: 3.12.4.

\- Project virtual environment Python: 3.14.8.

\- Confirmed that `uv run` executes Python inside the project virtual environment.

\- Added `.gitignore` to exclude `.venv`, `.env`, build output, Python caches, and test caches.

\- Initial Git commit: `d051ef9`.



\## Part 2 — GitHub REST API



\- Installed `requests` and `python-dotenv` using `uv add`.

\- Configured environment variables through `.env`.

\- Implemented configuration validation in `config.py`.

\- Implemented a GitHub API client in `client.py`.

\- Endpoint: `GET https://api.github.com/user`.

\- Authentication: Bearer token supplied through `GITHUB\_TOKEN`.

\- User-Agent: `Epita-Student-CLI`.

\- Verified a successful live API response.

\- Returned status: `LIVE\_SUCCESS`.

\- Authenticated username: `reeaarana`.

\- Public repositories: 16.

\- Followers: 0.

\- Verified that `.env` is ignored by Git and that the real token is not included in the report.



\## Part 3 — Dependency Management and Testing



\### Dependency Management



\- Added project dependencies and development tools using `uv`.

\- Used `uv tree` to inspect the dependency tree.

\- Updated `pyproject.toml` to define project metadata, dependencies, and the CLI entry point.

\- Generated and maintained `uv.lock` to record resolved dependency versions for reproducible installations.

\- Added `pytest` for automated testing.

\- Ran `uv run pytest` successfully: \*\*1 test passed\*\*.

\- Built the package using `uv build`, generating both a source distribution (`.tar.gz`) and a wheel (`.whl`).



\### CLI Installation Verification



\- Uploaded the package distributions to TestPyPI using Twine.

\- Created a separate virtual environment to verify installation.

\- Installed the published package from TestPyPI.

\- Executed `epita-group3-cli.exe` successfully.

\- Verified that the CLI displayed the GitHub profile information, including username, public repositories, and followers.

\- Confirmed that the GitHub API request returned `LIVE\_SUCCESS`.



\### Security



\- Stored the GitHub token in a local `.env` file rather than hardcoding it in the source code.

\- Added `.env` to `.gitignore` to prevent accidental commits of secrets.

\- Kept API tokens out of the project report and submission files.



\## Part 4 — CLI Packaging and TestPyPI Deployment



\### Package Build

Built the source distribution and wheel using `uv build`.



\- Source distribution: `epita\_reeaa\_rana\_epita-0.1.0.tar.gz`

\- Wheel: `epita\_reeaa\_rana\_epita-0.1.0-py3-none-any.whl`



\### TestPyPI Publication

Successfully uploaded both distribution files to TestPyPI using Twine.



Package URL: https://test.pypi.org/project/epita-reeaa-rana-epita/0.1.0/



\### Installation Verification

Created a separate virtual environment named `.venv\_test` and installed version `0.1.0` from TestPyPI.



\### CLI Verification

Ran `epita-group3-cli.exe` from the isolated environment. The CLI displayed the GitHub profile information, including API status, username, public repository count, and follower count.



\*\*Result:\*\* Package build, publication, installation, and CLI execution were successful.







\### Part 5 — Debugging Challenge



\*\*Tool used:\*\* Python interactive debugger (`pdb`).



\*\*Diagnosis:\*\* The API record stores `volume` and `weight` as strings. The debugger confirmed that `record\["volume"]` and `record\["weight"]` have type `str`.



\*\*Inspection:\*\* I used breakpoints and the `where`, `up`, `down`, `p`, and `type()` commands to inspect the call stack and variable types. In `compute\_weighted\_metric()`, the values were `450.0` and `3.0`, both of type `float`.



\*\*Fix:\*\* Convert numeric fields to floating-point numbers when parsing the API records, before performing arithmetic.



\*\*Verification:\*\* Running `uv run python scripts/debug\_challenge.py` completed successfully and printed the aggregate telemetry result.
