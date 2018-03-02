MailboxValidator Perl Module
============================

This Perl module provides an easy way to call the MailboxValidator API which validates if an email address is a valid one.

This module can be used in many types of projects such as:

 - validating a user's email during sign up
 - cleaning your mailing list prior to an email marketing campaign
 - a form of fraud check

Installation
============

To install this module type the following:

```
perl Makefile.PL
make
make test
make install
```

Dependencies
============

An API key is required for this module to function.

Go to https://www.mailboxvalidator.com/plans#api to sign up for a FREE API plan and you'll be given an API key.

Usage
=====

```perl
use MailboxValidator::SingleValidation;

my $mbv = MailboxValidator::SingleValidation->Init('PASTE_YOUR_API_KEY_HERE');

my $results = $mbv->ValidateEmail('example@example.com');

if (!defined($results))
{
	print "Error connecting to API.\n";
}
elsif ($results->{error_code} eq '')
{
	print 'email_address = ' . $results->{email_address} . "\n";
	print 'domain = ' . $results->{domain} . "\n";
	print 'is_free = ' . $results->{is_free} . "\n";
	print 'is_syntax = ' . $results->{is_syntax} . "\n";
	print 'is_domain = ' . $results->{is_domain} . "\n";
	print 'is_smtp = ' . $results->{is_smtp} . "\n";
	print 'is_verified = ' . $results->{is_verified} . "\n";
	print 'is_server_down = ' . $results->{is_server_down} . "\n";
	print 'is_greylisted = ' . $results->{is_greylisted} . "\n";
	print 'is_disposable = ' . $results->{is_disposable} . "\n";
	print 'is_suppressed = ' . $results->{is_suppressed} . "\n";
	print 'is_role = ' . $results->{is_role} . "\n";
	print 'is_high_risk = ' . $results->{is_high_risk} . "\n";
	print 'is_catchall = ' . $results->{is_catchall} . "\n";
	print 'mailboxvalidator_score = ' . $results->{mailboxvalidator_score} . "\n";
	print 'time_taken = ' . $results->{time_taken} . "\n";
	print 'status = ' . $results->{status} . "\n";
	print 'credits_available = ' . $results->{credits_available} . "\n";
}
else
{
	print 'error_code = ' . $results->{error_code} . "\n";
	print 'error_message = ' . $results->{error_message} . "\n";
}
```

Functions
=========

### Init(api_key)

Creates a new instance of the MailboxValidator object with the API key.

### ValidateEmail(email_address)

Performs email validation on the supplied email address.

Result Fields
=============

### email_address

The input email address.

### domain

The domain of the email address.

### is_free

Whether the email address is from a free email provider like Gmail or Hotmail.

Return values: True, False

### is_syntax

Whether the email address is syntactically correct.

Return values: True, False

### is_domain

Whether the email address has a valid MX record in its DNS entries.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_smtp

Whether the mail servers specified in the MX records are responding to connections.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_verified

Whether the mail server confirms that the email address actually exist.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_server_down

Whether the mail server is currently down or unresponsive.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_greylisted

Whether the mail server employs greylisting where an email has to be sent a second time at a later time.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_disposable

Whether the email address is a temporary one from a disposable email provider.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_suppressed

Whether the email address is in our blacklist.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_role

Whether the email address is a role-based email address like admin@example.net or webmaster@example.net.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_high_risk

Whether the email address contains high risk keywords.

Return values: True, False, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### is_catchall

Whether the email address is a catch-all address.

Return values: True, False, Unknown, -&nbsp;&nbsp;&nbsp;(- means not applicable)

### mailboxvalidator_score

Email address reputation score.

Score > 0.70 means good; score > 0.40 means fair; score <= 0.40 means poor.

### time_taken

The time taken to get the results in seconds.

### status

Whether our system think the email address is valid based on all the previous fields.

Return values: True, False

### credits_available

The number of credits left to perform validations.

### error_code

The error code if there is any error. See error table below.

### error_message

The error message if there is any error. See error table below.

Errors
======

| error_code | error_message |
| ---------- | ------------- |
| 100 | Missing parameter. |
| 101 | API key not found. |
| 102 | API key disabled. |
| 103 | API key expired. |
| 104 | Insufficient credits. |
| 105 | Unknown error. |

Copyright
=========

Copyright (C) 2018 by MailboxValidator.com, support@mailboxvalidator.com
