INTRODUCTION
============

This App provide SAML authentication support based on the simpleSAMLphp SP software.


INSTALLATION
============

PREVIOUS DEPENDENCE
-------------------

This App require a simpleSAMLphp SP installed, configured and connected to an IdP.
To learn how to do this check this documentation:

* `SimpleSAMLphp installation <http://simplesamlphp.org/docs/stable/simplesamlphp-install>`_
* `SimpleSAMLphp configuration as an SP <http://simplesamlphp.org/docs/stable/simplesamlphp-sp>`_


STEPS
-----

1. Copy the 'user_saml' folder inside the ownCloud's apps folder and give to apache server privileges on whole the folder.
2. Access to ownCloud web with an user with admin privileges.
3. Access to the Appications pannel and enable the SAML app.
4. Access to the Administration pannel and configure the SAML app.
5. Take care of session issue. ownCloud 4.5.5 and after version set for ownCloud its own session cookiename and that makes conflicts with simpleSAMLphp. There are 2 solutions for this problem:
 
* Set the same cookiename to simpleSAMLphp and ownCloud. Check the value of the 'instanceid' at config/config.php in ownCloud, and set the same value to the 'session.phpsession.cookiename' var of the config/config.php of simpleSAMLphp

* Use different session handler for ownCloud and simpleSAMLphp, Use memcache or SQL backend in simpleSAMLphp (http://simplesamlphp.org/docs/stable/simplesamlphp-maintenance#section_2)

EXTRA INFO
==========

* If you enable the "Autocreate user after saml login" option, then if an user does not exist, will be created. If this option is disabled and the user does not existed then the user will be not allowed to log in ownCloud.

* If you enable the "Update user data" option, when an existed user enter, then his email and groups will be updated.

  By default the SAML App will unlink all the groups from a user and will provide the group defined at the groupMapping attribute. If the groupMapping is not defined
  the value of the defaultGroup field will be used instead. If both are undefined, then the user will be set with no groups.
  But if you configure the "protected groups" field, those groups will not be unlinked from the user.


NOTES
=====

If you had an older version of this plugin installed and the SAML link no appears at the main view, edit the index.php and set the $RUNTIME_NOAPPS to FALSE; 
