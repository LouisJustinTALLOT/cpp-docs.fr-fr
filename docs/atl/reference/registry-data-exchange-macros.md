---
title: Macros d’échange de données de Registre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7473bed5e4bf973dcea4d186e9b5b3367fb03ff1
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880357"
---
# <a name="registry-data-exchange-macros"></a>Macros d’échange de données de Registre
Ces macros effectuent des opérations d’échange de données de Registre.  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marque le début de la carte de l’échange de données de Registre.|  
|[END_RDX_MAP](#end_rdx_map)|Marque la fin de la carte de l’échange de données de Registre.|  
|[RDX_BINARY](#rdx_binary)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type BYTE.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié du type CString.|  
|[RDX_DWORD](#rdx_dword)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type DWORD.|  
|[RDX_TEXT](#rdx_text)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type TCHAR.|  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlplus.h  
   
##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP  
 Marque le début de la carte de l’échange de données de Registre.  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>Notes  
 Les macros suivantes sont utilisées dans l’Explorateur de l’échange de données de Registre pour lire et écrire des entrées dans le Registre système :  
  
|Macro|Description|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type BYTE.|  
|[RDX_DWORD](#rdx_dword)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type DWORD.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié du type CString.|  
|[RDX_TEXT](#rdx_text)|Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type TCHAR.|  
  
 La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisé chaque fois que votre code a besoin d’échanger des données entre le Registre système et le variables spécifiées dans le mappage RDX.  
  
##  <a name="end_rdx_map"></a>  END_RDX_MAP  
 Marque la fin de la carte de l’échange de données de Registre.  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>  RDX_BINARY  
 Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type BYTE.  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Paramètres  
 *Clé racine*  
 Racine de la clé de Registre.  
  
 *sous-clé*  
 La sous-clé de Registre.  
  
 *nom de valeur*  
 La clé de Registre.  
  
 *Membre*  
 La variable membre à associer à l’entrée de Registre spécifié.  
  
 *member_size*  
 La taille, en octets, de la variable membre.  
  
### <a name="remarks"></a>Notes  
 Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisé pour effectuer l’échange de données entre le Registre système et les variables de membre dans le mappage RDX.  
  
##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT  
 Associe l’entrée de Registre spécifiée à une variable de membre spécifié du type CString.  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Paramètres  
 *Clé racine*  
 Racine de la clé de Registre.  
  
 *sous-clé*  
 La sous-clé de Registre.  
  
 *nom de valeur*  
 La clé de Registre.  
  
 *Membre*  
 La variable membre à associer à l’entrée de Registre spécifié.  
  
 *member_size*  
 La taille, en octets, de la variable membre.  
  
### <a name="remarks"></a>Notes  
 Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisé pour effectuer l’échange de données entre le Registre système et les variables de membre dans le mappage RDX.  
  
##  <a name="rdx_dword"></a>  RDX_DWORD  
 Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type DWORD.  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Paramètres  
 *Clé racine*  
 Racine de la clé de Registre.  
  
 *sous-clé*  
 La sous-clé de Registre.  
  
 *nom de valeur*  
 La clé de Registre.  
  
 *Membre*  
 La variable membre à associer à l’entrée de Registre spécifié.  
  
 *member_size*  
 La taille, en octets, de la variable membre.  
  
### <a name="remarks"></a>Notes  
 Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisé pour effectuer l’échange de données entre le Registre système et les variables de membre dans le mappage RDX.  
  
##  <a name="rdx_text"></a>  RDX_TEXT  
 Associe l’entrée de Registre spécifiée à une variable de membre spécifié de type TCHAR.  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Paramètres  
 *Clé racine*  
 Racine de la clé de Registre.  
  
 *sous-clé*  
 La sous-clé de Registre.  
  
 *nom de valeur*  
 La clé de Registre.  
  
 *Membre*  
 La variable membre à associer à l’entrée de Registre spécifié.  
  
 *member_size*  
 La taille, en octets, de la variable membre.  
  
### <a name="remarks"></a>Notes  
 Cette macro est utilisée conjointement avec les macros BEGIN_RDX_MAP et END_RDX_MAP pour associer une variable membre à une entrée de Registre donnée. La fonction globale [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), ou la fonction membre du même nom créé par les macros BEGIN_RDX_MAP et END_RDX_MAP, doit être utilisé pour effectuer l’échange de données entre le Registre système et les variables de membre dans le mappage RDX.  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







