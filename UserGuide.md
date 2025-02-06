# **User Guide for Salto Interview Exercise**
# **Salesforce Setup**
## **Creating a Salesforce Developer Account and generating and API token**
1. Go to [Salesforce Developer](https://developer.salesforce.com/signup) site and create a developer account
2. Once signed in, go to top right-corner and click on the profile picture
3. Click on the settings
4. In quick find, search for "Reset My Security Token"
5. Click Reset Security Token and the token will be sent to your email address

# **Salto Setup**
## Download the Binary
1. To install Salto's command line interface (CLI) download the latest binary from Github page: [Releases](https://github.com/salto-io/salto/releases/tag/v0.5.0)
2. Copy the binary to a folder and add it to the path
## Create a new Salto Workspace
Create a new Salto workspace to store all the Salto NaCL files. Salto init will prompt for a name for first environment, just accpet the default for now.
```
mkdir quickstart
cd quickstart
salto init
```
## Add a new service to the workspace
Next, connect the workspace to Salesforce account, by running:
```
salto service add salesforce
```
This command will prompt to enter the credentials fr the acount. Add the credentials.
# Implement Development Project in Salesforce
## Create Leads Queue
1. Go to Setup by clicking on the gear icon in the top-right corner and select Setup
2. In the Quick Find box, type Queues and select Queues under the Users section
3. Click 
### a. Create Hot Leads Queue
1. Enter Queue Name: Hot Leads. Unique Name would be filed in automatically
2. Select Lead from Available Objects
3. In the Queue Members add the user who should have access. In this case Manisha
4. CLick Save
### b. Create Cold Leads Queue
1. Enter Queue Name: Cold Leads. Unique Name would be filed in automatically
2. Select Lead from Available Objects
3. In the Queue Members add the user who should have access. In this case Manisha
4. Click Save
## Create Lead Assignment Rules
1. In Setup, search for Navigate to Lead Assignment Rules
2. Click New and name it Assign Leads
### a. Assignment Rule for Hot Lead
1. Click New in Rule Entries
2. In Step 1, Add Sort Order as 1
3. In Step 2, Select the Field as "Lead: Score"
4. Select the Operator as "greater or equal"
5. Add the value as 60
6. In Step 3, Select the Queue as Hot Leads
7. Click Save
### b. Assignment Rule for Cold Lead
1. Click New in Rule Entries
2. In Step 1, Add Sort Order as 2
3. In Step 2, Select the Field as "Lead: Score"
4. Select the Operator as "less than"
5. Add the value as 60
6. In Step 3, Select the Queue as Cold Leads
7. Click Save
