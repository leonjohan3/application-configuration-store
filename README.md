# Overview
Contains the externalized configurations for the Spring Boot microservices of the organization/team.
When these configurations change, they are deployed to AWS AppConfig (using CI/CD). Re-started microservices then pick up the new configuration.

Changes to configuration is managed using code review practices, and can be rolled back using version-controlling. Visibility to change means the ability to trace and reproduce issues quickly.

This implementation is more suited to configuration that remains mostly static while the application is running - so this is not suited to the use of feature flags. AWS AppConfig has built-in support for feature flags.
The "free form" configuration profile of AWS AppConfig is used here, and this supports not only YAML, but other formats, like Java properties.

# Directory structure
- The root folder contains the names of the applications or microservices. Name restrictions: start with a letter, have numbers, dashes and underscores, up to 60 characters
- The sub folders inside the application folders represent the environments the applications or microservices run in, e.g. prod, dev, test, etc.
- The environment sub-folders contain the files that hold the configuration used by the applications or microservices, e.g. application.yaml or application.properties

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

# Resources
- [AWS AppConfig](<https://docs.aws.amazon.com/appconfig/latest/userguide/what-is-appconfig.html>)
- [AWS AppConfig configuration store quotas and limitations](<https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-free-form-configurations-creating.html#appconfig-creating-configuration-and-profile-quotas>)
- [AWS AppConfig support for feature flags](<https://docs.aws.amazon.com/appconfig/latest/userguide/appconfig-creating-configuration-and-profile-feature-flags.html>)
