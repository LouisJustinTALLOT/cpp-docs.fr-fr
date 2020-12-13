---
description: 'En savoir plus sur : __readcr4'
title: __readcr4
ms.date: 09/02/2019
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: 3e1d3999f488d4b7c155fd2c475a2070f29f6cda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341033"
---
# <a name="__readcr4"></a>__readcr4

**Spécifique à Microsoft**

Lit le registre CR4 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>Valeur de retour

Valeur dans le registre CR4.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr4`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
