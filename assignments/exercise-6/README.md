
# Exercise 6: Create Reusable Workflows with GitHub Actions

In this exercise, you will create reusable workflows and use it.

## Steps

### 1. Create a Reusable Workflow
- **Directory**: Navigate to the `.github/workflows/` directory in your repository.
- **Create the Workflow File**: Create a new file named `ci.yml`.

### 2. Configure the Reusable Workflow
- **Name the Workflow**: `"Reusable CI Workflow"`.
- **Trigger the Workflow**: Use the `workflow_call` trigger to allow other workflows to invoke it.
- **Define Workflow Inputs**:
    - Specify required inputs, such as the Java version and distribution.
- **Add the Following Steps**:
    1. **Checkout the Repository Code**:  
       Use `actions/checkout@v3`.
    2. **Set Up Java Environment**:  
       Use `actions/setup-node@v3` and configure it to use the Node.js version passed as an input.
    3. **Install Dependencies**:  
       Run:
       ```bash
       mvn compile
       ```
    4. **Run Tests**:  
       Execute:
       ```bash
       mvn test
       ```
    5. **Project**:
        Use the project from exercise 5 in the workflow with the example code: 
        ```bash
       working-directory: assignments/exercise-5
       ```
        to specify the location of the project, where the "assignments/exercise-5"
        is the location of the project from exercise 5
### 3. Create a Workflow to Call the Reusable Workflow
- **Directory**: In the `.github/workflows/` directory of the same repository, create a new file named `main.yml`.
- **Configure the Workflow**:
    - **Name the Workflow**: `"CI"`.
    - **Trigger the Workflow**: Set it to run on pushes to the `main` branch.
    - **Call the Reusable Workflow**:
        - Use the `uses` keyword to reference the reusable workflow.
        - Provide the required inputs such as the Java version and distribution.

### 4. Verify the Workflows
1. **Commit and Push Changes**:  
   Push the `ci.yml` and `main.yml` files to the repository.
2. **Observe Workflow Execution**:  
   Go to the "Actions" tab in your GitHub repository to verify the workflow runs.
3. **Check Logs and Results**:  
   Confirm that the reusable workflow is called and all steps execute successfully.

Happy coding!
