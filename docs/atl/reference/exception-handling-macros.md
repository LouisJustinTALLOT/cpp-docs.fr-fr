---
title: Macros de manutention d’exception
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330088"
---
# <a name="exception-handling-macros"></a>Macros de manutention d’exception

Ces macros fournissent un soutien pour la gestion des exceptions.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Énoncé pour traiter les erreurs qui `_ATLTRY`se produisent dans le .|
|[_ATLCATCHALL](#_atlcatchall)|Énoncé pour traiter les erreurs qui `_ATLTRY`se produisent dans le .|
|[_ATLTRY](#_atltry)|Marque une section de code gardée où une erreur pourrait se produire.|

## <a name="requirements"></a>Conditions requises :

**En-tête:** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

Énoncé pour traiter les erreurs qui `_ATLTRY`se produisent dans le .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Paramètres

*E*<br/>
L’exception à attraper.

### <a name="remarks"></a>Notes

Utilisée conjointement avec `_ATLTRY`. Résout à la capture CMD [(CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) pour le traitement d’un type donné d’exceptions C.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

Énoncé pour traiter les erreurs qui `_ATLTRY`se produisent dans le .

```
_ATLCATCHALL
```

### <a name="remarks"></a>Notes

Utilisée conjointement avec `_ATLTRY`. Résout à la prise de C [(...)](../../cpp/try-throw-and-catch-statements-cpp.md) pour la manipulation de tous les types d’exceptions C.

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

Marque une section de code gardée où une erreur pourrait se produire.

```
_ATLTRY
```

### <a name="remarks"></a>Notes

Utilisé en conjonction avec [_ATLCATCH](#_atlcatch) ou [_ATLCATCHALL](#_atlcatchall). Résout au symbole CMD [essayer](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
