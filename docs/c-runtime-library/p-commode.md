---
title: __p__commode
ms.date: 11/04/2016
api_name:
- __p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: 930eb45e8069bdd71b5a7986e229b229318d0be8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944114"
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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__p\__commode|internal.h|