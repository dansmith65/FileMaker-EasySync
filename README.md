## Status

The [master](https://github.com/dansmith65/FileMaker-EasySync/tree/master) branch is just an archive of the last official release by it's original author. The [dev](https://github.com/dansmith65/FileMaker-EasySync/tree/dev) branch of this project is a work-in-progress that is not ready for release. I currently have no plans to continue development on this project. Although, it is possible that I'll decide I want to use this code for myself, and pick it up again. If somone wanted to sponsor development on this project, I'd be open to that as well. Here are a couple of the main features I was in the process of adding for my first release:

1. [modularfilemaker.org](http://modularfilemaker.org) format, which means easier configuration.
2. Test driven development, which means stable/tested code.
3. Improved handling of large payloads, which means faster syncing in some scenarios.

## EasySync / EasyDeploy Databases

There are three demo databases included:

- FM_Surveys_Hosted: The hosted database.
- FM_Surveys_Mobile: The mobile database.
- EasyDeploy: The EasyDeploy “helper” database that facilitates the downloading and installation of upgrades.



## EasySync FileMaker Accounts

There are four accounts setup in both the hosted and mobile “EasySync” databases:

Account Name: Admin  
Password: [blank]  
Privilege Set: Full Access

Account Name: User1  
Password: fmezuser1  
Privilege Set: Data Entry Only

Account Name: User2  
Password: fmezuser2  
Privilege Set: Data Entry Only

Account Name: ezdeploy  
Password: makeitso  
Privilege Set: EasyDeploy (Extremely limited access. Can only run the “Return Requested Deployment Segment” script.)  
Note: Used for EasyDeploy integration.



## EasyDeploy FileMaker Accounts

There are two accounts setup in the EasyDeploy databases:

Account Name: ezdeploy  
Password: makeitso  
Privilege Set: Data Entry Only  
Note: The file is set to open automatically with this account.

Account Name: Admin  
Password: [blank]  
Privilege Set: Full Access  
Note: Hold down the option (or alt) key when opening the file to bypass the default account.



## Contributing

Contributions to this project are encouraged. If you've used FMEasySync and made improvements to it see [CONTRIBUTING.md](CONTRIBUTING.md) for information on how you can contribute.
