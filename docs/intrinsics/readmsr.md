---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 029119bc47d0172c7e9cc5fbf8cd20c4ee23e0f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219649"
---
# <a name="__readmsr"></a>__readmsr

**Spécifique à Microsoft**

Génère l' `rdmsr` instruction, qui lit le Registre spécifique au modèle spécifié par **`register`** et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>Paramètres

*annuler*\
dans Registre spécifique au modèle à lire.

## <a name="return-value"></a>Valeur retournée

Valeur dans le registre spécifié.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette fonction est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

Pour plus d’informations, consultez la documentation AMD.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
