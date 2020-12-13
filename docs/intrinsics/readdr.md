---
description: 'En savoir plus sur : __readdr'
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: b3b5952d940db91b278344ab45edb3e8b914c094
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341007"
---
# <a name="__readdr"></a>__readdr

**Spécifique à Microsoft**

Lit la valeur du registre de débogage spécifié.

## <a name="syntax"></a>Syntaxe

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>Paramètres

*DebugRegister*\
dans Constante comprise entre 0 et 7 qui identifie le registre de débogage.

## <a name="return-value"></a>Valeur retournée

Valeur du registre de débogage spécifié.

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readdr`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
