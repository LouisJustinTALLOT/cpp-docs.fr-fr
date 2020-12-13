---
description: 'En savoir plus sur : __readcr8'
title: __readcr8
ms.date: 09/02/2019
f1_keywords:
- __readcr8
helpviewer_keywords:
- __readcr8 intrinsic
ms.assetid: fce16953-87ff-4fbe-8081-7962b97ae46c
ms.openlocfilehash: 1961f00575956c8377131cd0871e59f79db5dc1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341020"
---
# <a name="__readcr8"></a>__readcr8

**Spécifique à Microsoft**

Lit le registre CR8 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readcr8(void);
```

## <a name="return-value"></a>Valeur de retour

Valeur dans le registre CR8.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readcr8`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
