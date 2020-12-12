---
description: 'En savoir plus sur : __readmsr'
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 1a8acae272a450cb4470744e434277576cc8b9c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271913"
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
