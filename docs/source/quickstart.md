# Quickstart

## Dependencies

An API key is required for this module to function.

Go to https://www.mailboxvalidator.com/plans#api to sign up for FREE API plan and you'll be given an API key.

## Installation

To install this module type the following:

```bash
perl Makefile.PL
make
make test
make install
```

## Sample Codes

### Validate email

You can validate whether an email address is invalid or not as below:

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
	print 'base_email_address = ' . $results->{base_email_address} . "\n";
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
	print 'is_dmarc_enforced = ' . $results->{is_dmarc_enforced} . "\n";
	print 'is_strict_spf = ' . $results->{is_strict_spf} . "\n";
	print 'website_exist = ' . $results->{website_exist} . "\n";
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

### Check if an email is from a disposable email provider

You can validate whether an email address is disposable email address or not as below:

```perl
use MailboxValidator::SingleValidation;

my $mbv = MailboxValidator::SingleValidation->Init('PASTE_YOUR_API_KEY_HERE');

my $results = $mbv->DisposableEmail('example@example.com');

if (!defined($results))
{
	print "Error connecting to API.\n";
}
elsif ($results->{error_code} eq '')
{
	print 'email_address = ' . $results->{email_address} . "\n";
	print 'is_disposable = ' . $results->{is_disposable} . "\n";
	print 'credits_available = ' . $results->{credits_available} . "\n";
}
else
{
	print 'error_code = ' . $results->{error_code} . "\n";
	print 'error_message = ' . $results->{error_message} . "\n";
}
```

### Check if an email is from a free email provider

You can validate whether an email address is free email address or not as below:

```perl
use MailboxValidator::SingleValidation;

my $mbv = MailboxValidator::SingleValidation->Init('PASTE_YOUR_API_KEY_HERE');

my $results = $mbv->FreeEmail('example@example.com');

if (!defined($results))
{
	print "Error connecting to API.\n";
}
elsif ($results->{error_code} eq '')
{
	print 'email_address = ' . $results->{email_address} . "\n";
	print 'is_free = ' . $results->{is_free} . "\n";
	print 'credits_available = ' . $results->{credits_available} . "\n";
}
else
{
	print 'error_code = ' . $results->{error_code} . "\n";
	print 'error_message = ' . $results->{error_message} . "\n";
}
```
