---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: e43789d2fbed1bdc52665531c61c6c932a27f5ab
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219143"
---
# <a name="__writeeflags"></a>__writeeflags

Écrit la valeur spécifiée dans le registre d’État et de contrôle (EFLAGS) du programme.

## <a name="syntax"></a>Syntaxe

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Paramètres

*Ajoutée*\
dans Valeur à écrire dans le registre EFLAGS. Le `Value` paramètre a une longueur de 32 bits pour une plateforme 32 bits et une longueur de 64 bits pour une plateforme 64 bits.

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
