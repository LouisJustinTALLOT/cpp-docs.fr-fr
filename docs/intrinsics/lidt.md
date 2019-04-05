---
title: __lidt
ms.date: 11/04/2016
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 757309603af48820a17668cfe272bbeaad9239b3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038471"
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

Le `__lidt` fonction est équivalente à la `LIDT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez dans le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : Instruction Set Reference, » à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__sidt](../intrinsics/sidt.md)