---
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3990d4b15c25cfd6c753c2b1d44c112971ff59af
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918799"
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

|Value|Description|
|-----------|-----------------|
|0|Échec : aucun nouveau gestionnaire n’est installé ou actif.|
|1|Réussite : le nouveau gestionnaire est installé et activé. L’allocation de mémoire peut être retentée.|

## <a name="exceptions"></a>Exceptions

Cette fonction génère [bad_alloc](../../standard-library/bad-alloc-class.md) si le *nouveau gestionnaire* est introuvable.

## <a name="remarks"></a>Notes 

Le *nouveau gestionnaire* est appelé si l’[opérateur new](../../cpp/new-operator-cpp.md) ne parvient pas à allouer de la mémoire. Le nouveau gestionnaire peut alors lancer une action appropriée, par exemple la libération de mémoire pour que les allocations suivantes aboutissent.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Voir aussi

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
