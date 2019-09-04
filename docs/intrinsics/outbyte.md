---
title: __outbyte
ms.date: 09/02/2019
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: 18792010c45ffb648e9555ccb73f8614c3e3e6ea
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217197"
---
# <a name="__outbyte"></a>__outbyte

**Section spécifique à Microsoft**

Génère l' `out` instruction, qui envoie 1 octet spécifié par `Data` le port d’e/s spécifié par `Port`.

## <a name="syntax"></a>Syntaxe

```C
void __outbyte(
   unsigned short Port,
   unsigned char Data
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port auquel envoyer les données.

*Métadonnée*\
dans Octet à envoyer sur le port spécifié.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__outbyte`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
