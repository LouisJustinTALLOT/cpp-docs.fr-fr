---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858046"
---
# <a name="__writeeflags"></a>__writeeflags

**Section spécifique de Microsoft**

Écrit la valeur spécifiée dans le registre d’État et de contrôle (EFLAGS) du programme.

## <a name="syntax"></a>Syntaxe

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Parameters

*Value*\
dans Valeur à écrire dans le registre EFLAGS. Le paramètre `Value` a une longueur de 32 bits pour une plateforme de 32 bits et une longueur de 64 bits pour une plateforme 64 bits.

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Fichier d’en-tête** \<Intro. h >

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
