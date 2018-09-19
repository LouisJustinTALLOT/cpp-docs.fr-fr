---
title: Fonctions globales de sécurité identificateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8041d3928b819a7a5a53f89cc3dc2351a29ecf8f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020902"
---
# <a name="security-identifier-global-functions"></a>Fonctions globales identificateur de sécurité

Ces fonctions retournent des objets common SID bien connu.

> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[SIDs::AccountOps](#accountops)|Retourne le SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[SIDs::Admins](#admins)|Retourne le SID de DOMAIN_ALIAS_RID_ADMINS.|
|[SIDs::AnonymousLogon](#anonymouslogon)|Retourne le SID de SECURITY_ANONYMOUS_LOGON_RID.|
|[SIDs::AuthenticatedUser](#authenticateduser)|Retourne le SID de SECURITY_AUTHENTICATED_USER_RID.|
|[SIDs::BackupOps](#backupops)|Retourne le SID de DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[SIDs::batch](#batch)|Retourne le SID de SECURITY_BATCH_RID.|
|[SIDs::CreatorGroup](#creatorgroup)|Retourne le SID de SECURITY_CREATOR_GROUP_RID.|
|[SIDs::CreatorGroupServer](#creatorgroupserver)|Retourne le SID de SECURITY_CREATOR_GROUP_SERVER_RID.|
|[SIDs::CreatorOwner](#creatorowner)|Retourne le SID de SECURITY_CREATOR_OWNER_RID.|
|[SIDs::CreatorOwnerServer](#creatorownerserver)|Retourne le SID de SECURITY_CREATOR_OWNER_SERVER_RID.|
|[SIDs::Dialup](#dialup)|Retourne le SID de SECURITY_DIALUP_RID.|
|[SIDs::Guests](#guests)|Retourne le SID de DOMAIN_ALIAS_RID_GUESTS.|
|[SIDs::interactive](#interactive)|Retourne le SID de SECURITY_INTERACTIVE_RID.|
|[SIDs::local](#local)|Retourne le SID de SECURITY_LOCAL_RID.|
|[SIDs::Network](#network)|Retourne le SID de SECURITY_NETWORK_RID.|
|[SIDs::NetworkService](#networkservice)|Retourne le SID de SECURITY_NETWORK_SERVICE_RID.|
|[SIDs::null](#null)|Retourne le SID de SECURITY_NULL_RID.|
|[SIDs::PreW2KAccess](#prew2kaccess)|Retourne le SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[SIDs::PowerUsers](#powerusers)|Retourne le SID de DOMAIN_ALIAS_RID_POWER_USERS.|
|[SIDs::PrintOps](#printops)|Retourne le SID de DOMAIN_ALIAS_RID_PRINT_OPS.|
|[SIDs::proxy](#proxy)|Retourne le SID de SECURITY_PROXY_RID.|
|[SIDs::RasServers](#rasservers)|Retourne le SID de DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[SIDs::Replicator](#replicator)|Retourne le SID de DOMAIN_ALIAS_RID_REPLICATOR.|
|[SIDs::RestrictedCode](#restrictedcode)|Retourne le SID de SECURITY_RESTRICTED_CODE_RID.|
|[SIDs::Self](#self)|Retourne le SID de SECURITY_PRINCIPAL_SELF_RID.|
|[SIDs::ServerLogon](#serverlogon)|Retourne le SID de SECURITY_SERVER_LOGON_RID.|
|[SIDs::service](#service)|Retourne le SID de SECURITY_SERVICE_RID.|
|[SIDs::System](#system)|Retourne le SID de SECURITY_LOCAL_SYSTEM_RID.|
|[SIDs::SystemOps](#systemops)|Retourne le SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[SIDs::TerminalServer](#terminalserver)|Retourne le SID de SECURITY_TERMINAL_SERVER_RID.|
|[SIDs::Users](#users)|Retourne le SID de DOMAIN_ALIAS_RID_USERS.|
|[SIDs::World](#world)|Retourne le SID de SECURITY_WORLD_RID.|  

### <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h 

##  <a name="accountops"></a>  SIDs::AccountOps

Retourne le SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  SIDs::Admins

Retourne le SID de DOMAIN_ALIAS_RID_ADMINS.  

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  SIDs::AnonymousLogon

Retourne le SID de SECURITY_ANONYMOUS_LOGON_RID.  

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  SIDs::AuthenticatedUser

Retourne le SID de SECURITY_AUTHENTICATED_USER_RID.  

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  SIDs::BackupOps

Retourne le SID de DOMAIN_ALIAS_RID_BACKUP_OPS.  

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  SIDs::batch

Retourne le SID de SECURITY_BATCH_RID.  

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  SIDs::CreatorGroup

Retourne le SID de SECURITY_CREATOR_GROUP_RID.  

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  SIDs::CreatorGroupServer

Retourne le SID de SECURITY_CREATOR_GROUP_SERVER_RID.  

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  SIDs::CreatorOwner

Retourne le SID de SECURITY_CREATOR_OWNER_RID.  

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  SIDs::CreatorOwnerServer

Retourne le SID de SECURITY_CREATOR_OWNER_SERVER_RID.  

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  SIDs::Dialup

Retourne le SID de SECURITY_DIALUP_RID.  

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  SIDs::Guests

Retourne le SID de DOMAIN_ALIAS_RID_GUESTS.  

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  SIDs::interactive

Retourne le SID de SECURITY_INTERACTIVE_RID.  

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  SIDs::local

Retourne le SID de SECURITY_LOCAL_RID.  

```
CSid Local() throw(...);
```

##  <a name="network"></a>  SIDs::Network

Retourne le SID de SECURITY_NETWORK_RID.  

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  SIDs::NetworkService

Retourne le SID de SECURITY_NETWORK_SERVICE_RID.  

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Notes

Utilisez NetworkService pour permettre à l’utilisateur NT AUTHORITY\NetworkService lire un objet de sécurité CPerfMon. NetworkService ajoute un SecurityAttribute au code ATL qui permettra la DLL pour vous connecter sous le compte NetworkService sur Windows XP Édition familiale, Windows XP Professionnel, Windows Server 2003 et supérieure système d’exploitation.

Lorsque les compteurs de journal personnalisées sont créées avec la classe ATLServer CPerfMon dans la console MMC Perfmon, les compteurs peuvent être absentes lorsque vous affichez le fichier journal, bien qu’ils s’affichent correctement dans la vue en temps réel. Compteurs de performance personnalisés CPerfMon n’ont pas les autorisations nécessaires pour s’exécuter sous le service "Journaux et alertes de Performance » (smlogsvc.exe) de Windows XP Édition familiale, Windows XP Professionnel, Windows Server 2003 (ou version supérieures) les systèmes d’exploitation. Ce service s’exécute sous le compte « NT AUTHORITY\NetworkService ».

##  <a name="null"></a>  SIDs::null

Retourne le SID de SECURITY_NULL_RID.  

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  SIDs::PreW2KAccess

Retourne le SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.  

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  SIDs::PowerUsers

Retourne le SID de DOMAIN_ALIAS_RID_POWER_USERS.  

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  SIDs::PrintOps

Retourne le SID de DOMAIN_ALIAS_RID_PRINT_OPS.  

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  SIDs::proxy

Retourne le SID de SECURITY_PROXY_RID.  

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  SIDs::RasServers

Retourne le SID de DOMAIN_ALIAS_RID_RAS_SERVERS.  

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  SIDs::Replicator

Retourne le SID de DOMAIN_ALIAS_RID_REPLICATOR.  

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  SIDs::RestrictedCode

Retourne le SID de SECURITY_RESTRICTED_CODE_RID.  

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  SIDs::Self

Retourne le SID de SECURITY_PRINCIPAL_SELF_RID.  

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  SIDs::ServerLogon

Retourne le SID de SECURITY_SERVER_LOGON_RID.  

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  SIDs::service

Retourne le SID de SECURITY_SERVICE_RID.  

```
CSid Service() throw(...);
```

##  <a name="system"></a>  SIDs::System

Retourne le SID de SECURITY_LOCAL_SYSTEM_RID.  

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  SIDs::SystemOps

Retourne le SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.  

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  SIDs::TerminalServer

Retourne le SID de SECURITY_TERMINAL_SERVER_RID.  

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  SIDs::Users

Retourne le SID de DOMAIN_ALIAS_RID_USERS.  

```
CSid Users() throw(...);
```

##  <a name="world"></a>  SIDs::World

Retourne le SID de SECURITY_WORLD_RID.  

```
CSid World() throw(...);
```

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
