# markdown-test
testing magic of markdown

If the `dev` profile is not active, `AcmeProperties.list` contains one `MyPojo` entry,
as previously defined. If the `dev` profile is enabled, however, the `list` _still_
contains only one entry (with a name of `my another name` and a description of `null`).
This configuration _does not_ add a second `MyPojo` instance to the list, and it does not
merge the items.

When a collection is specified in multiple profiles, the one with the highest priority
(and only that one) is used. Consider the following example:

[source,yaml,indent=0]
----
	acme:
	  list:
		- name: my name
		  description: my description
		- name: another name
		  description: another description
	---
	spring:
	  profiles: dev
	acme:
	  list:
		 - name: my another name
----

In the preceding example, if the `dev` profile is active, `AcmeProperties.list` contains
_one_ `MyPojo` entry (with a name of `my another name` and a description of `null`).
