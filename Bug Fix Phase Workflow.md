# Workflow for Resolving Issue
## Supplementary Tools
- Trello  
- Mantis 
- Bitbucket

## Considerations
- Build app for testing.
- Wait for the test result to be uploaded in trello.
- While waiting, the monitoring person will frequently check mantis for the reported issues and then assign a person to deal with it.
- The assigned developer may not or may fix the issue right away.
- Fixing the issue, the developer should create an issue in bitbucket.
- The developer should create a new branch from the development branch to fix the issue.
- The developer should create a pull request.
- Once the pull request is merged, the monitoring person marked the bitbucket issue as 'resolved'.
- All bitbucket issues must be marked as 'resolved' before changing the status of all the mantis issues to 'resolve'.
- If the status of the issue in mantis is changed to 'close', the monitoring person should change the bitbucket issue to 'closed' respectively.
- If the tester approaches because he/she can not perform the other test cases due to application crash issues, the assigned developer must prioritize to fix that issue (development hot fixes).
- Once the test result file is uploaded, that is the time the developers must fix the issues assigned to them.
- If all the mantis issues are changed to 'resolve', build the app for testing again.
- Once the pull request of the developer is merged into the development branch, he/she can now click the resolve button of the bitbucket issue.

## Collaborating Mantis and Bitbucket

### Creating Bitbucket Issues

- Setting the title of the issue

```
FORMAT:
Resolve <Re-phrased-title-that-is-set-in-Mantis>

EXAMPLE:
Mantis: should follow a priority of validation
Bitbucket: Resolve on the priority validation in registration
```

- Setting the description of the issue

```
FORMAT:
<Mantis-Issue-Description>

Mantis [<Mantis-Issue-ID>](<link-that-redirects-to-mantis>)

EXAMPLE:
Should follow a priority of validation
1. username
2. password
3. confirm password
4. mobile
5. email

Mantis [3584](http://example.org:83/view.php?id=3643).
```

- If the title and description is the same, just set the issue's description to

```
Mantis [<Mantis-Issue-ID>](<link-that-redirects-to-mantis>)
```

- Title and description must start with an uppercase letter
- Default title of the issue is the `<Mantis-Issue-Title>`
- The montioring person has an option to rename and edit the title and give more details in the description appropriately
- If the issue reporter is confused on what title he/she should set, just choose the default title