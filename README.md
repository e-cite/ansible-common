# Ansible Rolle "Common"

Rolle zur Konfiguration allgemeiner Einstellungen:
- hostname
- apt
- packages
- username
- locales
- timezone
- unattended-upgrades

## Anforderungen

- Achtung: Diese Rolle kann den Hostname ändern. In diesem Fall ist das
  Inventory manuell anzupassen.

## Variablen

- `common__new_hostname`: (*Optional, default auf undefined*)

  Neuer Hostname, welcher gesetzt werden soll.
  ~~~yaml
  # Beispiel:
  common__new_hostname: "newhost"
  ~~~

- `common__new_domainname`: (*Optional, default auf undefined*)

  Neuer Domainname, welcher gesetzt werden soll.
  ~~~yaml
  # Beispiel:
  common__new_domainname: "newdomain.de"
  ~~~

- `common__apt_debian_source_url`: (*Optional, default auf Debian CDN*)

  URL eines Debian APT-Repository Servers.
  ~~~yaml
  # Beispiel:
  common__apt_debian_source_url: "http://deb.debian.org/debian"
  ~~~

- `common__apt_debian_source_security_url`: (*Optional, default auf Debian Security*)

  URL eines Debian APT-Repository Security-Servers.
  ~~~yaml
  # Beispiel:
  common__apt_debian_source_security_url: "http://security.debian.org/debian-security"
  ~~~

- `common__apt_proxy`: (*Optional, default auf undefined*)

  Adresse und Port eines APT Caching Proxies, nur HTTP.
  ~~~yaml
  # Beispiel:
  common__apt_proxy: "192.168.1.1:3142"
  ~~~

- `common__adminuser`: (*Optional*)

  Benutzername des Admin-Benutzers.
  ~~~yaml
  # Beispiel:
  common__adminuser: "ansibleadmin"
  ~~~

- `common__adminuser_groups`: (*Optional, default auf undefined*)

  Gruppen des Admin-Benutzers.
  ~~~yaml
  # Beispiel:
  common__adminuser_groups:
    - sudo
    - group1
    - group2
  ~~~

- `common__locales`: (*Optional, default auf undefined*)

  Setzt die Locales, die auf dem System installiert sind.
  ~~~yaml
  # Beispiel:
  common__locales: "de_DE.UTF-8"
  ~~~

- `common__timezone`: (*Optional, default auf undefined*)

  Setzt die Zeitzone.
  ~~~yaml
  # Beispiel:
  common__timezone: "Europe/Berlin"
  ~~~

- `common__ntp_servers`: (*Optional, default auf undefined*)

  Setzt die NTP-Server.
  ~~~yaml
  # Beispiel:
  common__ntp_servers:
    - 0.de.pool.ntp.org
    - 1.de.pool.ntp.org
    - 2.de.pool.ntp.org
    - 3.de.pool.ntp.org
  ~~~

- `common__unattended_upgrade_package_blacklist`: (*Optional, default auf []*)

  Definiert eine Liste mit Paketen, die von unattended-upgrades ausgeschlossen
  werden sollen.
  ~~~yaml
  # Beispiel:
  common__unattended_upgrade_package_blacklist:
    - linux-
    - unattended-upgrades
  ~~~

## Abhängigkeiten

- `community.general`: Zum Setzen von Locales und Zeitzone.

## Beispiel

    - hosts: all
      roles:
        - common

## Lizenz

MIT
