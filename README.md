# nl.sp.drupal-spwebform

With the spwebform module installed on the form website and the spcivitokens module installed on the CiviCRM website, it is possible to modify an existing form to a spwebform. This modification adds some hidden contact data fields to the webform that get automaticly filled with user data when contacts visits the webform using a special link in an e-mail send from CiviCRM.

To modify an existing form on the form website to such a spwebform, go to /admin/config/sp/spwebform. You have to enter a redirect path for the form. This is the path where the user that clicks the link in the e-mail will be redirected to find the form.

In CiviCRM the link in the e-mail should be exactly like this, where [webform node id] should be replaced with the node id of the webform:

https://doemee.sp.nl/spwebform/[webform node id]/{sptokens.spwebformsecret}

The {sptokens.spwebformsecret} is a CiviCRM token that CiviCRM will replace with a string that contains encrypted contact data when sending the e-mail. The contact will receive an e-mail containing a link looking like this:

https://doemee.sp.nl/spwebform/2/TjgwaW1hTVdvUExic3cyVHd3clBoK3hUeEs1RU05bmhKU1NFRlB1NW9OWmZUNnUzMHpKOEVyMFRWV0F

For CiviCRM to be able to encrypt the user data for the link, and the webform site to be able to decrypt the user data, both sites need the same secret code used for encryption. This code needs to be set in the configuration of the respective modules.

Configuration of the secret for the spwebform module on the form website: /admin/config/sp/spwebform/settings

Configuration of the secret for the spcivitokens module on the CiviCRM website: /admin/config/sp/spcivitokens
