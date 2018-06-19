---
title: Classe de _U_STRINGorID | Documents Microsoft
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
ms.openlocfilehash: 2a601b1c64b28681c13a0b9e8f42156d8820cb4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359660"
---
# <a name="ustringorid-class"></a>Classe de _U_STRINGorID
Cette classe d’argument d’adaptateur permet à deux noms de ressources ( `LPCTSTR`s) ou l’ID de ressource ( **UINT**s) à passer à une fonction sans nécessiter de l’appelant convertir une chaîne à l’aide de l’ID du **MAKEINTRESOURCE** (macro).  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
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
 Cette classe est conçue pour implémenter des wrappers pour l’API de gestion de ressources Windows telles que la [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042), [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), et [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) fonctions qui acceptent un `LPCTSTR` argument peut être le nom d’une ressource ou son ID.  
  
 La classe définit deux surcharges de constructeur : une accepte un `LPCTSTR` argument et l’autre accepte un **UINT** argument. Le **UINT** argument est converti en un type de ressource compatible avec les fonctions de gestion des ressources de Windows à l’aide de la **MAKEINTRESOURCE** macro et le résultat stocké dans le membre de données de la classe, [m_lpstr](#_u_stringorid__m_lpstr). L’argument de la `LPCTSTR` constructeur est stocké directement, sans conversion.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr  
 La classe contient la valeur passée à un de ses constructeurs comme publique `LPCTSTR` membre de données.  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID  
 Le **UINT** constructeur convertit son argument en un type de ressource compatible avec les fonctions de gestion des ressources de Windows à l’aide de la **MAKEINTRESOURCE** macro et le résultat est stocké dans unique de la classe membre de données, [m_lpstr](#_u_stringorid__m_lpstr).  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>Paramètres  
 `nID`  
 Un ID de ressource.  
  
 `lpString`  
 Un nom de ressource.  
  
### <a name="remarks"></a>Notes  
 L’argument de la `LPCTSTR` constructeur est stocké directement, sans conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
