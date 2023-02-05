## Exercise 1 - Create Your Own React App

**Goal:** We set up our own React app, which we will use as a basis for a memory game that we will implement throughout this workshop.

### Steps
1. Create your React app by choosing one of the following options (replace `my-app` with the name for your app):
    * Execute the following command:
    ```shell
   npx create-react-app my-app --template typescript
    ```
   * If you are using IntelliJ, you can alternatively create your app by creating a new project in IntelliJ and selecting React from the list of JavaScript templates.
   Make sure to set your app name as name for the project and to check the TypeScript option. 
   This will automatically execute `create-react-app` for you in your new project.
   
2. Navigate with a terminal into your new app's folder.

3. Start your app via
   ```shell
   npm start
   ```

4. Take a look at the tests. You can start them via your IDE or via
   ```shell
    npm test
   ```

5. Have a look at the generated files. 
   * What files were created?
   * Try to change something and see the result. 
   * Add your own "Hello World" component.

6. For team collaboration in the upcoming exercises: Push your code to a common repo via
   ```shell
   git remote add origin ssh://git@bitbucket.int.tngtech.com:122/msd/react-workshop-2023-02.git
   git push -u origin HEAD:[branch-for-your-group]
    ```
   
______________

**Note:** If you or someone else in your group doesn't have access to TNG's bitbucket, 
you can use Codesandbox as a fallback:
* Go to https://codesandbox.io and login
* Click on "Create", select "React Typescript"
* Enable live collaboration at menu item "Live" on the left
