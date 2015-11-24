# [ng-jedi-security](https://github.com/jediproject/ng-jedi-security)
An [AngularJs](https://angularjs.org/) component for Authentication and Authorization with token strategy.

  1. [Install](#install)
  1. [How To Use](#how-to-use)
  
  ### Install

* Install the dependency:

   ```shell
bower install ng-jedi-security --save
   ```
   
* Include module dependency:

   ```javascript
angular.module('yourApp', ['jedi.security']);
   ```
======

### How To Use

1. [Methods](#methods)
	1. [Initialize](#initialize)
	1. [SignUp](#signup)
	1. [SignIn](#signin)
	1. [SignOut](#signout)
	1. [RefreshToken](#refreshtoken)
	1. [GetToken](#gettoken)
	1. [HasRoles](#hasroles)
	1. [IsAuthenticated](#isauthenticated)
1. [Interceptors](#interceptors)
1. [Filters](#filters)
	1. [HasRoles](#hasroles)
	1. [IsAuthenticated](#isauthenticated)
1. [Directives](#directives)
	1. [jdRolesToShow](#jdrolestoshow)
	1. [jdRolesToActive](#jdrolestoactive)
	1. [jdActive](#jdactive)


#### Methods
All the functionalities that this module has to offer.

##### Initialize
Responsible to initialize the component itself broadcasting a few events that you can listen to:
- jedi.security:validation-success
	- When the user is successfully authenticated.
- jedi.security:validation-error
	- When there is an error authenticating the user credentials.
- jedi.security:invalid
	- When the user is not currently logged in.
 
##### SignUp
Triggers an API request to register an user returning a promise.
##### SignIn
Triggers an API request to login the user. Returns a promise and broadcast two events:
- jedi.security:login-success
	- When the user has successfully authenticaded.
- jedi.security:login-error
	- When there is an error authenticating the user credentials.
	
##### SignOut
Triggers an API request to logout and delete the current user token broadcasting two events:
- jedi.security:logout-success
	- When the user is successfully logged out.
- jedi.security:logout-error
	- When there was an error logging out the user.
	 
##### RefreshToken
Triggers an API request to revalidate the user's token giving it more time to use your app. Also it broadcasts two events:
- jedi.security:refresh-success
	- When the token has successfully been refreshed.
- jedi.security:refresh-error
	- When there was a problem revalidating the token.

##### GetToken
Retrieves the token from the current user.

##### HasRoles
Returns true if the user has roles and false otherwise.

##### IsAuthenticated
Returns true if the user is authenticated and false otherwise.

#### Interceptor
Injects the authentication data in the header of every request that you make so you don't need to worry about it.

Also it has a responseError treatment that broadcasts an event in case your session has expired:
- jedi.security:session-expired

Otherwise it will refresh you token.

#### Filters
A couple of filters to help you use all the things that this module has to offer.
##### HasRoles
In case the user don't have the roles specified returns an empty array (false).
##### IsAuthenticated
In case the user is not authenticated returns an empty array (false).

#### Directives
A few directives to help you use all the things that this module has to offer.
##### jdRolesToShow
Show or hide a DOM element according to the user's roles.

##### jdRolesToActive
Enable or disable(readonly) a DOM element according to the user's roles.

##### jdActive
Enable or disable(readonly) a DOM element. Can receive true/false, a variable from the controller or a function to determine its value.

