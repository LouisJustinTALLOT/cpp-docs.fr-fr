---
title: Classe de CSocketAddr | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ee3f69874460d09e495a237985a98ace19134a01
ms.lasthandoff: 02/24/2017

---
# <a name="csocketaddr-class"></a>CSocketAddr (classe)
Cette classe fournit des méthodes pour la conversion des noms d’hôte en adresses d’hôte, prenant en charge les formats IPv4 et IPV6.  
  
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
|[CSocketAddr::FindAddr](#findaddr)|Appelez cette méthode pour convertir le nom d’hôte fourni à l’adresse d’hôte.|  
|[CSocketAddr::FindINET4Addr](#findinet4addr)|Appelez cette méthode pour convertir le nom d’hôte IPv4 à l’adresse d’hôte.|  
|[CSocketAddr::FindINET6Addr](#findinet6addr)|Appelez cette méthode pour convertir le nom d’hôte IPv6 à l’adresse d’hôte.|  
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|Appelez cette méthode pour retourner un pointeur vers un élément spécifique de la **addrinfo** liste.|  
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|Appelez cette méthode pour retourner un pointeur vers le **addrinfo** liste.|  
  
## <a name="remarks"></a>Remarques  
 Cette classe fournit une version IP agnostique approche pour rechercher les adresses de réseau pour une utilisation avec Windows sockets fonctions API et les wrappers de socket dans les bibliothèques.  
  
 Les membres de cette classe qui sont utilisés pour rechercher des adresses réseau utilisent la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520).  
  
 Cette classe prend en charge les deux adresses de réseau IPv4 andIPv6.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsocket.h  
  
##  <a name="csocketaddr"></a>CSocketAddr::CSocketAddr  
 Constructeur.  
  
```
CSocketAddr();
```  
  
### <a name="remarks"></a>Remarques  
 Crée un `CSocketAddr` de l’objet et initialise la liste liée contenant les informations de réponse de l’hôte.  
  
##  <a name="findaddr"></a>CSocketAddr::FindAddr  
 Appelez cette méthode pour convertir le nom d’hôte fourni à l’adresse d’hôte.  
  
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
 Le nom d’hôte ou les adresses IP en pointillé.  
  
 *szPortOrServiceName*  
 Le numéro de port ou le nom de service sur l’hôte.  
  
 `nPortNo`  
 Le numéro de port.  
  
 `flags`  
 0 ou une combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.  
  
 *addr_family*  
 Adresse famille (par exemple, PF_INET).  
  
 `sock_type`  
 Type de socket (par exemple, SOCK_STREAM).  
  
 *ai_proto*  
 Protocole (tel que IPPROTO_IP ou IPPROTO_IPV6).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket différent de zéro en cas d’échec. Si réussie, l’adresse calculée est stockée dans une liste liée qui peut-être être référencée à l’aide de `CSocketAddr::GetAddrInfoList` et `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Notes  
 Le paramètre de nom d’hôte peut être au format IPv4 ou IPv6. Cette méthode appelle la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) pour effectuer la conversion.  
  
##  <a name="findinet4addr"></a>CSocketAddr::FindINET4Addr  
 Appelez cette méthode pour convertir le nom d’hôte IPv4 à l’adresse d’hôte.  
  
```
int FindINET4Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Paramètres  
 `szHost`  
 Le nom d’hôte ou les adresses IP en pointillé.  
  
 `nPortNo`  
 Le numéro de port.  
  
 `flags`  
 0 ou une combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.  
  
 `sock_type`  
 Type de socket (par exemple, SOCK_STREAM).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket différent de zéro en cas d’échec. Si réussie, l’adresse calculée est stockée dans une liste liée qui peut-être être référencée à l’aide de `CSocketAddr::GetAddrInfoList` et `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Remarques  
 Cette méthode appelle la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) pour effectuer la conversion.  
  
##  <a name="findinet6addr"></a>CSocketAddr::FindINET6Addr  
 Appelez cette méthode pour convertir le nom d’hôte IPv6 à l’adresse d’hôte.  
  
```
int FindINET6Addr(
    const char *szHost,
    int nPortNo,
    int flags,
    int sock_type,);
```  
  
### <a name="parameters"></a>Paramètres  
 `szHost`  
 Le nom d’hôte ou les adresses IP en pointillé.  
  
 `nPortNo`  
 Le numéro de port.  
  
 `flags`  
 0 ou une combinaison de AI_PASSIVE, AI_CANONNAME ou AI_NUMERICHOST.  
  
 `sock_type`  
 Type de socket (par exemple, SOCK_STREAM).  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne zéro si l’adresse est calculée avec succès. Retourne un code d’erreur Windows Socket différent de zéro en cas d’échec. Si réussie, l’adresse calculée est stockée dans une liste liée qui peut-être être référencée à l’aide de `CSocketAddr::GetAddrInfoList` et `CSocketAddr::GetAddrInfo`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle la fonction API Win32 [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520) pour effectuer la conversion.  
  
##  <a name="getaddrinfo"></a>CSocketAddr::GetAddrInfo  
 Appelez cette méthode pour retourner un pointeur vers un élément spécifique de la **addrinfo** liste.  
  
```
addrinfo* const GetAddrInfoint nIndex = 0) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Une référence à un élément spécifique de la [addrinfo](http://msdn.microsoft.com/library/windows/desktop/ms737530) liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le **addrinfo** structure référencée par `nIndex` dans la liste liée contenant les informations de réponse de l’hôte.  
  
##  <a name="getaddrinfolist"></a>CSocketAddr::GetAddrInfoList  
 Appelez cette méthode pour retourner un pointeur vers le **addrinfo** liste.  
  
```
addrinfo* const GetAddrInfoList() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une liste liée d’une ou plusieurs `addrinfo` structures contenant des informations de réponse sur l’ordinateur hôte. Pour plus d’informations sur la `addrinfo` de la structure, consultez l’article « addrinfo » dans le [MSDN Library](http://go.microsoft.com/fwlink/linkid=556)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

