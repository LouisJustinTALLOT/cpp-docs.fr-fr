---
title: _U_rect, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
dev_langs:
- C++
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ebb76d2f373862b39f2a3742481e14523a7a94b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882219"
---
# <a name="urect-class"></a>_U_rect, classe
Permet à cette classe d’adaptateur argument soit `RECT` les pointeurs ou références à passer à une fonction qui est implémentée en termes de pointeurs.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class _U_RECT
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|Constructeur.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Pointeur vers un `RECT`.|  
  
## <a name="remarks"></a>Notes  
 La classe définit deux surcharges de constructeur : une accepte un **RECT &** argument et l’autre accepte un `LPRECT` argument. Le premier constructeur stocke l’adresse de l’argument de référence dans le membre de données unique de la classe, [m_lpRect](#_u_rect__m_lprect). L’argument du constructeur de pointeur est stocké directement, sans conversion.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlwin.h  
  
##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect  
 La classe contient la valeur passée à un de ses constructeurs comme publique `LPRECT` membre de données.  
  
```
LPRECT m_lpRect;
```  
  
##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT  
 L’adresse de l’argument de référence est stockée dans le membre de données unique de la classe, [m_lpRect](#_u_rect__m_lprect).  
  
```
_U_RECT(RECT& rc);  
_U_RECT(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *rc*  
 Un `RECT` référence.  
  
 *lpRect*  
 Un `RECT` pointeur.  
  
### <a name="remarks"></a>Notes  
 L’argument du constructeur de pointeur est stocké directement, sans conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
