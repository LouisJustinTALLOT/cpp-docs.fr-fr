---
title: __inwordstring
ms.date: 11/04/2016
f1_keywords:
- __inwordstring
- __inwordstring_cpp
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
ms.openlocfilehash: 52c36754e1eea56b84eeb494e82e37a5b043246e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030217"
---
# <a name="inwordstring"></a>__inwordstring

**Section spécifique à Microsoft**

Lit les données du port spécifié à l’aide de la `rep insw` instruction.

## <a name="syntax"></a>Syntaxe

```
void __inwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Paramètres

*Port*<br/>
[in] Le port à lire.

*Mémoire tampon*<br/>
[out] Les données lues à partir du port sont écrit ici.

*Nombre*<br/>
[in] Le nombre de mots de données à lire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__inwordstring`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)