---
title: __p__fmode
ms.date: 4/2/2020
api_name:
- __p__fmode
- _o___p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: dfd9962c49b03dbb30223d1d7403b791ed6dbec9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919874"
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

La fonction `__p__fmode` est exclusivement réservée à un usage interne et ne doit pas être appelée à partir du code utilisateur.

Le mode de traduction de fichiers spécifie une traduction `binary` ou `text` pour les opérations d’E/S [_open](../c-runtime-library/reference/open-wopen.md) et [_pipe](../c-runtime-library/reference/pipe.md). Pour plus d’informations, consultez [_fmode](../c-runtime-library/fmode.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
