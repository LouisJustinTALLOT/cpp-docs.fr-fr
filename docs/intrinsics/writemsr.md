---
title: __writemsr
ms.date: 09/02/2019
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: 7819477edb8d4e6b18a1213a73ba67065ea7ff57
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219133"
---
# <a name="__writemsr"></a>__writemsr

**Section spécifique à Microsoft**

Génère l’instruction écrire dans le Registre spécifique`wrmsr`au modèle ().

## <a name="syntax"></a>Syntaxe

```C
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

### <a name="parameters"></a>Paramètres

*Annuler*\
dans Registre spécifique au modèle.

*Ajoutée*\
dans Valeur à écrire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writemsr`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette fonction ne peut être utilisée qu’en mode noyau, et cette routine est uniquement disponible en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
