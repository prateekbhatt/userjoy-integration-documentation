# Reference of the JavaScript API

## Overview

#### Modules
UserJoy allows you to categorize your app into modules, i.e. for a task management app, these could be 'Team' module, 'Task' module.

#### Events
Every module should have a set of events, i.e. for the 'Team' module, events could be  'Created New Team', 'Added Team Member' etc.

#### Properties
You can pass an optional properties object alongwith the event, i.e. for the 'Team' module, this could be, { total_members: 11 } etc.


## Javascript API


### Identify

```js
userjoy.identify(properties, callback)
```

Identify the logged in user

##### Params

name       | required  | type      | description
-----      | ------    | -----     | ------
properties | yes       | Object    | Attributes of the user such as email, name, user_id etc.
callback   | no        | Function  | Optional function to be called after the `userjoy.identify` call

##### Special Properties

name       | required  | type      | description
-----      | ------    | ------    | ----------
email      | yes       | String    | email address of the logged in user
unique_id  | no        | String    | unique user id, should be database id
status     | yes       | String    | trial / free / paying / cancelled
plan       | no        | String    | name of the plan


### Company

```js
userjoy.company(properties, callback)
```

Identify the company/team/organization that the logged in user belongs to

##### Params

name       | required  | type      | description
-----      | ------    | -----     | ------
properties | yes       | Object    | Attributes of the company such as name, members etc.
callback   | no        | Function  | Optional function to be called after the `userjoy.company` call

##### Special Properties

name       | required  | type      | description
-----      | ------    | ------    | -----
unique_id  | yes       | String    | unique company id, should be database id
name       | no        | String    | name of the company
status     | yes       | String    | trial / free / paying / cancelled
plan       | yes       | String    | name of the plan


### Page

```js
userjoy.page(module, name, properties, callback)
```

Track a pageview.

##### Params

name       | required  | type      | description
-----      | ------    | -----     | ------
module     | no        | String    | Name of the product module, i.e. 'Team', 'Tasks', 'Billing' etc.
name       | yes       | String    | Name of the event, i.e. 'Added New Member', 'Created New Task', 'Upgraded Plan' etc
properties | no        | Object    | Additional properties for the event, i.e. { total_members: 11 } etc
callback   | no        | Function  | Optional function to be called after the `userjoy.track` call


##### Reserved Properties (Do Not Send)

name       | description
-----      | ------
name       | already being sent as the first / second param
module     | already being sent as the first param



### Track

```js
userjoy.track(module, name, properties, callback)
```

Track an event performed by the user.

##### Params

name       | required  | type      | description
-----      | ------    | -----     | ------
module     | no        | String    | Name of the product module, i.e. 'Team', 'Tasks', 'Billing' etc.
name       | yes       | String    | Name of the event, i.e. 'Added New Member', 'Created New Task', 'Upgraded Plan' etc
properties | no        | Object    | Additional properties for the event, i.e. { total_members: 11 } etc
callback   | no        | Function  | Optional function to be called after the `userjoy.track` call


### Track_Link

```js
userjoy.track_link(links, name, callback)
```

`track_link` is a helper method to help you track url clicks.

##### Params

name       | required  | type       | description
-----      | ------    | -----      | ------
links      | yes       | DOM Element| DOM Element representing the link(s), i.e. `document.getElementById('new_link')`
name       | yes       | String     | Name of the event, i.e. 'Clicked Billing Link' etc
callback   | no        | Function   | Optional function to be called after the `userjoy.track_link` call


### Track_Form

```js
userjoy.track_form(forms, callback)
```

`track_form` is a helper method to help you track form submissions.

##### Params

name       | required  | type       | description
-----      | ------    | -----      | ------
forms      | yes       | DOM Element| DOM Element representing the link(s), i.e. `document.getElementById('new_form')`
name       | yes       | String     | Name of the event, i.e. 'Submitted Billing Form' etc
callback   | no        | Function   | Optional function to be called after the `userjoy.track_link
