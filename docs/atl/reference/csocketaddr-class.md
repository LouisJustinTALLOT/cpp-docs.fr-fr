---
title: Classe de CSocketAddr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
dev_langs:
- C++
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 830b1087d0a4792b449c516ed12ad7e8a84b2a51
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363394"
---
# <a name="csocketaddr-class"></a>Classe de CSocketAddr
Cette classe fournit des méthodes de conversion des noms d’hôte en adresses d’hôte, prenant en charge les formats IPv4 et IPV6.  
  
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
|[CSocketAddr::FindAddr](#findaddr)|Appelez cette méthode pour convertir le nom d’hôte fourni à l’adresse de l’hôte.|  
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Appelez cette méthode pour convertir le nom d’hôte IPv4 à l’adresse de l’hôte.|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Appelez cette méthode pour convertir le nom d’hôte IPv6 à l’adresse de l’hôte.|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Appelez cette méthode pour retourner un pointeur vers un élément spécifique de la **addrinfo** liste.|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Appelez cette méthode pour retourner un pointeur vers le **addrinfo** liste.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit une adresse IP version agnostique approche pour rechercher les adresses de réseau pour une utilisation avec Windows sockets fonctions API ainsi que les wrappers de socket dans les bibliothèques.  
  
 Les membres de cette classe qui sont utilisés pour rechercher des adresses réseau utilisent la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520).  
  
 Cette classe prend en charge les deux adresses de réseau IPv4 andIPv6.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsocket.h  
  
##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr  
 Constructeur.  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>Notes  
 Crée un `CSocketAddr` de l’objet et initialise la liste liée contenant les informations de réponse de l’ordinateur hôte.  
  
##  <a name="findaddr"></a>  CSocketAddr::FindAddr  
 Appelez cette méthode pour convertir le nom d’hôte fourni à l’adresse de l’hôte.  
  
```
int FindAddr(
    const char *szHost,
    const char *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const char *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```  
  
### <a name="parameters"></a>Paramètres  
 `szHost`  
 Le nom d’hôte ou l’adresse en pointillés.  
  
 *szPortOrServiceName*  
 Le numéro de port ou le nom du service sur l’ordinateur hôte.  
  
 `nPortNo`  
 Le numéro de port.  
  
 `flags`  
 0 ou une combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.  
  
 *addr_family*  
 Famille (par exemple, PF_INET) d’adresse.  
  
 `sock_type`  
 Type de socket (par exemple, SOCK_STREAM).  
  
 *ai_proto*  
 Protocole (tel que IPPROTO_IP ou IPPROTO_IPV6).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur de Socket Windows différente de zéro en cas d’échec. Si la réussite, l’adresse calculée est stockée dans une liste liée qui peut-être être référencée à l’aide de `CSocketAddr::GetAddrInfoList` et `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Notes  
 Le paramètre de nom d’hôte peut être au format IPv4 ou IPv6. Cette méthode appelle la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) pour effectuer la conversion.  
  
##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr  
 Appelez cette méthode pour convertir le nom d’hôte IPv4 à l’adresse de l’hôte.  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Paramètres  
 `szHost`  
 Le nom d’hôte ou l’adresse en pointillés.  
  
 `nPortNo`  
 Le numéro de port.  
  
 `flags`  
 0 ou une combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.  
  
 `sock_type`  
 Type de socket (par exemple, SOCK_STREAM).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur de Socket Windows différente de zéro en cas d’échec. Si la réussite, l’adresse calculée est stockée dans une liste liée qui peut-être être référencée à l’aide de `CSocketAddr::GetAddrInfoList` et `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) pour effectuer la conversion.  
  
##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr  
 Appelez cette méthode pour convertir le nom d’hôte IPv6 à l’adresse de l’hôte.  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Paramètres  
 `szHost`  
 Le nom d’hôte ou l’adresse en pointillés.  
  
 `nPortNo`  
 Le numéro de port.  
  
 `flags`  
 0 ou une combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.  
  
 `sock_type`  
 Type de socket (par exemple, SOCK_STREAM).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur de Socket Windows différente de zéro en cas d’échec. Si la réussite, l’adresse calculée est stockée dans une liste liée qui peut-être être référencée à l’aide de `CSocketAddr::GetAddrInfoList` et `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) pour effectuer la conversion.  
  
##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo  
 Appelez cette méthode pour retourner un pointeur vers un élément spécifique de la **addrinfo** liste.  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Une référence à un élément spécifique de la [addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530) liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le **addrinfo** structure référencée par `nIndex` dans la liste liée contenant les informations de réponse de l’ordinateur hôte.  
  
##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList  
 Appelez cette méthode pour retourner un pointeur vers le **addrinfo** liste.  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une liste liée d’une ou plusieurs `addrinfo` structures contenant des informations de réponse sur l’ordinateur hôte. Pour plus d’informations, consultez [addrinfo structure](https://msdn.microsoft.com/library/windows/desktop/ms737530).
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
