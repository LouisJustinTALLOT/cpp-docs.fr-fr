---
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 740c76e5dcc8f94b9257272624a6ad3c1f9726c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219969"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Section spécifique à Microsoft**

Efface l’indicateur d’interruption globale.

## <a name="syntax"></a>Syntaxe

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>Notes

La fonction `__svm_clgi` est équivalente à l’instruction machine `CLGI` . L’indicateur d’interruption globale détermine si le microprocesseur ignore, ajourne ou gère les interruptions, en raison d’événements tels qu’une exécution d’e/s, une alerte de température matérielle ou une exception de débogage.

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez «volume manuel du programmeur d’architecture AMD64 2: Programmation système», sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_clgi`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)
