---
title: __readcr3
ms.date: 09/02/2019
f1_keywords:
- __readcr3
helpviewer_keywords:
- __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
ms.openlocfilehash: b03ff46fabc99839d9c0bbd5c72e1b76d25814c0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221267"
---
# <a name="__readcr3"></a>__readcr3

**Section spécifique à Microsoft**

Lit le registre CR3 et retourne sa valeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readcr3(void);
```

## <a name="return-value"></a>Valeur de retour

Valeur dans le registre CR3.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readcr3`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque est disponible uniquement en mode noyau et la routine n’est disponible qu’en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
