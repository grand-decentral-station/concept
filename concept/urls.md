# URLs

This document is intended as an overview of all URL schemes for services and applications. Those schemes should also be mentioned in other documents, but this list can help to keep structure them. 

## Domain Placeholder

All examples use "yourdomain.tld" as a placeholder.

## Encryption

All requests with GDS should be SSL encrypted. Maybe this should even be a must and the system should help assist to purchase and setup a certificate. 

## General URL Scheme

### Single User per domain

{app}.yourdomain.tld/{path}

### Multiple Users per domain

{app}.{username}.yourdomain.tld/{path}

## Grand Decentral Panel

home.yourdomain.tld

### Possible alternatives

- admin
- config
- panel

## Avatar Server

avatar.yourdomain.tld
avatar.yourdomain.tld/{width}x{height}

## vCard Server

vcard.yourdomain.tld

## Email Server

### Interface

mail.yourdomain.tld

### IMAP

imap.yourdomain.tld

### SMTP

smtp.yourdomain.tld

## Calendar

calendar.yourdomain.tld

## Contacts

contacts.yourdomain.tld

## Files

files.yourdomain.tld

## Assets Server

assets.yourdomain.tld
assets.yourdomain.tld/core/…
assets.yourdomain.tld/{app}/…
