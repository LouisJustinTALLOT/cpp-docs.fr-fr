---
title: __writecr3
ms.date: 09/02/2019
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: f2472a21fe42f10dbf0918480ef02f7e48109747
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219278"
---
# <a name="__writecr3"></a>__writecr3

**Section spécifique à Microsoft**

Écrit la valeur `Data` dans le registre Cr3.

## <a name="syntax"></a>Syntaxe

```C
void writecr3(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Paramètres

*Métadonnée*\
dans Valeur à écrire dans le registre CR3.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writecr3`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Cette intrinsèque est disponible uniquement en mode noyau et la routine est disponible uniquement comme intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
