# Function to add user to Azure subscription (replace with your actual implementation)
function Add-AzureSubscriptionUser {
    param (
        [string]$userName
    )

    # Implement your logic here to add the user to the Azure subscription
    # For example:
    # Connect-AzAccount
    # Add-AzRoleAssignment -SignInName $userName -RoleDefinitionName "Contributor" -Scope "/subscriptions/{subscription-id}"
    # Replace {subscription-id} with the actual subscription ID where you want to add the user
}

# Read names from CSV file and add users to Azure subscription
function Add-UsersFromCSVToAzure {
    param (
        [string]$csvFilePath
    )

    # Import the CSV file and get the list of names
    $names = Import-Csv -Path $csvFilePath | ForEach-Object { $_.Name }

    # Loop through each name and add the user to the Azure subscription
    foreach ($name in $names) {
        Write-Host "Adding user $name to Azure subscription..."
        Add-AzureSubscriptionUser -userName $name
        Write-Host "User $name added to Azure subscription."
    }
}

# Replace 'users.csv' with the actual path to your CSV file containing names
Add-UsersFromCSVToAzure -csvFilePath "users.csv"
