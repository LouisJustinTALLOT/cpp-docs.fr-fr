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
ms.openlocfilehash: 6f7676fc5c9958be3d0567e6bf22a11367094150
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939987"
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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__p\__fmode|stdlib.h|