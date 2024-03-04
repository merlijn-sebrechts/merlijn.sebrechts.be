---
title: "Ghent University address book in Thunderbird"
layout: post
type: "post"
date: 2022-08-31
categories:
  - 'University'
tags:
  - 'Thunderbird'
  - 'Exchange ActiveSync'
  - 'Outlook'
featured: "/2022/address-book-example.png"
---

## UGent address book support in Mozilla Thunderbird

Ghent University has an LDAP address book which contains all students and staff. Adding this address book to Thunderbird is non-trivial, though. Follow these steps to add it.

1. Install the extensions "TbSync" and "Provider for Exchange ActiveSync". (Press `alt` to show the menu and choose `Edit` > `Preferences` > `Add-ons and Themes`)
1. Open TBSync settings, click `Account actions` > `Add New Account` > `Exchange ActiveSync`.

   ![open-tbsync-settings-account](/img/2022/open-tbsync-settings-account.png)
1. Choose the option `Microsoft Office 365`.

   ![add-activesync-account](/img/2022/add-activesync-account.png)
1. A screen pops up to login into your UGent account. Fill this in. This supports two-factor authentication using OAuth SSO.
1. Click on `Enable and synchronize this account`, enable the `Contacts` resource, and click `Synchronize now`.

   ![enable-activesync-account](/img/2022/enable-activesync-account.png)

That's it! Now when you compose a new email, Thunderbird will auto-suggest email addresses from the UGent address book.

## Manually searching the address book

You can also search the address book directly.

1. Start by clicking on the "go to address book" button.

   ![go-to-address-book](/img/2022/go-to-address-book.png)

1. Because the UGent address book is so large, Thunderbird doesn't show anything until you start searching. Select the address book and type a name in the search bar to see the contacts.

   ![search-address-book](/img/2022/search-address-book.png)
