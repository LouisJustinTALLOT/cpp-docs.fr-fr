---
title: Macros d’exceptions | Microsoft Docs
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
ms.openlocfilehash: 2473a2a66792f1bfff18086030a8898a67339e10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024279"
---
# <a name="exception-handling-macros"></a>Macros de gestion des exceptions

Ces macros prennent en charge la gestion des exceptions.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Instructions permettant de gérer les erreurs qui se produisent dans associé `_ATLTRY`.|
|[_ATLCATCHALL](#_atlcatchall)|Instructions permettant de gérer les erreurs qui se produisent dans associé `_ATLTRY`.|
|[_ATLTRY](#_atltry)|Marque une section de code protégée où une erreur peut éventuellement se produire.|

## <a name="requirements"></a>Configuration requise :

**En-tête :** atldef.h

##  <a name="_atlcatch"></a>  _ATLCATCH

Instructions permettant de gérer les erreurs qui se produisent dans associé `_ATLTRY`.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Paramètres

*e*<br/>
Exception à intercepter.

### <a name="remarks"></a>Notes

Utilisé conjointement avec `_ATLTRY`. Se résout en C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pour gérer un type donné des exceptions C++.

##  <a name="_atlcatchall"></a>  _ATLCATCHALL

Instructions permettant de gérer les erreurs qui se produisent dans associé `_ATLTRY`.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Notes

Utilisé conjointement avec `_ATLTRY`. Se résout en C++ [catch (...) ](../../cpp/try-throw-and-catch-statements-cpp.md) pour gérer tous les types d’exceptions C++.

##  <a name="_atltry"></a>  _ATLTRY

Marque une section de code protégée où une erreur peut éventuellement se produire.

```
_ATLTRY
```

### <a name="remarks"></a>Notes

Utilisé conjointement avec [_ATLCATCH](#_atlcatch) ou [_ATLCATCHALL](#_atlcatchall). Correspond au symbole C++ [essayez](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
