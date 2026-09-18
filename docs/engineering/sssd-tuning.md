# Making Linux domain logins faster

**Environment:** Higher-education IT · 100 Ubuntu workstations

Waiting a minute to log in is frustrating, especially when it happens every time you sit down at a lab machine. I edited `sssd.conf` to change how SSSD handles directory lookups, bringing domain login time from about **60 seconds to 10 seconds** across an environment of 100 Ubuntu workstations.

## What I changed

The improvement came from configuration edits in `sssd.conf`. I changed how SSSD searches Active Directory, resolves nested groups, applies Group Policy, and caches directory information.

| Configuration area | What I changed | Why it mattered |
| --- | --- | --- |
| `ldap_group_nesting_level` | Limited how deeply SSSD follows nested groups | Reduced the amount of group-resolution work during login |
| Dynamic DNS | Disabled dynamic DNS updates | Removed DNS-update work the lab machines did not need |
| Forest lookups | Prevented searches across the entire forest | Kept identity lookups focused on the directory scope we actually use |
| Group permission searches | Restricted searches to the groups needed for access decisions | Avoided unnecessary group lookups while preserving required permissions |
| `ad_gpo_access_control` | Set Group Policy processing to permissive | Allowed us to evaluate GPO results without having them block logins |
| SSSD cache | Set the cache lifetime to 14,400 seconds (four hours) | Reduced repeated directory queries for information that had already been resolved |

## The balance

A faster login still needs to give someone the right access. I tested the narrower lookup behavior against the users and groups the lab depended on. The four-hour cache also meant directory changes could take time to appear unless the cache was refreshed.

## The result

The change cut roughly 50 seconds from a domain login. It's a small part of using a workstation, but one that people notice immediately.

Organization-specific directory names and configuration values are omitted here.
