---
title: __svm_stgi
ms.date: 11/04/2016
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: ea138f17a24af21afa937991f77bd1e2a689c3f7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024788"
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

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : Système de programmation, » document nombre 24593, révision 3.11, sur le [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_clgi](../intrinsics/svm-clgi.md)