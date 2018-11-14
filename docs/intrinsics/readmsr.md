---
title: __readmsr
ms.date: 11/04/2016
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 891ca43af4a81b63de39d367ea418e43811f78d0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326405"
---
# <a name="readmsr"></a>__readmsr

**Section spécifique à Microsoft**

Génère le `rdmsr` instruction, qui lit le Registre spécifiques au modèle spécifié par `register` et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```
__int64 __readmsr(
   int register
);
```

#### <a name="parameters"></a>Paramètres

*register*<br/>
[in] Le modèle spécifique s’inscrire à lire.

## <a name="return-value"></a>Valeur de retour

La valeur dans le Registre spécifié.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette fonction est uniquement disponible en mode noyau, et la routine est uniquement disponible comme intrinsèque.

Pour plus d’informations, consultez la documentation AMD.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)