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
ms.openlocfilehash: 2c866213c452f3b8791bf0fe031a43bb024e91fb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027625"
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

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)