---
title: account
description: This table holds information on all available game accounts.
published: true
date: 2021-08-19T19:27:55.841Z
tags: database, auth, master, account
editor: markdown
dateCreated: 2021-08-19T10:37:27.827Z
---

## Structure

| Field | Type | Attributes | Key | Null | Default | Extra | Comment |
|---|---|---|---|---|---|---|---|
| [id](#id) | int(10) | unsigned | PRI | NO |  | Auto increment | Identifier |
| [username](#username) |  |  | UNI |  |  |  |  |
| [salt](#salt) |  |  |  |  |  |  |  |
| [verifier](#verifier) |  |  |  |  |  |  |  |
| [session_key_auth](#session_key_auth) |  |  |  |  |  |  |  |
| [session_key_bnet](#session_key_bnet) |  |  |  |  |  |  |  |
| [sha_pass_hash](#sha_pass_hash) |  |  |  |  |  |  |  |
| [v](#v) |  |  |  |  |  |  |  |
| [s](#s) |  |  |  |  |  |  |  |
| [token_key](#token_key) |  |  |  |  |  |  |  |
| [email](#email) |  |  |  |  |  |  |  |
| [reg_mail](#reg_mail) |  |  |  |  |  |  |  |
| [joindate](#joindate) |  |  |  |  |  |  |  |
| [last_ip](#last_ip) |  |  |  |  |  |  |  |
| [last_attempt_ip](#last_attempt_ip) |  |  |  |  |  |  |  |
| [failed_logins](#failed_logins) |  |  |  |  |  |  |  |
| [locked](#locked) |  |  |  |  |  |  |  |
| [lock_country](#lock_country) |  |  |  |  |  |  |  |
| [last_login](#last_login) |  |  |  |  |  |  |  |
| [online](#online) |  |  |  |  |  |  |  |
| [expansion](#expansion) |  |  |  |  |  |  |  |
| [mutetime](#mutetime) |  |  |  |  |  |  |  |
| [mutereason](#mutereason) |  |  |  |  |  |  |  |
| [muteby](#muteby) |  |  |  |  |  |  |  |
| [locale](#locale) |  |  |  |  |  |  |  |
| [os](#os) |  |  |  |  |  |  |  |
| [recruiter](#recruiter) |  |  |  |  |  |  |  |
| [battlenet_account](#battlenet_account) |  |  |  |  |  |  |  |
| [battlenet_index](#battlenet_index) |  |  |  |  |  |  |  |
&nbsp;
## Description of fields

### id
The unique account ID.
&nbsp;

### username
The account user name.
&nbsp;

### salt
*- no description -*
&nbsp;

### verifier
*- no description -*
&nbsp;

### session_key_auth
*- no description -*
&nbsp;

### session_key_bnet
*- no description -*
&nbsp;

### sha_pass_hash
This field contains the encrypted password. The encryption is SHA1 and is in the following format: username:password. The SQL to create the password (or to compare with the current hash) is:

<div class="next-codeblock-no-line-numbers"></div>

```bash
SELECT SHA1(CONCAT(UPPER(`username`), ':', UPPER(&lt;pass&gt;)));
```
&nbsp;

### v
*- no description -*
&nbsp;

### s
*- no description -*
&nbsp;

### token_key
The authenticator key.

Key can be generated through the Google Authenticator API, a 3rd-party TOTP generator, or manually specified (must be a Base32-compliant expression that is 16 characters).

Implementation link on Wikipedia for the Google Authenticator API

http://en.wikipedia.org/wiki/Google_Authenticator#Implementations
&nbsp;

### email
The e-mail address associated with this account.
&nbsp;

### reg_mail
The registration e-mail address associated with this account.
&nbsp;

### joindate
The date when the account was created.
&nbsp;

### last_ip
The last IP used by the person who logged in the account.
&nbsp;

### last_attempt_ip
*- no description -*
&nbsp;

### failed_logins
The number of failed logins attempted on the account.
&nbsp;

### locked
Boolean 0 or 1 controlling if the account has been locked or not. This can be controlled with the ".account lock" GM command. If locked (1), the user can only log in with their last_ip. If unlocked (0), a user can log in from any IP, and their last_ip will be updated if it is different. ".Ban account" does not lock it.
&nbsp;

### lock_country
*- no description -*
&nbsp;

### last_login
The date when the account was last logged into.
&nbsp;

### online
Boolean 0 or 1 controlling if the account is currently logged in and online.
&nbsp;

### expansion
Integer 0 - 8 controlling if the client logged in on the account has any expansions. (for example if client is TBC, but expansion is set to 0, it will not be able to enter outlands and etc.)

|Value|Expansion|
|:---:|:---: |
|0|Vanilla|
|1|The Burning Crusade (TBC)|
|2|Wrath of the Lich King (WotLK)|
|3|Cataclysm (Cata)|
|4|Mist of Pandaria (MoP)|
|5|Warlords of Draenor (WoD)|
|6|Legion|
|7|Battle for Azeroth (BfA)|
|8|Shadowlands (SL)|
&nbsp;

### mutetime
The time, in Unix time, when the account will be unmuted. To see when mute will be expired you can use this query:

<div class="next-codeblock-no-line-numbers"></div>

```bash
SELECT FROM_UNIXTIME(`mutetime`);
```
&nbsp;

### mutereason
The reason for the mute.
&nbsp;

### muteby
The character name with the rights to the .mute command that give the mute.
&nbsp;

### locale
The locale used by the client logged into this account. If multiple locale data has been configured and added to the world servers, the world servers will return the proper locale strings to the client. See localization IDs
&nbsp;

### os
Stores information about client's OS. Used by Warden system.

- Win
- Mac
&nbsp;

### recruiter
The account ID of another account. Used for recuit-a-friend system. See [account.id](#id)
&nbsp;

### battlenet_account
*- no description -*
&nbsp;

### battlenet_index
*- no description -*
&nbsp;