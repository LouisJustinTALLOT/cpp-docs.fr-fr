---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 473e7223e9974d0125e772c152ea85ae90b97342
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858059"
---
# <a name="__writedr"></a>__writedr

**Section spécifique de Microsoft**

Écrit la valeur spécifiée dans le registre de débogage spécifié.

## <a name="syntax"></a>Syntaxe

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>Parameters

*DebugRegister*\
dans Nombre compris entre 0 et 7 qui identifie le registre de débogage.

*DebugValue*\
dans Valeur à écrire dans le registre de débogage.

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writedr`|x86, x64|

**Fichier d’en-tête** \<Intro. h >

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
