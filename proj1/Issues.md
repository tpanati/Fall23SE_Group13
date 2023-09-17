# Issues and Solutions with Assigned Projects

Here are the issues encountered while trying to run the five projects assigned to us, along with possible ways they could have been rectified:

- In the Slashbot project, the code appends the directory `"C:/NCSU/Sem 1/SE/Project 3/slashbot/"` to the Python `sys.path` list (https://github.com/secheaper/slashbot/blob/main/src/bot.py#L24C1-L29C1), violating best practices by hardcoding values in the source code. So as a user, it led to import errors as this path is different from where the project was cloned in my local PC (the path may differ in different environments). This practice hinders code portability, maintenance, and reusability, as hardcoded values are less adaptable to different environments, require manual updates, and can introduce errors. To avoid hardcoding, we wish to use configuration files, environment variables, or command-line arguments for more flexible and maintainable code.

- The code formatter used in the Slashbot project, specifically the `black.yml` file, lacks comments or explanations, violating the software engineering best practice of "Code Documentation and Comments." This omission can hinder collaboration and make it challenging to understand and modify the workflow configuration. To adhere to best practices, we wish to include informative comments or documentation within the YAML file, explaining the purpose of each section and its intended behavior, making it easier for others to comprehend, contribute, and maintain the workflow configuration.

- Slashbot stores user data as Python objects in binary files with a `.pickle` extension. When the code needs to retrieve user data, it reads the pickle file with the matching user ID (chat ID), deserializes the data, and returns it as a Python object - https://github.com/secheaper/slashbot/blob/main/src/bot.py#L1259-L1277. While this approach allows for persistent data storage, it can lead to issues when existing pickle files of the developers are present in the `./data` directory (https://github.com/secheaper/slashbot/tree/main/src/data) for new users. The software takes care of generating a new .pickle file with the user's chat ID on running the application (https://github.com/secheaper/slashbot/blob/main/src/bot.py#L152-L156). Developers pushing locally generated `.pickle` files to the main repository violates the best practice of "Version Control and Collaboration." This practice increases repository size, causes potential merge conflicts, and poses security concerns. To rectify this, we wish to add `.pickle` files to the project's `.gitignore` file to exclude them from version control, ensuring a cleaner and more efficient collaboration environment while preserving user data locally.

These issues and solutions highlight the importance of adhering to best practices in software engineering to enhance code quality, maintainability, and collaboration.