---
title: __outdword
ms.date: 11/04/2016
f1_keywords:
- __outdword
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
ms.openlocfilehash: 236c4812f62cb092876b400051248425ee1b13e7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034221"
---
# <a name="outdword"></a>__outdword

**Section spécifique à Microsoft**

Génère le `out` instruction pour envoyer un mot double `Data` le port de sortie `Port`.

## <a name="syntax"></a>Syntaxe

```
void __outdword(
   unsigned short Port,
   unsigned long Data
);
```

#### <a name="parameters"></a>Paramètres

*Port*<br/>
[in] Le port pour envoyer les données.

*Données*<br/>
[in] Le mot double à envoyer.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__outdword`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)