---
title: __outdword
ms.date: 09/02/2019
f1_keywords:
- __outdword
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
ms.openlocfilehash: ce1358e7cef0136ccf7d314038d06d271916e0bc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221656"
---
# <a name="__outdword"></a>__outdword

**Section spécifique à Microsoft**

Génère l' `out` instruction pour envoyer des *données* de mot double vers le *port*du port.

## <a name="syntax"></a>Syntaxe

```C
void __outdword(
   unsigned short Port,
   unsigned long Data
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port auquel envoyer les données.

*Métadonnée*\
dans Mot double à envoyer.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__outdword`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
