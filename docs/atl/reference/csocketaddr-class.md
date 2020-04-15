---
title: Classe CSocketAddr
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: 66d33d62212389a2b0f318250c1c16a99167c6eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330678"
---
# <a name="csocketaddr-class"></a>Classe CSocketAddr

Cette classe fournit des méthodes pour convertir les noms d’hôtes pour héberger des adresses, en soutenant les formats IPv4 et IPV6.

## <a name="syntax"></a>Syntaxe

```
class CSocketAddr
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|Appelez cette méthode pour convertir le nom d’hôte fourni à l’adresse hôte.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Appelez cette méthode pour convertir le nom d’hôte IPv4 à l’adresse hôte.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Appelez cette méthode pour convertir le nom d’hôte IPv6 à l’adresse hôte.|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Appelez cette méthode pour retourner un pointeur à un élément spécifique de la `addrinfo` liste.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Appelez cette méthode pour retourner `addrinfo` un pointeur à la liste.|

## <a name="remarks"></a>Notes

Cette classe offre une approche agnostique version IP pour rechercher des adresses réseau pour une utilisation avec les fonctions API de prises Windows et les emballages de prises dans les bibliothèques.

Les membres de cette classe qui sont utilisés pour rechercher des adresses réseau utilisent la fonction Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). La version ANSI ou UNICODE de la fonction est appelée selon que votre code est compilé pour ANSI ou UNICODE.

Cette classe prend en charge les adresses réseau IPv4 et IPv6.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsocket.h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a>CSocketAddr::CSocketAddr

Constructeur.

```
CSocketAddr();
```

### <a name="remarks"></a>Notes

Crée un `CSocketAddr` nouvel objet et initialise la liste liée contenant des informations de réponse sur l’hôte.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a>CSocketAddr::FindAddr

Appelez cette méthode pour convertir le nom d’hôte fourni à l’adresse hôte.

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>Paramètres

*szHost*<br/>
Le nom d’hôte ou l’adresse IP pointillée.

*szPortOrServiceName (en)*<br/>
Le numéro de port ou le nom du service sur l’hôte.

*nPortNo*<br/>
Numéro de port.

*Drapeaux*<br/>
0 ou combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.

*addr_family*<br/>
Adressez-vous à la famille (comme PF_INET).

*sock_type*<br/>
Type de prise (comme SOCK_STREAM).

*ai_proto*<br/>
Protocole (comme IPPROTO_IP ou IPPROTO_IPV6).

### <a name="return-value"></a>Valeur de retour

Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket nonzero sur l’échec. En cas de succès, l’adresse calculée est `CSocketAddr::GetAddrInfoList` stockée `CSocketAddr::GetAddrInfo`dans une liste liée qui peut être référencée à l’aide et .

### <a name="remarks"></a>Notes

Le paramètre du nom d’hôte peut être en format IPv4 ou IPv6. Cette méthode appelle la fonction Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) pour effectuer la conversion.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a>CSocketAddr::FindINET4Addr

Appelez cette méthode pour convertir le nom d’hôte IPv4 à l’adresse hôte.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Paramètres

*szHost*<br/>
Le nom d’hôte ou l’adresse IP pointillée.

*nPortNo*<br/>
Numéro de port.

*Drapeaux*<br/>
0 ou combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.

*sock_type*<br/>
Type de prise (comme SOCK_STREAM).

### <a name="return-value"></a>Valeur de retour

Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket nonzero sur l’échec. En cas de succès, l’adresse calculée est `CSocketAddr::GetAddrInfoList` stockée `CSocketAddr::GetAddrInfo`dans une liste liée qui peut être référencée à l’aide et .

### <a name="remarks"></a>Notes

Cette méthode appelle la fonction Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) pour effectuer la conversion.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a>CSocketAddr::FindINET6Addr

Appelez cette méthode pour convertir le nom d’hôte IPv6 à l’adresse hôte.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Paramètres

*szHost*<br/>
Le nom d’hôte ou l’adresse IP pointillée.

*nPortNo*<br/>
Numéro de port.

*Drapeaux*<br/>
0 ou combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.

*sock_type*<br/>
Type de prise (comme SOCK_STREAM).

### <a name="return-value"></a>Valeur de retour

Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket nonzero sur l’échec. En cas de succès, l’adresse calculée est `CSocketAddr::GetAddrInfoList` stockée `CSocketAddr::GetAddrInfo`dans une liste liée qui peut être référencée à l’aide et .

### <a name="remarks"></a>Notes

Cette méthode appelle la fonction Win32 API [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) pour effectuer la conversion.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo

Appelez cette méthode pour retourner un pointeur à un élément spécifique de la `addrinfo` liste.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Une référence à un élément spécifique dans la liste [addrinfo.](/windows/win32/api/ws2def/ns-ws2def-addrinfow)

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à la `addrinfo` structure référencée par *nIndex* dans la liste liée contenant des informations de réponse sur l’hôte.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList

Appelez cette méthode pour retourner `addrinfo` un pointeur à la liste.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une liste `addrinfo` liée d’une ou plusieurs structures contenant des informations de réponse sur l’hôte. Pour plus d’informations, voir [la structure addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
