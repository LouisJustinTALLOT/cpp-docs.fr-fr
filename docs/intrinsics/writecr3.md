---
title: __writecr3
ms.date: 11/04/2016
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: 88467e4fb39abc9526e47a73f998d630470111a9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037365"
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

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)