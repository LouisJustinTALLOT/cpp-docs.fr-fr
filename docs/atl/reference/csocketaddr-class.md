---
description: 'En savoir plus sur : classe CSocketAddr'
title: CSocketAddr, classe
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
ms.openlocfilehash: eff93b6a8e6d0ea487e3571cd52973d9e17115d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140527"
---
# <a name="csocketaddr-class"></a>CSocketAddr, classe

Cette classe fournit des méthodes pour convertir des noms d’hôtes en adresses hôtes, prenant en charge les formats IPv4 et IPV6.

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
|[CSocketAddr::FindAddr](#findaddr)|Appelez cette méthode pour convertir le nom d’hôte fourni en adresse hôte.|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Appelez cette méthode pour convertir le nom d’hôte IPv4 en adresse hôte.|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Appelez cette méthode pour convertir le nom d’hôte IPv6 en adresse hôte.|
|[CSocketAddr :: GetAddrInfo](#getaddrinfo)|Appelez cette méthode pour retourner un pointeur vers un élément spécifique dans la `addrinfo` liste.|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Appelez cette méthode pour retourner un pointeur vers la `addrinfo` liste.|

## <a name="remarks"></a>Notes

Cette classe fournit une approche IP de version agnostique pour la recherche d’adresses réseau à utiliser avec les fonctions de l’API Windows Sockets et les wrappers de socket dans les bibliothèques.

Les membres de cette classe qui sont utilisés pour rechercher des adresses réseau utilisent la fonction d’API Win32 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo). La version ANSI ou UNICODE de la fonction est appelée selon que votre code est compilé pour ANSI ou UNICODE.

Cette classe prend en charge les adresses réseau IPv4 andIPv6.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsocket. h

## <a name="csocketaddrcsocketaddr"></a><a name="csocketaddr"></a> CSocketAddr::CSocketAddr

Constructeur.

```
CSocketAddr();
```

### <a name="remarks"></a>Notes

Crée un `CSocketAddr` objet et initialise la liste liée contenant des informations de réponse sur l’hôte.

## <a name="csocketaddrfindaddr"></a><a name="findaddr"></a> CSocketAddr::FindAddr

Appelez cette méthode pour convertir le nom d’hôte fourni en adresse hôte.

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
Le nom d’hôte ou l’adresse IP en pointillés.

*szPortOrServiceName*<br/>
Numéro de port ou nom du service sur l’ordinateur hôte.

*nPortNo*<br/>
Le numéro de port.

*flags*<br/>
0 ou combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.

*addr_family*<br/>
Famille d’adresses (par exemple, PF_INET).

*sock_type*<br/>
Type de socket (tel que SOCK_STREAM).

*ai_proto*<br/>
Protocole (par exemple, IPPROTO_IP ou IPPROTO_IPV6).

### <a name="return-value"></a>Valeur renvoyée

Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket différent de zéro en cas d’échec. En cas de réussite, l’adresse calculée est stockée dans une liste liée qui peut être référencée à l’aide `CSocketAddr::GetAddrInfoList` de et de `CSocketAddr::GetAddrInfo` .

### <a name="remarks"></a>Notes

Le paramètre de nom d’hôte peut être au format IPv4 ou IPv6. Cette méthode appelle la fonction d’API Win32 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) pour effectuer la conversion.

## <a name="csocketaddrfindinet4addr"></a><a name="findinet4addr"></a> CSocketAddr::FindINET4Addr

Appelez cette méthode pour convertir le nom d’hôte IPv4 en adresse hôte.

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Paramètres

*szHost*<br/>
Le nom d’hôte ou l’adresse IP en pointillés.

*nPortNo*<br/>
Le numéro de port.

*flags*<br/>
0 ou combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.

*sock_type*<br/>
Type de socket (tel que SOCK_STREAM).

### <a name="return-value"></a>Valeur renvoyée

Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket différent de zéro en cas d’échec. En cas de réussite, l’adresse calculée est stockée dans une liste liée qui peut être référencée à l’aide `CSocketAddr::GetAddrInfoList` de et de `CSocketAddr::GetAddrInfo` .

### <a name="remarks"></a>Notes

Cette méthode appelle la fonction d’API Win32 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) pour effectuer la conversion.

## <a name="csocketaddrfindinet6addr"></a><a name="findinet6addr"></a> CSocketAddr::FindINET6Addr

Appelez cette méthode pour convertir le nom d’hôte IPv6 en adresse hôte.

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>Paramètres

*szHost*<br/>
Le nom d’hôte ou l’adresse IP en pointillés.

*nPortNo*<br/>
Le numéro de port.

*flags*<br/>
0 ou combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.

*sock_type*<br/>
Type de socket (tel que SOCK_STREAM).

### <a name="return-value"></a>Valeur renvoyée

Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket différent de zéro en cas d’échec. En cas de réussite, l’adresse calculée est stockée dans une liste liée qui peut être référencée à l’aide `CSocketAddr::GetAddrInfoList` de et de `CSocketAddr::GetAddrInfo` .

### <a name="remarks"></a>Notes

Cette méthode appelle la fonction d’API Win32 [getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo) pour effectuer la conversion.

## <a name="csocketaddrgetaddrinfo"></a><a name="getaddrinfo"></a> CSocketAddr :: GetAddrInfo

Appelez cette méthode pour retourner un pointeur vers un élément spécifique dans la `addrinfo` liste.

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Référence à un élément spécifique dans la liste [addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow) .

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers la `addrinfo` structure référencée par *nIndex* dans la liste liée contenant les informations de réponse relatives à l’hôte.

## <a name="csocketaddrgetaddrinfolist"></a><a name="getaddrinfolist"></a> CSocketAddr::GetAddrInfoList

Appelez cette méthode pour retourner un pointeur vers la `addrinfo` liste.

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur désignant une liste liée d’une ou plusieurs `addrinfo` structures contenant des informations de réponse sur l’hôte. Pour plus d’informations, consultez [structure addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
