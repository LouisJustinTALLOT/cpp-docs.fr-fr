---
title: __readcr4
ms.date: 11/04/2016
f1_keywords:
- __readcr4
helpviewer_keywords:
- __readcr4 intrinsic
ms.assetid: b841a27b-fe0d-4ee9-b76b-f91d3eb061fa
ms.openlocfilehash: b67016846768be778881c02b395c8d6f3af1ef3f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037215"
---
# <a name="readcr4"></a>__readcr4

**Section spécifique à Microsoft**

Lit le Registre CR4 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __readcr4(void);
```

## <a name="return-value"></a>Valeur de retour

La valeur du Registre CR4.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readcr4`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)