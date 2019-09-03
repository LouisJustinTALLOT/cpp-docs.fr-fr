---
title: __indwordstring
ms.date: 09/02/2019
f1_keywords:
- __indwordstring
- __indwordstring_cpp
helpviewer_keywords:
- __indwordstring intrinsic
- rep insd instruction
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
ms.openlocfilehash: b0b160ba00b1c0b7aa6bffc913e4cb56d503c2ff
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217832"
---
# <a name="__indwordstring"></a>__indwordstring

**Section spécifique à Microsoft**

Lit les données à partir du port spécifié `rep insd` à l’aide de l’instruction.

## <a name="syntax"></a>Syntaxe

```C
void __indwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port à partir duquel effectuer la lecture.

*Mémoire tampon*\
à Les données lues à partir du port sont écrites ici.

*Saut*\
dans Nombre d’octets de données à lire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__indwordstring`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
