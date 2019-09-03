---
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 6bd731951b440d3d2597d54c9a52d9f8640a5c5f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219835"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Section spécifique à Microsoft**

Définit l’indicateur d’interruption globale.

## <a name="syntax"></a>Syntaxe

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>Notes

La fonction `__svm_stgi` est équivalente à l’instruction machine `STGI` . L’indicateur d’interruption globale détermine si le microprocesseur ignore, ajourne ou gère les interruptions, en raison d’événements tels qu’une exécution d’e/s, une alerte de température matérielle ou une exception de débogage.

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez «volume manuel du programmeur d’architecture AMD64 2: Programmation système», sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
