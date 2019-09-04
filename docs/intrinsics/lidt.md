---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217507"
---
# <a name="__lidt"></a>__lidt

**Section spécifique à Microsoft**

Charge le registre de la table du descripteur d’interruption (IDTR) avec la valeur dans l’emplacement de mémoire spécifié.

## <a name="syntax"></a>Syntaxe

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Source*|dans Pointeur vers la valeur à copier dans IDTR.|

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__lidt`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

La `__lidt` fonction est équivalente à `LIDT` l’instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document «Guide du développeur de logiciels d’architecture Intel, volume 2: Référence du jeu d’instructions, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
