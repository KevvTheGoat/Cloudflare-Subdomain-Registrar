# Cloudflare Subdomain Registrar

# This Project has Paused it's development and being Archived Due To A New Project Being Developed [here](https://github.com/KevvTheGoat/Cloudflare-Subdomain-Registrar)

A PHP Program For Subdomain Registeration And Management Based On Cloudflare DNS.

[中文 README](https://github.com/KevvTheGoat/SubdomainRegistrarCloudflare/blob/main/README_ZH_CN.md)


# To-Do List

- [x] Multi-Lingual Support
- [ ] Extend Google Login to username-password login w/ E-mail verification
- [ ] Multiple NS Record Support
- [ ] Multi-Domain Support
- [ ] Domain Name Registeration Duration (ability to allow users to register domains for a certain amount of years and renew) e.g. cron.php
- [ ] Whois Lookup (with on-site contact form to domain owner) / User Contact Information
- [ ] Payment system integration Paypal, Crypto, Alipay, Wechat pay(ability to purchase premium [specified or regex] sub-domains) 
- [ ] Support for more DNS providers (he.net, cloudns, tencent cloud, alicloud)
- [ ] Mailing API for system to notify user of domain status. SMTP and Support for mailer API(mailjet, mailgun, etc.)
- [ ] Support for users to add other records like A, CNAME, etc. Allow users to enable Cloudflare proxy(may not be feasible, Cloudflare ToS)
- [ ] 2FA
- [ ] DNSSEC
- [ ] Change global domain limits on Admin panel
- [ ] Localize assets(some asset cdn not global access friendly)
- [ ] Better theme

# Next Update
- [x] Edit NS Record Record
- [ ] Program setup script
- [ ] Account Status (ability to suspend/cancel accounts)
- [ ] Domain Name Status (ability to require registerations to be approved, suspend/cancel sub-domains)
- [ ] Better Admin panel: Edit NS Record for specific sub-domain, etc.



# Configuration
PLEASE READ AND FOLLOW THE STEPS CAREFULLY.

## Step 1: Creating and Importing Database
Create a MySQL database in your server, and import `cloudflareNIC.sql`. Make sure to take note of your database name, username and password.

## Step 2: Configuring `config.php`

### 1. Database Configuration

Update the following constants with your database credentials:

```php
define('DB_HOST', 'your-database-host');        // e.g. localhost
define('DB_USER', 'your-database-username');
define('DB_PASS', 'your-database-password');
define('DB_NAME', 'your-database-name');
```

---

### 2. Registrar System Setup

Replace the following with your domain details:

```php
define('DOMAIN_NAME', 'example.com');           // Lowercase version
define('DOMAIN_NAME_UP', 'EXAMPLE.COM');        // Uppercase version
define('REGISTRAR_DOMAIN', 'registrar.example.com');  // Domain of the registrar system
```

---

### 3. Cloudflare Setup

Create a scoped API token with permissions for DNS:Read and DNS:Edit for your domain.

```php
define('CLOUDFLARE_API_KEY', 'your-cloudflare-api-token');
define('CLOUDFLARE_ZONE_ID', 'your-cloudflare-zone-id');
```
Get API Token From [Cloudflare dashboard](https://dash.cloudflare.com/profile/api-tokens).
Find your zone ID on the Overview tab for your domain in the Cloudflare dashboard.

---

### 4. HCaptcha Integration

Set up HCaptcha for bot protection.

```php
define('HCAPTCHA_SITE_KEY', 'your-hcaptcha-site-key');
define('HCAPTCHA_SECRET', 'your-hcaptcha-secret-key');
```

Get these from your [hCaptcha dashboard](https://dashboard.hcaptcha.com/).

---

### 5. Google Login Setup

Enable OAuth on [Google Cloud Console](https://console.cloud.google.com/) and get your credentials.

A more detailed guide is available at [Setting Up Google Login](https://documentation.commerce7.com/how-do-i-setup-google-login)

Follow the guide up until step 1 in the guide, you will have all of the informations you need for this step.

```php
define('GOOGLE_CLIENT_ID', 'your-google-client-id');
define('GOOGLE_CLIENT_SECRET', 'your-google-client-secret');
```

Use a redirect URI like:
```
https://your-registrar-domain.com/oauth_callback.php
```

---

## Step 3: Update User Role in MySQL Table
You need to manually update the MySQL entry once you logged in with your Google account, change the `role` field of your user record from `user` to `admin`. After this step, log out and log back in you will be able to access the Admin panel. 



# License
            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2025 Kevin

 Everyone is permitted to copy and distribute verbatim or modified
 copies of this license document, and changing it is allowed as long
 as the name is changed.

            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
   TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

  0. You just DO WHAT THE FUCK YOU WANT TO.



