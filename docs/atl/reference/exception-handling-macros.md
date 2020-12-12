---
description: En savoir plus sur les macros de gestion des exceptions
title: Macros de gestion des exceptions
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 8d5e6564dec5769fb172c66b3102677e58cbd788
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139826"
---
# <a name="exception-handling-macros"></a>Macros de gestion des exceptions

Ces macros assurent la prise en charge de la gestion des exceptions.

|Nom|Description|
|-|-|
|[_ATLCATCH](#_atlcatch)|Instruction (s) pour gérer les erreurs qui se produisent dans le associé `_ATLTRY` .|
|[_ATLCATCHALL](#_atlcatchall)|Instruction (s) pour gérer les erreurs qui se produisent dans le associé `_ATLTRY` .|
|[_ATLTRY](#_atltry)|Marque une section de code protégée dans laquelle une erreur peut se produire.|

## <a name="requirements"></a>Conditions requises :

**En-tête :** atldef. h

## <a name="_atlcatch"></a><a name="_atlcatch"></a> _ATLCATCH

Instruction (s) pour gérer les erreurs qui se produisent dans le associé `_ATLTRY` .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Paramètres

*Envoyer*<br/>
Exception à intercepter.

### <a name="remarks"></a>Notes

Utilisée conjointement avec `_ATLTRY`. Résout en C++ [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pour gérer un type donné d’exceptions c++.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a> _ATLCATCHALL

Instruction (s) pour gérer les erreurs qui se produisent dans le associé `_ATLTRY` .

```
_ATLCATCHALL
```

### <a name="remarks"></a>Notes

Utilisée conjointement avec `_ATLTRY`. Résout en C++ [catch (...)](../../cpp/try-throw-and-catch-statements-cpp.md) pour gérer tous les types d’exceptions c++.

## <a name="_atltry"></a><a name="_atltry"></a> _ATLTRY

Marque une section de code protégée dans laquelle une erreur peut se produire.

```
_ATLTRY
```

### <a name="remarks"></a>Notes

Utilisé conjointement avec [_ATLCATCH](#_atlcatch) ou [_ATLCATCHALL](#_atlcatchall). Correspond au symbole C++ [try](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
