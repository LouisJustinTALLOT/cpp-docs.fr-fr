---
description: 'En savoir plus sur : __outword'
title: __outword
ms.date: 09/02/2019
f1_keywords:
- __outword
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
ms.openlocfilehash: 07136a5ae293f7e23a1cf6b0baa2b3a0f0cc54d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257574"
---
# <a name="__outword"></a>__outword

**Spécifique à Microsoft**

Génère l' `out` instruction, qui envoie le mot *Data* out au port d’e/s spécifié par le *port*.

## <a name="syntax"></a>Syntaxe

```C
void __outword(
   unsigned short Port,
   unsigned short Data
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port auquel envoyer les données.

*Données*\
dans Données à envoyer.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__outword`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
