---
title: __max
ms.date: 04/05/2018
apiname:
- __max
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 32e1207ea4bb030ac5303de32c0566f98e0596a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156862"
---
# <a name="max"></a>__max

Macro de préprocesseur qui retourne le plus grand de deux valeurs.

## <a name="syntax"></a>Syntaxe

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Paramètres

*a*, *b*<br/>
Valeurs de tout type numérique à comparer.

## <a name="return-value"></a>Valeur de retour

**__max** retourne le plus grand de ses arguments.

## <a name="remarks"></a>Notes

Le **__max** macro compare deux valeurs et retourne la valeur la plus grande. Les arguments peuvent être de n’importe quel type de données numérique, signé ou non signé. Les deux arguments et la valeur de retour doivent être du même type de données.

L’argument retourné est évaluée deux fois par la macro. Cela peut entraîner des résultats inattendus si l’argument est une expression qui modifie sa valeur lorsqu’elle est évaluée, tel que `*p++`.

## <a name="requirements"></a>Configuration requise

|Macro|En-tête requis|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Exemple

Pour plus d’informations, consultez l’exemple pour [__min](min.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>