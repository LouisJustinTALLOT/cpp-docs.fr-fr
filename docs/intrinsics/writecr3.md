---
title: __writecr3
ms.date: 11/04/2016
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: 2046e3b2014bd17e74e880e8dbd0fcdc0a65021c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592557"
---
# <a name="writecr3"></a>__writecr3

**Section spécifique à Microsoft**

Écrit la valeur `Data` au CR3 s’inscrivent.

## <a name="syntax"></a>Syntaxe

```
void writecr3( 
   unsigned __int64 Data 
);
```

#### <a name="parameters"></a>Paramètres

*Données*<br/>
[in] La valeur à écrire dans le Registre CR3.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writecr3`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)