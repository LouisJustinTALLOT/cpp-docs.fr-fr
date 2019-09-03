---
title: __readcr8
ms.date: 09/02/2019
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: 525775fde4cb96cecfcabef878780d5a2aa6743a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221242"
---
# <a name="__readcr8"></a>__readcr8

**Section spécifique à Microsoft**

Lit le registre CR8 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>Valeur de retour

Valeur dans le registre CR8.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readcr8`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
