---
title: __indwordstring
ms.date: 11/04/2016
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: 6f50aed8e6efe3b0b0a6e7eaebef5719475463ea
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027868"
---
# <a name="indwordstring"></a>__indwordstring

**Section spécifique à Microsoft**

Lit les données du port spécifié à l’aide de la `rep insd` instruction.

## <a name="syntax"></a>Syntaxe

```
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
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
|`__indwordstring`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)