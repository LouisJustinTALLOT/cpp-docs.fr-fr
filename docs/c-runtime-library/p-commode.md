---
description: 'En savoir plus sur : __p__commode'
title: __p__commode
ms.date: 4/2/2020
api_name:
- __p__commode
- _o___p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: f3f779196b650d05bb16c0da652d47946fc2a10d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213622"
---
# <a name="__p__commode"></a>__p__commode

Pointe vers la variable globale `_commode`, qui spécifie le *mode de validation de fichiers* par défaut pour les opérations d’E/S de fichier.

## <a name="syntax"></a>Syntaxe

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers la variable globale `_commode`.

## <a name="remarks"></a>Notes

La fonction `__p__commode` est exclusivement réservée à un usage interne et ne doit pas être appelée à partir du code utilisateur.

Le mode de validation de fichiers spécifie quand les données critiques sont écrites sur le disque. Pour plus d’informations, consultez [fflush](../c-runtime-library/reference/fflush.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__p\__commode|internal.h|
