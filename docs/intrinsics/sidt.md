---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222327"
---
# <a name="__sidt"></a>__sidt

**Section spécifique à Microsoft**

Stocke la valeur du registre de la table du descripteur d’interruption (IDTR) dans l’emplacement de mémoire spécifié.

## <a name="syntax"></a>Syntaxe

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>Paramètres

*Destination*\
dans Pointeur vers l’emplacement de mémoire où le IDTR est stocké.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__sidt`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

La fonction `__sidt` est équivalente à l’instruction machine `SIDT` . Pour plus d’informations, recherchez le document «Guide du développeur de logiciels d’architecture Intel, volume 2: Référence du jeu d’instructions, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
