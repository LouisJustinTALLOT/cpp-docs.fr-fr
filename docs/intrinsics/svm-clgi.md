---
description: 'En savoir plus sur : __svm_clgi'
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: d0b372e28b0b119d3576dd87b34f1edf883f1337
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336863"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Spécifique à Microsoft**

Efface l’indicateur d’interruption globale.

## <a name="syntax"></a>Syntaxe

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>Notes

La fonction `__svm_clgi` est équivalente à l’instruction machine `CLGI` . L’indicateur d’interruption globale détermine si le microprocesseur ignore, ajourne ou gère les interruptions, en raison d’événements tels qu’une exécution d’e/s, une alerte de température matérielle ou une exception de débogage.

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez « Configuration manuelle du volume 2 : programmation du système par le programmeur d’architecture AMD64 » sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_clgi`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)
