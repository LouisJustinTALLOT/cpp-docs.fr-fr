---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: fbaf9e761f9f1450ccd12dc378ab6e498aa0df08
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857877"
---
# <a name="__readdr"></a>__readdr

**Section spécifique de Microsoft**

Lit la valeur du registre de débogage spécifié.

## <a name="syntax"></a>Syntaxe

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>Parameters

*DebugRegister*\
dans Constante comprise entre 0 et 7 qui identifie le registre de débogage.

## <a name="return-value"></a>Valeur de retour

Valeur du registre de débogage spécifié.

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Configuration requise pour

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readdr`|x86, x64|

**Fichier d’en-tête** \<Intro. h >

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
