---
title: __outdwordstring
ms.date: 11/04/2016
f1_keywords:
- __outdwordstring
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
ms.openlocfilehash: 51cb4a97d271d6d41d39d1025e3a5d34b273cdc4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035252"
---
# <a name="outdwordstring"></a>__outdwordstring

**Section spécifique à Microsoft**

Génère le `rep outsd` instruction, qui envoie `Count` mots doubles en commençant à `Buffer` le port d’e/s spécifié par `Port`.

## <a name="syntax"></a>Syntaxe

```
void __outdwordstring(
   unsigned short Port,
   unsigned long* Buffer,
   unsigned long Count
);
```

#### <a name="parameters"></a>Paramètres

*Port*<br/>
[in] Le port pour envoyer les données.

*Mémoire tampon*<br/>
[in] Un pointeur vers les données seront envoyés le port spécifié.

*Nombre*<br/>
[in] Le nombre de mots doubles à envoyer.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__outdwordstring`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)