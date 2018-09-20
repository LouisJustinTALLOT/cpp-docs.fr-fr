---
title: __readmsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readmsr
dev_langs:
- C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d21d33d1e90d7c4aac9ea833d0c5bd80f5172312
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416602"
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