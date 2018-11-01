---
title: __svm_invlpga
ms.date: 11/04/2016
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: 2d356cf7426c558c8ac0312eff02c0cb9de9c859
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544298"
---
# <a name="svminvlpga"></a>__svm_invlpga

**Section spécifique à Microsoft**

Invalide l’entrée de mappage d’adresse dans la mémoire tampon de l’ordinateur traduction ITLB. Les paramètres spécifient l’adresse virtuelle et l’identificateur d’espace d’adresse de la page à invalider.

## <a name="syntax"></a>Syntaxe

```
void __svm_invlpga(void *Va, int ASID);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Évaluation des vulnérabilités*|[in] L’adresse virtuelle de la page à invalider.|
|*ASID*|[in] L’identificateur d’espace adresse (ASID) de la page à invalider.|

## <a name="remarks"></a>Notes

La fonction `__svm_invlpga` est équivalente à l’instruction machine `INVLPGA` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « 24593, révision 3.11, de numéro de document sur le [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_invlpga`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)