---
title: __writecr0
ms.date: 11/04/2016
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 8e36aa1c1e7299c1de5cba26acb8a4ae8165ad6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547145"
---
# <a name="writecr0"></a>__writecr0

**Section spécifique à Microsoft**

Écrit la valeur `Data` pour le registre CR0.

## <a name="syntax"></a>Syntaxe

```
void writecr0( 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>Paramètres

*Données*<br/>
[in] La valeur à écrire dans le registre CR0.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writecr0`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)