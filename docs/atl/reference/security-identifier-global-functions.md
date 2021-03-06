---
description: 'En savoir plus sur : fonctions globales d’identificateur de sécurité'
title: Fonctions globales d’identificateur de sécurité
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
ms.openlocfilehash: 035cdf2991f00d518bf4cfc3a93a226650728846
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138864"
---
# <a name="security-identifier-global-functions"></a>Fonctions globales d’identificateur de sécurité

Ces fonctions retournent des objets SID communs connus.

> [!IMPORTANT]
> Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|Nom|Description|
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
|[Sids::SystemOps](#systemops)|Retourne le SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Sids::TerminalServer](#terminalserver)|Retourne le SID de SECURITY_TERMINAL_SERVER_RID.|
|[Sids::Users](#users)|Retourne le SID de DOMAIN_ALIAS_RID_USERS.|
|[Sids::World](#world)|Retourne le SID de SECURITY_WORLD_RID.|

### <a name="requirements"></a>Spécifications

**En-tête :** ATLSecurity. h

## <a name="sidsaccountops"></a><a name="accountops"></a> Sid :: AccountOps

Retourne le SID de DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a> Sid :: admins

Retourne le SID de DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a> Sid :: AnonymousLogon

Retourne le SID de SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a> Sid :: AuthenticatedUser

Retourne le SID de SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a> Sid :: BackupOps

Retourne le SID de DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a> Sid :: batch

Retourne le SID de SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a> Sid :: CreatorGroup

Retourne le SID de SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a> Sid :: CreatorGroupServer

Retourne le SID de SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a> Sid :: CreatorOwner

Retourne le SID de SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a> Sid :: CreatorOwnerServer

Retourne le SID de SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a> Sid ::D ialup

Retourne le SID de SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a> Sid :: invités

Retourne le SID de DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a> Sid :: Interactive

Retourne le SID de SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a> Sid :: local

Retourne le SID de SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a> Sid :: réseau

Retourne le SID de SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a> Sid :: NetworkService

Retourne le SID de SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Notes

Utilisez NetworkService pour permettre à l’utilisateur NT AUTHORITY\NetworkService de lire un objet de sécurité CPerfMon. NetworkService ajoute un SecurityAttribute au code ATLServer, ce qui permet à la DLL de se connecter sous le compte NetworkService sur Windows XP Édition personnelle, Windows XP professionnel, Windows Server 2003 et le système d’exploitation ultérieur.

Lorsque des compteurs de journalisation personnalisés sont créés avec la classe ATLServer CPerfMon dans la console MMC Perfmon, les compteurs peuvent ne pas apparaître lors de l’affichage du fichier journal, bien qu’ils s’affichent correctement dans l’affichage en temps réel. Les compteurs de performance personnalisés CPerfMon ne disposent pas des autorisations nécessaires pour s’exécuter sous le service « Journaux et alertes de performance » (smlogsvc.exe) sur les systèmes d’exploitation Windows XP édition familial, Windows XP professionnel, Windows Server 2003 (ou version ultérieure). Ce service s’exécute sous le compte « NT AUTHORITY\NetworkService ».

## <a name="sidsnull"></a><a name="null"></a> Sid :: null

Retourne le SID de SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a> Sid ::P reW2KAccess

Retourne le SID de DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a> Sid ::P owerUsers

Retourne le SID de DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a> Sid ::P rintOps

Retourne le SID de DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a> Sid ::P SPROXY

Retourne le SID de SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a> Sid :: RasServers

Retourne le SID de DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a> Sid :: Replicator

Retourne le SID de DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a> Sid :: RestrictedCode

Retourne le SID de SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a> Sid :: Self

Retourne le SID de SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a> Sid :: ServerLogon

Retourne le SID de SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a> Sid :: service

Retourne le SID de SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a> Sid :: System

Retourne le SID de SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a> Sid :: SystemOps

Retourne le SID de DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a> Sid :: TerminalServer

Retourne le SID de SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a> Sid :: Users

Retourne le SID de DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a> Sid :: World

Retourne le SID de SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
