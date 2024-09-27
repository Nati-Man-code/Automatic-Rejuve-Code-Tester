This repo is designed to automatically test project when changes are made to the codebase.
It checks for changes in adapters, writers, configurations, and the main script. Depending on what
changes, it triggers specific actions to ensure the system is tested only where it's needed. Here’s a
breakdown of each part of the workflow:
1. Triggers:
• The workflow runs on pushes or pull requests to the "main" branch.
• It only watches specific parts of the codebase like the adapters folder, main script, the
writer, and the configuration file to decide when to trigger a test.
2. it Detect Changes:
• This step checks what files were changed between the current commit and the
previous one. It identifies if there were changes to the adapters, writers, config file,
or the main script.
• It uses regular expressions to detect which specific files or directories were affected
and stores that information (e.g., changed adapters, changed writers, or if the main
script or config changed).
3. Prepare test Config:
• If there are changes in adapters or the config file, this job generates a specific test
configuration file based on the changed adapters or config.
• If no changes in adapters or config are detected, it defaults to using a sample
configuration file.
4. Run Tasks:
• This job is where the actual testing happens.
• It checks the changes and runs the necessary tests based on those. For example, if the
main script changed, it runs all adapters with the full sample config. If writers
changed, it runs all adapters with the changed writer. For the config and adapter
change it run that specific node or edge from the config or that specific changed
adapter with all the three writers.
