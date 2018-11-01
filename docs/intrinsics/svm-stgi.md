---
title: __svm_stgi
ms.date: 11/04/2016
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 9f7e35bbecf4051e4a47c32753b3a221dd2a4cc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494664"
---
# <a name="svmstgi"></a>__svm_stgi

**Section spécifique à Microsoft**

Définit l’indicateur d’interruption global.

## <a name="syntax"></a>Syntaxe

```
void __svm_stgi(void);
```

## <a name="remarks"></a>Notes

La fonction `__svm_stgi` est équivalente à l’instruction machine `STGI` . L’indicateur d’interruption global détermine si le microprocesseur ignore, diffère ou gère les interruptions dues à des événements comme un achèvement d’e/s, une alerte de température de matériel ou une exception de débogage.

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « 24593, révision 3.11, de numéro de document sur le [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_clgi](../intrinsics/svm-clgi.md)