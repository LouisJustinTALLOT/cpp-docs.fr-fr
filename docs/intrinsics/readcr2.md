---
description: 'En savoir plus sur : __readcr2'
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: dd862f88716fd2d385622c5100f91fdf47061543
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257353"
---
# <a name="__readcr2"></a>__readcr2

**Spécifique à Microsoft**

Lit le registre CR2 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>Valeur de retour

Valeur dans le registre CR2.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr2`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
