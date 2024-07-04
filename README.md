# Overview
This GutHub repo contains an example of the externalized configurations for the Spring Boot microservices/applications of the organization/team.
When these configurations change, they are automatically deployed to AWS AppConfig (using CI/CD or GitOps). Re-started microservices/applications then pick up the new configuration.

Changes to configuration is managed using normal code review practices, and can be rolled back using version-controlling. Visibility to changes mean the ability to trace and reproduce issues (caused by configuration changes) quickly.

This implementation is more suited to configuration that remains mostly static while the application is running - so this is not suited to the use of feature flags. AWS AppConfig has built-in support for feature flags (using an agent).
The "free form" configuration profile of AWS AppConfig is used here, and this supports not only YAML, but other formats, like Java properties.

# Also visit the other related GitHub repos
- [acs-codepipeline](<https://github.com/leonjohan3/acs-codepipeline/blob/main/README.md>)
- [application-configuration-store-cicd](<https://github.com/leonjohan3/application-configuration-store-cicd/blob/main/README.md>)

# Directory structure
- The root folder contains the names of the microservices/applications (names should not include the group prefix, e.g: acs/my-app). Name restrictions: start with a letter, have numbers, dashes and underscores, up to 60 characters
- The sub-folders inside the application folders represent the environments the microservices/applications run in, e.g. prod, dev, test, etc.
- The environment sub-folders contain the files that hold the configuration used by the microservices/applications, e.g. application.yaml or application.properties

# Example
```
├── claims_modulith
│   ├── dev
│   │   └── application.properties
│   └── sit
│       └── application.properties
├── policies-microservice
│   ├── prod
│   │   └── application.yaml
│   └── test
│       └── application.yaml
└── rewards_backend_api
    ├── pre-prod
    │   └── application.yaml
    └── prod
        └── application.yaml
```

# Folder structure rules
- the root folder may contain folders and files (e.g. a README.md file, or .git folder)
- all the 1st level folders (applications) should have one or more sub-folders (environments)
- all the 2nd level folders (environments) should contain only a single configuration file

# Resources
- [AWS AppConfig](<https://docs.aws.amazon.com/appconfig/latest/userguide/what-is-appconfig.html>)
- [AWS AppConfig configuration store quotas and limitations](<https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-free-form-configurations-creating.html#appconfig-creating-configuration-and-profile-quotas>)
- [AWS AppConfig support for feature flags](<https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-creating-configuration-and-profile-feature-flags.html>)
