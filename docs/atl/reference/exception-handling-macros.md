---
title: Macros d’exceptions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05ee381aa792c252fc9b80107d25e15e7d1ecfca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358975"
---
# <a name="exception-handling-macros"></a>Macros de gestion des exceptions
Ces macros prennent en charge la gestion des exceptions.  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|Instructions permettant de gérer les erreurs qui se produisent dans le type `_ATLTRY`.|  
|[_ATLCATCHALL](#_atlcatchall)|Instructions permettant de gérer les erreurs qui se produisent dans le type `_ATLTRY`.|  
|[_ATLTRY](#_atltry)|Marque une section de code protégé où une erreur peut éventuellement se produire.|  
  
## <a name="requirements"></a>Configuration requise :
**En-tête :** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH  
 Instructions permettant de gérer les erreurs qui se produisent dans le type `_ATLTRY`.  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>Paramètres  
 *e*  
 Exception à intercepter.  
  
### <a name="remarks"></a>Notes  
 Utilisée conjointement avec `_ATLTRY`. Est résolu en C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pour la gestion d’un type donné d’exceptions C++.  
  
##  <a name="_atlcatchall"></a>  _ATLCATCHALL  
 Instructions permettant de gérer les erreurs qui se produisent dans le type `_ATLTRY`.  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>Notes  
 Utilisée conjointement avec `_ATLTRY`. Est résolu en C++ [catch (...) ](../../cpp/try-throw-and-catch-statements-cpp.md) pour la gestion de tous les types d’exceptions C++.  
  
##  <a name="_atltry"></a>  _ATLTRY  
 Marque une section de code protégé où une erreur peut éventuellement se produire.  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>Notes  
 Utilisée conjointement avec [_ATLCATCH](#_atlcatch) ou [_ATLCATCHALL](#_atlcatchall). Correspond au symbole C++ [essayez](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)
