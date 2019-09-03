---
title: __outbytestring
ms.date: 09/02/2019
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 31caf17db5d56efccd6b30200994b1080356b4c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217171"
---
# <a name="__outbytestring"></a>__outbytestring

**Section spécifique à Microsoft**

Génère l' `rep outsb` instruction, qui envoie les premiers `Count` octets de données pointés par `Buffer` vers le port spécifié par `Port`.

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

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
