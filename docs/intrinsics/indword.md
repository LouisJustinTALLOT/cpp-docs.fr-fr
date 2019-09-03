---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222121"
---
# <a name="__indword"></a>__indword

**Section spécifique à Microsoft**

Lit un mot double de données à partir du port spécifié à `in` l’aide de l’instruction.

## <a name="syntax"></a>Syntaxe

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port à partir duquel effectuer la lecture.

## <a name="return-value"></a>Valeur de retour

Mot lu à partir du port.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__indword`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
