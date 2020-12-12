---
description: 'En savoir plus sur : __writeeflags'
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 9c439194782f52b474ec6c6365705ebd8756c6b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331864"
---
# <a name="__writeeflags"></a>__writeeflags

**Spécifique à Microsoft**

Écrit la valeur spécifiée dans le registre d’État et de contrôle (EFLAGS) du programme.

## <a name="syntax"></a>Syntaxe

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Paramètres

*Value*\
dans Valeur à écrire dans le registre EFLAGS. Le `Value` paramètre a une longueur de 32 bits pour une plateforme 32 bits et une longueur de 64 bits pour une plateforme 64 bits.

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
