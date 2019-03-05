---
title: Fonctions globales identificateur de sécurité
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: ab5d743c7c6abf7ee3a849a28916ebd32788ef40
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269407"
---
# <a name="security-identifier-global-functions"></a>Fonctions globales identificateur de sécurité

Ces fonctions retournent des objets common SID bien connu.

> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[Sids::AccountOps](#accountops)|Retourne le SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[Sids::Admins](#admins)|Retourne le SID de DOMAIN_ALIAS_RID_ADMINS.|
|[Sids::AnonymousLogon](#anonymouslogon)|Retourne le SID de SECURITY_ANONYMOUS_LOGON_RID.|
|[Sids::AuthenticatedUser](#authenticateduser)|Retourne le SID de SECURITY_AUTHENTICATED_USER_RID.|
|[Sids::BackupOps](#backupops)|Retourne le SID de DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[Sids::Batch](#batch)|Retourne le SID de SECURITY_BATCH_RID.|
|[Sids::CreatorGroup](#creatorgroup)|Retourne le SID de SECURITY_CREATOR_GROUP_RID.|
|[Sids::CreatorGroupServer](#creatorgroupserver)|Retourne le SID de SECURITY_CREATOR_GROUP_SERVER_RID.|
|[Sids::CreatorOwner](#creatorowner)|Retourne le SID de SECURITY_CREATOR_OWNER_RID.|
|[Sids::CreatorOwnerServer](#creatorownerserver)|Retourne le SID de SECURITY_CREATOR_OWNER_SERVER_RID.|
|[Sids::Dialup](#dialup)|Retourne le SID de SECURITY_DIALUP_RID.|
|[Sids::Guests](#guests)|Retourne le SID de DOMAIN_ALIAS_RID_GUESTS.|
|[Sids::Interactive](#interactive)|Retourne le SID de SECURITY_INTERACTIVE_RID.|
|[Sids::Local](#local)|Retourne le SID de SECURITY_LOCAL_RID.|
|[Sids::Network](#network)|Retourne le SID de SECURITY_NETWORK_RID.|
|[Sids::NetworkService](#networkservice)|Retourne le SID de SECURITY_NETWORK_SERVICE_RID.|
|[Sids::Null](#null)|Retourne le SID de SECURITY_NULL_RID.|
|[Sids::PreW2KAccess](#prew2kaccess)|Retourne le SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[Sids::PowerUsers](#powerusers)|Retourne le SID de DOMAIN_ALIAS_RID_POWER_USERS.|
|[Sids::PrintOps](#printops)|Retourne le SID de DOMAIN_ALIAS_RID_PRINT_OPS.|
|[Sids::Proxy](#proxy)|Retourne le SID de SECURITY_PROXY_RID.|
|[Sids::RasServers](#rasservers)|Retourne le SID de DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[Sids::Replicator](#replicator)|Retourne le SID de DOMAIN_ALIAS_RID_REPLICATOR.|
|[Sids::RestrictedCode](#restrictedcode)|Retourne le SID de SECURITY_RESTRICTED_CODE_RID.|
|[Sids::Self](#self)|Retourne le SID de SECURITY_PRINCIPAL_SELF_RID.|
|[Sids::ServerLogon](#serverlogon)|Retourne le SID de SECURITY_SERVER_LOGON_RID.|
|[Sids::Service](#service)|Retourne le SID de SECURITY_SERVICE_RID.|
|[Sids::System](#system)|Retourne le SID de SECURITY_LOCAL_SYSTEM_RID.|
|[SIDs::SystemOps](#systemops)|Retourne le SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Sids::TerminalServer](#terminalserver)|Retourne le SID de SECURITY_TERMINAL_SERVER_RID.|
|[SIDs::Users](#users)|Retourne le SID de DOMAIN_ALIAS_RID_USERS.|
|[Sids::World](#world)|Retourne le SID de SECURITY_WORLD_RID.|

### <a name="requirements"></a>Spécifications

**En-tête :** atlsecurity.h

##  <a name="accountops"></a>  Sids::AccountOps

Retourne le SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  Sids::Admins

Retourne le SID de DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  Sids::AnonymousLogon

Retourne le SID de SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  Sids::AuthenticatedUser

Retourne le SID de SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  Sids::BackupOps

Retourne le SID de DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  Sids::Batch

Retourne le SID de SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  Sids::CreatorGroup

Retourne le SID de SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  Sids::CreatorGroupServer

Retourne le SID de SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  Sids::CreatorOwner

Retourne le SID de SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  Sids::CreatorOwnerServer

Retourne le SID de SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  Sids::Dialup

Retourne le SID de SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  Sids::Guests

Retourne le SID de DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  Sids::Interactive

Retourne le SID de SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  Sids::Local

Retourne le SID de SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

##  <a name="network"></a>  Sids::Network

Retourne le SID de SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  Sids::NetworkService

Retourne le SID de SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Notes

Utilisez NetworkService pour permettre à l’utilisateur NT AUTHORITY\NetworkService lire un objet de sécurité CPerfMon. NetworkService ajoute un SecurityAttribute au code ATL qui permettra la DLL pour vous connecter sous le compte NetworkService sur Windows XP Édition familiale, Windows XP Professionnel, Windows Server 2003 et supérieure système d’exploitation.

Lorsque les compteurs de journal personnalisées sont créées avec la classe ATLServer CPerfMon dans la console MMC Perfmon, les compteurs peuvent être absentes lorsque vous affichez le fichier journal, bien qu’ils s’affichent correctement dans la vue en temps réel. Compteurs de performance personnalisés CPerfMon n’ont pas les autorisations nécessaires pour s’exécuter sous le service "Journaux et alertes de Performance » (smlogsvc.exe) de Windows XP Édition familiale, Windows XP Professionnel, Windows Server 2003 (ou version supérieures) les systèmes d’exploitation. Ce service s’exécute sous le compte « NT AUTHORITY\NetworkService ».

##  <a name="null"></a>  Sids::Null

Retourne le SID de SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  Sids::PreW2KAccess

Retourne le SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  Sids::PowerUsers

Retourne le SID de DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  Sids::PrintOps

Retourne le SID de DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  Sids::Proxy

Retourne le SID de SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  Sids::RasServers

Retourne le SID de DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  Sids::Replicator

Retourne le SID de DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  Sids::RestrictedCode

Retourne le SID de SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  Sids::Self

Retourne le SID de SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  Sids::ServerLogon

Retourne le SID de SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  Sids::Service

Retourne le SID de SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

##  <a name="system"></a>  Sids::System

Retourne le SID de SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  Sids::SystemOps

Retourne le SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  Sids::TerminalServer

Retourne le SID de SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  Sids::Users

Retourne le SID de DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

##  <a name="world"></a>  Sids::World

Retourne le SID de SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
