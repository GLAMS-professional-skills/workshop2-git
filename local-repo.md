*This is an altered version of content spit out from ChatGPT*

# Step 1: Install Git

If you haven't already, install Git on your computer. You can download it from the official website: [Git](https://git-scm.com/)

# Step 2: Set Up Git

Each commit (version) created contains some data, including the previous version, the time of creation, but also logs the name and email of the author.
This information does not need to be real however if this information matches your GitHub account, then the commits will be associated to your account on GitHub when viewed on the site.


Open a terminal or command prompt and set up your Git username and email address using the following commands:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

# Step 3: Create a New Repository

Create a new directory for your project and navigate into it:

```bash
mkdir my-project
cd my-project
```

Initialize a new Git repository:

```bash
git init
```

# Step 4: Add Some Files

Create some files in your project directory. For example, let's create a README.md file:

```bash
echo "# My Project" >> README.md
```

You can also just create from the file browser, or any other way you like.

# Step 5: Add Files to the Staging Area

Add the files you want to track to the staging area:

```bash
git add README.md
```

# Step 6: Commit Your Changes

Commit the changes to your local repository:

```bash
git commit -m "Initial commit"
```

# Step 7: Make More Changes and Commit

Make further changes to your files if desired. For example, let's add some content to README.md:

```bash
echo "This is my first project using Git." >> README.md
```

Add and commit these changes:

```bash
git add README.md
git commit -m "Added content to README.md"
```

Try some of these commands in your next commits:

```bash
git add -A
```

To add everything*

```bash
git commit -am "<message>"
```

To stage changes to tracked files and commit in one go.

# Step 8: Publish to GitHub

Go to GitHub and sign in (or create an account if you don't have one).

Create a new repository on GitHub. Give it a name, optionally add a description, and choose other settings as needed.

After creating a new blank repository, you should receive instructions to push an existing repository, follow them.


# Step 9: Check Your GitHub Repository

Go back to your GitHub repository in your browser and refresh the page. You should see your files there.

That's it! You've now created a Git repository, made some commits, and published it to GitHub.
