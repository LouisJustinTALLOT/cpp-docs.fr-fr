---
title: _callnewh
ms.date: 11/04/2016
api_name:
- _callnewh
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3e14450538807b164897c335f7e37d82d8562314
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939378"
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
