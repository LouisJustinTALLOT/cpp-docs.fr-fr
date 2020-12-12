---
description: 'En savoir plus sur : __writedr'
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 3a52b8985a28268c430cbb1bfb7b2494e9004820
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331878"
---
# <a name="__writedr"></a>__writedr

**Spécifique à Microsoft**

Écrit la valeur spécifiée dans le registre de débogage spécifié.

## <a name="syntax"></a>Syntaxe

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>Paramètres

*DebugRegister*\
dans Nombre compris entre 0 et 7 qui identifie le registre de débogage.

*DebugValue*\
dans Valeur à écrire dans le registre de débogage.

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__writedr`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
