---
description: 'En savoir plus sur : __writecr8'
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: b9c642d92cd5d5cfb861dbff3d159b5c98a1aa5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331889"
---
# <a name="__writecr8"></a>__writecr8

**Spécifique à Microsoft**

Écrit la valeur `Data` dans le registre CR8.

## <a name="syntax"></a>Syntaxe

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Paramètres

*Données*\
dans Valeur à écrire dans le registre CR8.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__writecr8`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L' `__writecr8` intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
