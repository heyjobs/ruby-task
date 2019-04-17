### Introduction
First of all, thank you for taking the time to complete this test task!
The purpose of the task is to get an idea of your development style: the way you structure code, automated tests you add etc.

### Task background

We publish our jobs to different marketing sources. To keep track of where the particular job is published, we create
`Campaign` entity in database. `Campaigns` are periodically synchronized with 3rd party _Ad Service_.

`Campaign` properties:

- `id`
- `job_id`
- `status`: one of [active, paused, deleted]
- `external_reference`: corresponds to Ad’s ‘reference’
- `ad_description`: text description of an Ad

Due to various types of failures (_Ad Service_ inavailability, errors in campaign details etc.)
local `Campaigns` can fall out of sync with _Ad Service_.
So we need a way to detect discrepancies between local and remote state.

### TODOs
1. Develop a [Service](https://medium.com/selleo/essential-rubyonrails-patterns-part-1-service-objects-1af9f9573ca1)(as in _Service Object_ pattern),
which would get campaigns from external JSON API([example link](https://mockbin.org/bin/fcb30500-7b98-476f-810d-463a0b8fc3df)) and detect discrepancies between local and remote state.
2. The purpose of the task is to work on business logic, so please don't create a Rails app. Rather stucture your project the following way:
```
|-- .ruby-version
|-- .ruby-gemset
|-- Gemfile
|-- lib
    |-- source files go here
|-- spec
    |-- specs go here
```
You're free to add gems you need(including those which are part of Rails).

3. You don't have to put all your code into one class. Please use your best judgment to split the code up into separate components.
4. **Note** Don't fork this repository. Create you own public repository and send us a link to it. You may describe some of the assumptions you had in the README file of your repository.

### Service output format
You're free to choose the output format which makes sense to you, we suggest the following:
```
[
  {
    "remote_reference": "1",
    "discrepancies": [
      "status": {
        "remote": "disabled",
        "local": "active"
      },
      "description": {
        "remote": "Rails Engineer",
        "local": "Ruby on Rails Developer"
      }
    ]
  }
]
```

**Have fun!**
