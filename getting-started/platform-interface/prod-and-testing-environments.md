# Prod and Testing environments

The Commanders Act platform allows you to manage data sources, destinations, transformations across different environments. These environments—namely Production, Staging, and Development—help you organize and control your data flow more efficiently.

### What Are Environments?

Environments are labels can be applied to sources, destinations, and transformations. These labels help you categorize and manage how data flows and is processed within the system. By selecting an environment, you can specify the context in which a particular source, destination, or transformation should operate.\
The default three primary environments are:

* **Production**: This is the live environment (on which to be very carreful)
* **Staging**: Often used for testing and quality assurance.
* **Development**: Used to build and test things

### Workflow Examples

#### Use Case 1: Team-wide Testing of a New Destination

* **Scenario**: Your team needs to validate a new destination configuration.
* **Steps**:
  1. Create a destination in the Development environment and label it "Team\_Test\_Destination."
  2. Connect only Development sources that are sending known, controlled events.
* **Outcome**: The team can collectively test and validate the new destination using controlled, lower-volume data.

#### Use Case 2: Testing Data Transformations on a Smaller Scale

* **Scenario**: You've developed a new data transformation logic and want to test its impact before applying it to your live data.
* **Steps**:
  1. Create a source in the Development environment and label it "Transformation\_Test."
  2. Direct only a subset of your events, preferably test events, to this source.
  3. Create a transformation in the Development environment and connect it to the "Transformation\_Test" source.
* **Outcome**: You can validate the new data transformation logic using controlled, lower-volume data without affecting the Production environment.

#### Use Case 3: Verifying a Mobile App Update

* **Scenario**: You're releasing a new version of your mobile app and want to ensure it works as expected.
* **Steps**:
  1. Create a source in the Development environment specifically for the new mobile app version.
  2. Initially, connect this source to destinations in the Development environment.
  3. Once verified, connect it to Production destinations.
* **Outcome**: You can test the new app version in a controlled, lower-volume setting before rolling it out to your user base.

#### Use Case 4: Role-based Access Control (soon)

* **Scenario**: You want to control who can make changes in different environments.
* **Steps**:
  1. Assign roles to team members, specifying permissions for Production, Staging, and Development.
  2. Implement these roles to restrict or grant access to specific sources, destinations, or transformations.
* **Outcome**: Only authorized team members can make changes in sensitive environments, enhancing security and accountability.

{% hint style="info" %}
In the near future, the platform will introduce user permission management that will allow you to define who can modify or create elements in each environment. This adds an extra layer of control and security, ensuring that only authorized personnel can make changes to critical environments like Production.
{% endhint %}

### Advantages of Using Environments

#### Data Isolation

Isolating data between environments minimizes the risk of errors and data corruption. For example, testing a new feature in the Development or Staging environment will not affect your live data in Production.

#### Enhanced Security

Production data is isolated from Development and Staging, reducing the risk of unauthorized access or data leakage.

#### Improved Testability

New features or data transformations can be thoroughly tested in the Staging or Development environment before being rolled out to Production.

#### Streamlined Deployment

Moving new features from Development to Staging and finally to Production becomes more straightforward, reducing the chances of errors during deployment.

#### Team Collaboration

Environments facilitate better collaboration between development, testing, and operations teams by providing dedicated spaces for each phase.

#### Future Feature: User Permission Management

It allows you to define who can modify or create elements on production, staging, etc. This adds an extra layer of control and security, ensuring that only authorized personnel can make changes to critical environments like Production.

### How to Use Environments

1. **Creating a Source or Destination**: You have the option to label it with an environment tag—either Production, Staging, or Development. This helps you categorize and manage how data flows and is processed within the system.
2. **Data Cleansing Transformations**: While creating a transformation, you can choose to apply it to a specific environment, giving you more control over your data flow.
