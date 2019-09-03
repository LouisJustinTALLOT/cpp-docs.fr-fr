---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221034"
---
# <a name="__readpmc"></a>__readpmc

**Section spécifique à Microsoft**

Génère l' `rdpmc` instruction, qui lit le compteur d’analyse des performances spécifié par *Counter*.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>Paramètres

*)* \
dans Compteur de performance à lire.

## <a name="return-value"></a>Valeur de retour

Valeur du compteur de performances spécifié.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau, et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
