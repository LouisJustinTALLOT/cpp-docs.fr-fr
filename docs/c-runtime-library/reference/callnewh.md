---
title: _callnewh | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40d8f621b7098618b9be3872620d5294013fbe3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393090"
---
# <a name="callnewh"></a>_callnewh

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

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>Voir aussi

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
