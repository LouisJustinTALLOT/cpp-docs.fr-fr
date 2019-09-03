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
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222339"
---
# <a name="__readmsr"></a>__readmsr

**Section spécifique à Microsoft**

Génère l' `rdmsr` instruction, qui lit le Registre spécifique au modèle spécifié par `register` et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>Paramètres

*annuler*\
dans Registre spécifique au modèle à lire.

## <a name="return-value"></a>Valeur de retour

Valeur dans le registre spécifié.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette fonction est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

Pour plus d’informations, consultez la documentation AMD.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
