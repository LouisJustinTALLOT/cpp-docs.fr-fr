---
description: 'En savoir plus sur : __wbinvd'
title: __wbinvd
ms.date: 09/02/2019
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: b40e1b618e49ab317a7b9cdeea647bcd58df7912
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257262"
---
# <a name="__wbinvd"></a>__wbinvd

**Spécifique à Microsoft**

Génère l’instruction d’écriture différée et de cache ( `wbinvd` ).

## <a name="syntax"></a>Syntaxe

```C
void __wbinvd(void);
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__wbinvd`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette fonction est disponible uniquement en mode noyau avec un niveau de privilège (CPL) égal à 0, et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
