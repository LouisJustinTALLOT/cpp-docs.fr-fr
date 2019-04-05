---
title: __readcr2
ms.date: 11/04/2016
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: e26ccbb3db1dfc113f84210314379b06dae93542
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031100"
---
# <a name="readcr2"></a>__readcr2

**Section spécifique à Microsoft**

Lit le Registre CR2 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>Valeur de retour

La valeur dans le Registre CR2.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readcr2`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)