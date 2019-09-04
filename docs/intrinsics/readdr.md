---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: 646330ca92af08903485fd4583eb2c217fe3e023
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216677"
---
# <a name="__readdr"></a>__readdr

Lit la valeur du registre de débogage spécifié.

## <a name="syntax"></a>Syntaxe

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>Paramètres

*DebugRegister*\
dans Constante comprise entre 0 et 7 qui identifie le registre de débogage.

## <a name="return-value"></a>Valeur de retour

Valeur du registre de débogage spécifié.

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau, et les routines sont disponibles uniquement comme intrinsèques.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readdr`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
