---
description: 'En savoir plus sur : __writemsr'
title: __writemsr
ms.date: 09/02/2019
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: 0ab7392d9df07a9083ca095bc7002a6bf7d45628
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331854"
---
# <a name="__writemsr"></a>__writemsr

**Spécifique à Microsoft**

Génère l’instruction écrire dans le Registre spécifique au modèle ( `wrmsr` ).

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

*Value*\
dans Valeur à écrire.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__writemsr`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette fonction ne peut être utilisée qu’en mode noyau, et cette routine est uniquement disponible en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
