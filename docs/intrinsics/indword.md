---
title: __indword
ms.date: 11/04/2016
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 063ebd92682f8011bc6b60eee14c3443bc04c333
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348924"
---
# <a name="indword"></a>__indword

**Section spécifique à Microsoft**

Lit des données d’un mot double du port spécifié à l’aide de la `in` instruction.

## <a name="syntax"></a>Syntaxe

```
unsigned long __indword(
   unsigned short Port
);
```

#### <a name="parameters"></a>Paramètres

*Port*<br/>
[in] Le port à lire.

## <a name="return-value"></a>Valeur de retour

Le mot lire à partir du port.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__indword`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)