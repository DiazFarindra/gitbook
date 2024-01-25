# Naming Conventions

Naming something is one of the most difficult things in the programming world. therefore here we provide guidelines for naming something.

<figure><img src="https://media.giphy.com/media/zOvBKUUEERdNm/giphy.gif" alt=""><figcaption></figcaption></figure>

## Adding Matrics to Name

Consider adding the unit to the name whenever you work with something measurable.

```php
// ❌ bad: we don't know what that 100 represents
$averageTime = 100;

// ✅ good: we now know that it is 100ms
$averageTimeInMs = 100;
```

## Controllers

for naming restful or resourceful controllers (`index, create, update, delete`), with Laravel standards, we usually do it with the Model name at the beginning and at the end of the Controller. this is to improve the consistency of a code, easy to read, easy to develop, and easy to maintain.

For example, if there is a `User` model, the controller is `UserController`.

when writing a controller that is not restful or non-resourceful, we might use `__invoke` it to perform a single action. these can be named according to the action they perform and then end with the Controller.

e.g. `PerformCleanupController`.

## Jobs

Job name should describe the action.

e.g. `PerformDatabaseCleanup` or `CreateUser`

## Events

The event will often be executed before or after the event it should have been. This must be very clear with the tense used in the name.

for example `ApprovingLoan` before the action finishes, and `LoanApproved` after the action finishes.

## Listeners

The Listener will perform an action based on the incoming Event, the name must reflect an action ending with the Listener. this will be weird at first, but it's meant to avoid a collision with the Jobs naming.

e.g. `SendInvitationMailListener`.

## Laravel Standard Naming

| What                             | How                                                                            | Good                                          | Bad                                              |
| -------------------------------- | ------------------------------------------------------------------------------ | --------------------------------------------- | ------------------------------------------------ |
| Controller                       | singular                                                                       | ArticleController                             | ArticlesController                               |
| Route                            | plural                                                                         | articles/1                                    | article/1                                        |
| Named route                      | snake\_case with dot notation                                                  | users.show\_active                            | users.show-active, show-active-users             |
| Model                            | singular                                                                       | User                                          | Users                                            |
| hasOne or belongsTo relationship | singular                                                                       | articleComment                                | articleComments, article\_comment                |
| All other relationships          | plural                                                                         | articleComments                               | articleComment, article\_comments                |
| Table                            | plural                                                                         | article\_comments                             | article\_comment, articleComments                |
| Pivot table                      | singular model names in alphabetical order                                     | article\_user                                 | user\_article, articles\_users                   |
| Table column                     | snake\_case without model name                                                 | meta\_title                                   | MetaTitle; article\_meta\_title                  |
| Foreign key                      | singular model name with \_id suffix                                           | article\_id                                   | ArticleId, id\_article, articles\_id             |
| Primary key                      | -                                                                              | id (sometimes uuid)                           | custom\_id                                       |
| Migration                        | -                                                                              | 2017\_01\_01\_000000\_create\_articles\_table | 2017\_01\_01\_000000\_articles                   |
| Method                           | camelCase                                                                      | getAll                                        | get\_all                                         |
| Function                         | snake\_case                                                                    | abort\_if                                     | abortIf                                          |
| Method in resource controller    | more infos: [table](https://laravel.com/docs/controllers#resource-controllers) | store                                         | saveArticle                                      |
| Method in test class             | camelCase                                                                      | testGuestCannotSeeArticle                     | test\_guest\_cannot\_see\_article                |
| Model property                   | snake\_case                                                                    | $model->model\_property                       | $model->modelProperty                            |
| Variable                         | camelCase                                                                      | $anyOtherVariable                             | $any\_other\_variable                            |
| Collection                       | descriptive, plural                                                            | $activeUsers = User::active()->get()          | $active, $data                                   |
| Object                           | descriptive, singular                                                          | $activeUser = User::active()->first()         | $users, $obj                                     |
| Config and language files index  | snake\_case                                                                    | articles\_enabled                             | ArticlesEnabled; articles-enabled                |
| View                             | kebab-case                                                                     | show-filtered.blade.php                       | showFiltered.blade.php, show\_filtered.blade.php |
| Config                           | kebab-case                                                                     | google-calendar.php                           | googleCalendar.php, google\_calendar.php         |
| Contract (interface)             | adjective or noun                                                              | Authenticatable                               | AuthenticationInterface, IAuthentication         |
| Trait                            | adjective                                                                      | Notifiable                                    | NotificationTrait                                |
