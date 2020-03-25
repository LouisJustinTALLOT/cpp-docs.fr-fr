---
title: __p__fmode
ms.date: 11/04/2016
api_name:
- __p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: 2364a22d52c5bc418e4499a4a639c8e06559063a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171448"
---
# <a name="__p__fmode"></a>__p__fmode

Pointe vers la variable globale `_fmode`, qui spécifie le *mode de traduction de fichiers* par défaut pour les opérations d’E/S de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers la variable globale `_fmode`.

## <a name="remarks"></a>Notes

La fonction `__p__fmode` est réservé exclusivement à un usage interne et ne doit pas être appelée à partir du code utilisateur.

Le mode de traduction de fichiers spécifie une traduction `binary` ou `text` pour les opérations d’E/S [_open](../c-runtime-library/reference/open-wopen.md) et [_pipe](../c-runtime-library/reference/pipe.md). Pour plus d’informations, consultez [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
