# React-Native-101
How to install React Native and get started with a project. Also tips on how to make your project as a repo in GitHub. 

## Installation 
Go to Facebook's installation [tutorial](https://facebook.github.io/react-native/docs/getting-started.html) and follow the steps with these configurations: 
- React Native CLI Quickstart 
- Development OS: macOS
- Target OS: Android or iOS (see notes) 
Note: For Android, have Android Studio installed. For iOS, have Xcode installed.

The following should be installed (detailed instructions on Facebook's website):
1. Install Node & Watchman using Homebrew.
  ```
  brew install node 
  brew install watchman
  ```
Note: Watchman is a tool by Facebook for watching changes in the file system. It is highly recommended you install it for better performance. 

2. Xcode and CocoaPods 
  `sudo gem install cocoapods`

3. React Native Command Line Interface 
   - npx this ships with Node.js, use this command to check the version 
   `npx react-native <command>`

## Installation Debugging 
The following steps should help in debugging. 
1. Go to the home directory. 
2. Type `react-native -v` to verify the version. 
   - If you get `command not found` then the following steps that edit your `.bash_profile` may help. 
     1. `ls-la` 
     2. `sudo nano .bash_profile`
        - `sudo` forces your computer to give access to that file 
        - `nano` gives you the ability to write/edit it 
     3. To edit: `Control + O` then press `Enter` 
     4. To save/write: `Control + X` and you may need to type `Y` for "yes" to write. 
     5. Copy and paste the path from the tutorial website and paste this at the bottom IF you are having trouble running it. 
        ```
        npm set prefix ~/.npm
        PATH="$HOME/.npm/bin:$PATH"
        PATH="./node_modules/.bin:$PATH"
        ```
     6. Then, you have to type the following command to link your path to your downloaded components: 
        `source ~/.bash_profile`
        - This command sets your path. DO NOT IGNORE.
        
## Starting your Project
1. Use terminal to change to the directory you want to make your project.
2. Since we want to navigate between screens, we must install *React Navigation*. This gives us the ability to use Tabs, Containers, Stack Navigators, etc.. 
   - `npm install react-navigation`
   - `npm install react-native-gesture-handler react-native-reanimated`
   - Now, you must link React Navigation with React Native: 
     - For iOS: (first, make sure you have cocoapods installed)
            - `cd ios`
            - `pod install`
            - `cd ..`
     - For Android: 
            - Must make changes to MainActivity.java 
              - android>app>src>main>java>MainActivity.java
              - Copy the text from the link above and remove the ‘+’ signs 
   - Now, if you go to package.json you can see react-native-gesture-handler and react-native-reanimated are in dependencies. 
IMPORTANT: If you get an error “requiring unknown module…” then restart your metro bundler on terminal.
3. `react-native init sampleApp`
4. `App.js` will be the file you need to edit at first.
5. To run in Android: 
   - `react-native run-android`
   - You need to have the android emulator on from Android Studio running before you run the command, otherwise your computer might crash. 
     - Open Android Studio-> AVD Manager -> Create Virtual Device 
6. To run in iOS: 
   - `react-native run-ios`
   - Have XCode open first.

## Other Notes 
- The `-g` in npm install means that react native is installing globally 
- Your `.bash_profile` is important because it gives you access to downloaded components like react native. 
  - If you don’t have one then make one!!
  
If you still get `command not found` when trying to init a React Native project, then it’s probably because you don’t have a PATH established to run React Native. If this is the case, please follow the following steps: 
1. Type this command in Terminal to establish a PATH:
   - `source $HOME/.bash_profile`
   - If `no such file found` error, then it is fine and ignore this command

## Creating a GitHub Repository 

### How to clone a repo:

1. After creating a repo on GitHub, click the clone button on the repo page.
2. Copy the HTTPS link.
3. Open terminal. 
4. Navigate to the location where you want to clone this repo locally. 
5. Type `git clone <https-link>` on the command line and press return.

### How to work in the repo:

Whenever you want to make changes, **always make a new branch** with a name that is descriptive of the general changes you are going to make. I recommend making branch names all lowercase with dashes instead of underscores so it's easier to type fast on the command line when pushing/pulling/switching branches. Making branches ensures that we can maintain version control and review each others code before merging it with our master code.

### How to make a new branch: 
1. Enter `git checkout -b <name-of-branch>` on the command line in your local repository.
2. To check which branch you are in, enter `git branch` on the command line.

### How to push your changes to the remote repository (on GitHub):

1. Make sure you are in the correct branch by typing `git branch` on the command line (like above). To enter a different branch, type `git checkout <name-of-existing-branch>`.
2. Pull any changes that may have been made on your branch BEFORE pushing any of your changes by typing `git pull origin <name-of-branch>`
2. See the changes you have made to make sure you are changing the correct things by typing `git status`. You should see a list of the changes you have made.
3. You can choose to push all your changes in one go by typing `git add -A` on the command line, or you can select specific changes you wish to push by typing `git add "name-of-file"`
4. Commit your changes with a message that describes the changes you made by typing `git commit -m "message about changes"`
5. Push your changes to the branch by typing `git push origin <name-of-branch>`

### MAIN STEPS

1. CHECK WHAT BRANCH YOU'RE IN: `git branch`
2. PULL CHANGES: `git pull origin <name-of-branch>`
    * make changes
3. CHECK CHANGES YOU'VE MADE: `git status`
4. STAGE YOUR CHANGES: `git add -A` or `git add <name-of-file&path>` 
5. *optional* CHECK STAGED CHANGES: `git status`
     * Can do `git reset HEAD <name-of-file>` to unstage
5. COMMIT YOUR CHANGES: `git commit -m "message"`
6. PUSH CHANGES TO REMOTE REPO: `git push origin <name-of-branch>`

### Pull Requests:

* When you are ready to merge the changes you have made on your branch with the master branch, you should start a pull request and ask someone to review your code on your branch. Once it has been reviewed, we can merge it with the master.
* You can create a pull request on the repository website on GitHub.

### Creating a .gitignore:

You must create a .gitignore so that you don't push unnecessary/annoying files (such as .DS_Store files) to the repository. For our purposes, this should be enough for now:

**.gitignore**
```
*~
*.
.gitignore
.DS_Store
```

### Resources

* [Git Command Line Cheat Sheet](https://gist.github.com/davfre/8313299)
* [Terminal Command Line Cheat Sheet](https://www.git-tower.com/blog/posts/command-line-cheat-sheet)



