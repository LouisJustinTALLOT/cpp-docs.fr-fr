---
title: __readcr0 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr0
dev_langs:
- C++
helpviewer_keywords:
- __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f989c7bd6cc74a688e8694ed59899c59c50cb0d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430655"
---
# <a name="readcr0"></a>__readcr0

**Section spécifique à Microsoft**

Lit le registre CR0 et renvoie sa valeur.

## <a name="syntax"></a>Syntaxe

```
unsigned long __readcr0(void);  /* X86 */
unsigned __int64 __readcr0(void);  /* X64 */

```

## <a name="return-value"></a>Valeur de retour

Valeur contenue dans le registre CR0.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readcr0`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)