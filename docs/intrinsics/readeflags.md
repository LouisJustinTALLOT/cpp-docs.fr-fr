---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 6afdc0f20a3ae72865a80ba2eb7f896f79f63171
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857903"
---
# <a name="__readeflags"></a>__readeflags

**Section spécifique de Microsoft**

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

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readeflags`|x86, x64|

**Fichier d’en-tête** \<Intro. h >

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
