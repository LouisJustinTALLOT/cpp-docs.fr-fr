---
title: _callnewh
ms.date: 11/04/2016
apiname:
- _callnewh
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 98526f6c8c40b71104345563db71ef098b6cfb8d
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739819"
---
# <a name="_callnewh"></a>_callnewh

Appelle le *nouveau gestionnaire* installé.

## <a name="syntax"></a>Syntaxe

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Quantité de mémoire que l’[opérateur new](../../cpp/new-operator-cpp.md) a essayé d’allouer.

## <a name="return-value"></a>Valeur de retour

|Valeur|Description|
|-----------|-----------------|
|0|Toute Aucun nouveau gestionnaire n’est installé ou aucun nouveau gestionnaire n’est actif.|
|1|Fructueux Le nouveau gestionnaire est installé et actif. L’allocation de mémoire peut être retentée.|

## <a name="exceptions"></a>Exceptions

Cette fonction génère [bad_alloc](../../standard-library/bad-alloc-class.md) si le *nouveau gestionnaire* est introuvable.

## <a name="remarks"></a>Notes

Le *nouveau gestionnaire* est appelé si l’[opérateur new](../../cpp/new-operator-cpp.md) ne parvient pas à allouer de la mémoire. Le nouveau gestionnaire peut alors lancer une action appropriée, par exemple la libération de mémoire pour que les allocations suivantes aboutissent.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Voir aussi

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
