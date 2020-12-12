---
description: 'En savoir plus sur : __outbytestring'
title: __outbytestring
ms.date: 09/02/2019
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: feadb0b4275e370de88bfc04c8a10f90c41d0844
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222422"
---
# <a name="__outbytestring"></a>__outbytestring

**Spécifique à Microsoft**

Génère l' `rep outsb` instruction, qui envoie les premiers `Count` octets de données pointés par `Buffer` vers le port spécifié par `Port` .

## <a name="syntax"></a>Syntaxe

```C
void __outbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port auquel envoyer les données.

*Mémoire tampon*\
dans Données à envoyer sur le port spécifié.

*Saut*\
dans Nombre d’octets de données à envoyer.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
