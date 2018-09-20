---
title: __outdword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outdword
dev_langs:
- C++
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7f7d5cf08ba83f83513f591ce04b1ff527cd491
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420567"
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

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)