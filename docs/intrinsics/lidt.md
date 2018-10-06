---
title: __lidt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f07f4aee87df98b93c5aca54d1435339bf546539
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820657"
---
# <a name="lidt"></a>__lidt

**Section spécifique à Microsoft**

Charge le Registre des interruptions table descripteur (IDTR) avec la valeur dans l’emplacement de mémoire spécifié.

## <a name="syntax"></a>Syntaxe

```
void __lidt(void * Source);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Source*|[in] Pointeur vers la valeur à copier vers le IDTR.|

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__lidt`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Le `__lidt` fonction est équivalente à la `LIDT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez dans le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : référence de jeu d’instructions, » à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)