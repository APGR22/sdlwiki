# CategoryQuit

An [SDL_QUIT](SDL_QUIT) event is generated when the user tries to close the
application window. If it is ignored or filtered out, the window will
remain open. If it is not ignored or filtered, it is queued normally and
the window is allowed to close. When the window is closed, screen updates
will complete, but have no effect.

[SDL_Init](SDL_Init)() installs signal handlers for SIGINT (keyboard
interrupt) and SIGTERM (system termination request), if handlers do not
already exist, that generate [SDL_QUIT](SDL_QUIT) events as well. There is
no way to determine the cause of an [SDL_QUIT](SDL_QUIT) event, but setting
a signal handler in your application will override the default generation
of quit events for that signal.

<!-- END CATEGORY DOCUMENTATION -->

## Functions

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryQuit, CategoryAPIFunction -->
<!-- END CATEGORY LIST -->

## Datatypes

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryQuit, CategoryAPIDatatype -->
<!-- END CATEGORY LIST -->

## Structs

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryQuit, CategoryAPIStruct -->
<!-- END CATEGORY LIST -->

## Enums

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryQuit, CategoryAPIEnum -->
<!-- END CATEGORY LIST -->

## Macros

<!-- DO NOT HAND-EDIT CATEGORY LISTS, THEY ARE AUTOGENERATED AND WILL BE OVERWRITTEN, BASED ON TAGS IN INDIVIDUAL PAGE FOOTERS. EDIT THOSE INSTEAD. -->
<!-- BEGIN CATEGORY LIST: CategoryQuit, CategoryAPIMacro -->
<!-- END CATEGORY LIST -->

----
[CategoryAPICategory](CategoryAPICategory)

