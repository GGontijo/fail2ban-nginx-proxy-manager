# fail2ban-nginx-proxy-manager
Filters and actions to block/notify when someone fails to log into nginx basic authentication or try to scan your domains.

### Script fail2ban-telegram.sh (Location: /etc/fail2ban/scripts/)
This script sends text messages using Telegram to alert the system administrator about fail2ban actions. It requires one argument, which can be one of the following:

start: Indicates that fail2ban has just started.
stop: Indicates that fail2ban has just stopped.
ban: Indicates that fail2ban has just banned an IP. An optional second argument can be provided to indicate the banned IP.
unban: Indicates that fail2ban has just unbanned an IP. An optional second argument can be provided to indicate the unbanned IP.

### Configuration file npm-auth.local (Location: /etc/fail2ban/jail.d/)
This file is a configuration for fail2ban that monitors failed authentication attempts for the npm-auth service. It is enabled and configured to ban IPs that exceed a certain number of failed authentication attempts within a specified period of time.

### Filter file npm-error.conf (Location: /etc/fail2ban/filter.d/)
This filter file is used by fail2ban to extract information from logs related to errors from the npm-error service.

### Configuration file npm-error.local (Location: /etc/fail2ban/jail.d/)
This file is a configuration for fail2ban that monitors errors from the npm-error service. It is enabled and configured to ban IPs that exceed a certain number of error occurrences within a specified period of time.

### Filter file npm-redirect.conf (Location: /etc/fail2ban/filter.d/)
This filter file is used by fail2ban to extract information from logs related to redirects from the npm-redirect service.

### Configuration file npm-redirect.local (Location: /etc/fail2ban/jail.d/)
This file is a configuration for fail2ban that monitors access attempts to the npm-redirect service. It is enabled and configured to ban IPs that exceed a certain number of access attempts within a specified period of time.

### Filter file npm-auth.conf (Location: /etc/fail2ban/filter.d/)
This filter file is used by fail2ban to extract information from logs related to authentication from the npm-auth service.

### Action file telegram.conf (Location: /etc/fail2ban/action.d/)
This configuration file specifies the actions fail2ban should take when banning or unbanning an IP. It is configured to call the fail2ban-telegram.sh script with the appropriate arguments to start, stop, ban, or unban an IP.
