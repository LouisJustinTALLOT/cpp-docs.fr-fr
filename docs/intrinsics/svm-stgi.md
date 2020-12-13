---
description: 'En savoir plus sur : __svm_stgi'
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 8a6c7c221ed0bbf71a00685e8a0545818dd507a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336844"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Spécifique à Microsoft**

Définit l’indicateur d’interruption globale.

## <a name="syntax"></a>Syntaxe

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>Notes

La fonction `__svm_stgi` est équivalente à l’instruction machine `STGI` . L’indicateur d’interruption globale détermine si le microprocesseur ignore, ajourne ou gère les interruptions, en raison d’événements tels qu’une exécution d’e/s, une alerte de température matérielle ou une exception de débogage.

Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez « Configuration manuelle du volume 2 : programmation du système par le programmeur d’architecture AMD64 » sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
