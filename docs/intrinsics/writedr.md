---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 715ef7432d506c2758c9c3da913e9c0ebb24e13f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219223"
---
# <a name="__writedr"></a>__writedr

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

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writedr`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
