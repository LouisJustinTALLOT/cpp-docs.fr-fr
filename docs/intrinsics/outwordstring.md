---
description: 'En savoir plus sur : __outwordstring'
title: __outwordstring
ms.date: 09/02/2019
f1_keywords:
- __outwordstring
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
ms.openlocfilehash: c0dba174776c7606a0f9ed11ac172331a6a8f350
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257535"
---
# <a name="__outwordstring"></a>__outwordstring

**Spécifique à Microsoft**

Génère l' `rep outsw` instruction, qui envoie des mots de *nombre* commençant à la *mémoire tampon* en dehors du port d’e/s spécifié par le *port*.

## <a name="syntax"></a>Syntaxe

```C
void __outwordstring(
   unsigned short Port,
   unsigned short* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port auquel envoyer les données.

*Mémoire tampon*\
dans Pointeur vers les données à envoyer vers le port spécifié.

*Saut*\
dans Nombre de mots à envoyer.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__outwordstring`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
