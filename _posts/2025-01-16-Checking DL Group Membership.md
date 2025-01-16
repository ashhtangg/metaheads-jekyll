Certainly! Here's a brief blog post with a more generalized version of the script:

## Checking Distribution List Membership in Exchange Online: A PowerShell Solution

As an IT administrator, you might often need to verify if certain users are members of a specific distribution list in Exchange Online. Here's a simple PowerShell script that can help you automate this process.

```powershell
# Connect to Exchange Online
Connect-ExchangeOnline

# Get members of the distribution group
$dlUsers = Get-DistributionGroupMember -Identity "Your Distribution Group Name" | Select-Object -ExpandProperty PrimarySmtpAddress

# Read list of users to check
$users = Get-Content -Path "Path\To\Your\UserList.csv"

# Check each user against the distribution group
foreach ($user in $users) {
    if ($dlUsers -notcontains $user) {
        Write-Host "$user is not in the Distribution Group"
    }
}
```

This script does the following:

1. Connects to Exchange Online.
2. Retrieves members of the specified distribution group.
3. Reads a list of users from a CSV file.
4. Checks each user against the distribution group membership and reports any users not in the group.

To use this script, replace "Your Distribution Group Name" with the actual name of your distribution group, and "Path\To\Your\UserList.csv" with the path to your CSV file containing the list of users to check.

Remember to run this script in an elevated PowerShell session and ensure you have the necessary permissions to access the distribution group in Exchange Online.

This simple yet effective script can save you time and reduce errors when managing large distribution lists in your organization.