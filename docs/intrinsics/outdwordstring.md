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
ms.openlocfilehash: d94db2f59f9a3a8074331054b04cef59cebac0dd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502594"
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

*mémoire tampon*<br/>
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

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)