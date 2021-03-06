This is a staging area for tools and information related to the
[https://wiki.openstack.org/wiki/TripleO/TripleOCloud production quality cloud]
the TripleO program is running in a continuous delivery fashion.

Currently found here:

* tripleo-cd-admins: A list (ircname,email,human name,comment) of people
  permitted root access to the tripleo cloud. This is used for recording
  details and for automatically creating admin (and regular user) accounts.

* tripleo-cd-users: A list of users of the TripleO CD overcloud - either
  TripleO ATC's or other folk which the TripleO PTL has granted access to the
  cloud. This is used to populate users on the cloud automatically, and new
  ATC's should ask for access by submitting a review to add their details.
  The comment field should list why non-ATC's have access.

* tripleo-cd-ssh-keys: The ssh keys for people in tripleo-cd-admins.

Policy on adding / removing people:
 - get consensus/supermajority for adds from existing triple-cd-admins members.
 - remove folk at own request or if idle for extended period.

Implementation of adding / removing people:
 - Ssh into the seed VM host and add / remove a user for them.
 - Ssh into the seed VM and update the root authorized-keys likewise.
 - Update the 'default' keyring on the CD seed 'admin' user to the current
   keyring here.
 - Ssh into cd-undercloud.tripleo.org and update the heat-admin authorized-keys
   file.
 - Update the 'default' keyring on the CD undercloud 'admin' user to the
   current keyring here.
 - Add them to https://docs.google.com/spreadsheet/ccc?key=0AlLkXwa7a4bpdERqN0p5RjNMQUJJeDdhZ05fRVUxUnc&usp=sharing
 - In future, we need to create per-user accounts too.
