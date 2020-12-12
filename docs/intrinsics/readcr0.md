---
description: 'En savoir plus sur : __readcr0'
title: __readcr0
ms.date: 09/02/2019
f1_keywords:
- __readcr0
helpviewer_keywords:
- __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
ms.openlocfilehash: b8a7b98042e5e5dbff5236c27b97d8378d72ed6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257405"
---
# <a name="__readcr0"></a>__readcr0

**Spécifique à Microsoft**

Lit le registre CR0 et renvoie sa valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned long __readcr0(void);  /* X86 */
unsigned __int64 __readcr0(void);  /* X64 */
```

## <a name="return-value"></a>Valeur de retour

Valeur contenue dans le registre CR0.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr0`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
