---
title: _U_stringorid, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 611fecad210b9297b6c7cd16c83dbd0c6c3e41a8
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886165"
---
# <a name="ustringorid-class"></a>_U_stringorid, classe
Cette classe d’adaptateur argument permet des noms de ressources (LPCTSTRs) ou ID de ressource (ventes) à passer à une fonction sans nécessiter de l’appelant convertir l’ID d’une chaîne à l’aide de la macro MAKEINTRESOURCE.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class _U_STRINGorID
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Constructeur.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|L’identificateur de ressource.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est conçue pour implémenter des wrappers pour l’API de gestion de ressources Windows telles que la [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042), [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), et [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) fonctions qui acceptent les un argument LPCTSTR qui peut être le nom d’une ressource ou son ID.  
  
 La classe définit deux surcharges de constructeur : une accepte un argument LPCTSTR et l’autre accepte un argument UINT. L’argument UINT est converti en un type de ressource compatible avec les fonctions de gestion des ressources de Windows à l’aide de la macro MAKEINTRESOURCE et le résultat stocké dans le membre de données unique de la classe, [m_lpstr](#_u_stringorid__m_lpstr). L’argument au constructeur LPCTSTR est stocké directement, sans conversion.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr  
 La classe contient la valeur passée à un de ses constructeurs comme un membre de données LPCTSTR public.  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID  
 Le constructeur UINT convertit son argument en un type de ressource compatible avec les fonctions de gestion des ressources de Windows à l’aide de la macro MAKEINTRESOURCE et le résultat est stocké dans le membre de données unique de la classe, [m_lpstr](#_u_stringorid__m_lpstr).  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 Un ID de ressource.  
  
 *lpString*  
 Un nom de ressource.  
  
### <a name="remarks"></a>Notes  
 L’argument au constructeur LPCTSTR est stocké directement, sans conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
