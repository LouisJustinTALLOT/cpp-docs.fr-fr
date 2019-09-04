---
title: __inwordstring
ms.date: 09/02/2019
f1_keywords:
- __inwordstring
- __inwordstring_cpp
helpviewer_keywords:
- __inwordstring intrinsic
- rep insw instruction
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
ms.openlocfilehash: a6f67e15bc5eef9fbe9cc8d12e95afcdf869e3b1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221881"
---
# <a name="__inwordstring"></a>__inwordstring

**Section spécifique à Microsoft**

Lit les données à partir du port spécifié `rep insw` à l’aide de l’instruction.

## <a name="syntax"></a>Syntaxe

```C
void __inwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port à partir duquel effectuer la lecture.

*Mémoire tampon*\
à Les données lues à partir du port sont écrites ici.

*Saut*\
dans Nombre de mots de données à lire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__inwordstring`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
