---
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: c8df13c15b5cd8a51b77d65ad930a1852809ee30
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219235"
---
# <a name="__writecr8"></a>__writecr8

**Section spécifique à Microsoft**

Écrit la valeur `Data` dans le registre CR8.

## <a name="syntax"></a>Syntaxe

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Paramètres

*Métadonnée*\
dans Valeur à écrire dans le registre CR8.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writecr8`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L' `__writecr8` intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
