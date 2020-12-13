---
description: 'En savoir plus sur : __readeflags'
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: e74864f522ba411f44b4a264e9c0e1fd16aa84ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340994"
---
# <a name="__readeflags"></a>__readeflags

**Spécifique à Microsoft**

Lit le registre de l’état du programme et du contrôle (EFLAGS).

## <a name="syntax"></a>Syntaxe

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>Valeur de retour

Valeur du Registre EFLAGS. La valeur de retour est de 32 bits sur une plateforme de 32 bits et de 64 bits sur une plateforme de 64 bits.

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
