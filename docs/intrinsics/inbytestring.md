---
title: __inbytestring
ms.date: 11/04/2016
f1_keywords:
- __inbytestring
- __inbytestring_cpp
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
ms.openlocfilehash: e515c6452d18ca022707fa2f9e36e2045523ccd5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038581"
---
# <a name="inbytestring"></a>__inbytestring

**Section spécifique à Microsoft**

Lit les données du port spécifié à l’aide de la `rep insb` instruction.

## <a name="syntax"></a>Syntaxe

```
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Paramètres

*Port*<br/>
[in] Le port à lire.

*Mémoire tampon*<br/>
[out] Les données lues à partir du port sont écrit ici.

*Nombre*<br/>
[in] Le nombre d’octets de données à lire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__inbytestring`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)