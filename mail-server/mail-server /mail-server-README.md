# Mail Server (Postfix + Dovecot + Maildir)
This section documents my full mail server stack built in my homelab.

#Components
- Postfix (SMTP server)
- Dovecot (IMAP server)
- Maildir storage
- Local delivery testing
- SMTP connectivity testing

## What I demonstrate 
- Full SMTP delivery pipeline
- Maildir structure and permissions
- Postfix configuration (main.cf, master.cf)
- Dovecot configuration (10-mail.conf, 10-auth.conf)
- Testiing with ´telnet´, ´nc´, and WP-CLI

## Skills shown
- Linux service management
- Email protocols (SMTP, IMAP)
- Log analysis (journalctl, syslog)
- Security basics (inet_interfaces, TLS optional)
