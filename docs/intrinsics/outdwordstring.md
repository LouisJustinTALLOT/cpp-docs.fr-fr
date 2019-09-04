---
title: __outdwordstring
ms.date: 09/02/2019
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 50908a65795af617f18a497c073cfefe009dfd80
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217162"
---
# <a name="__outdwordstring"></a>__outdwordstring

**Section spécifique à Microsoft**

Génère l' `rep outsd` instruction, qui envoie `Count` des mots doubles `Buffer` à partir du port d’e/s `Port`spécifié par.

## <a name="syntax"></a>Syntaxe

```C
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port auquel envoyer les données.

*Mémoire tampon*\
dans Pointeur vers les données à envoyer vers le port spécifié.

*Saut*\
dans Nombre de mots doubles à envoyer.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__outdwordstring`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
