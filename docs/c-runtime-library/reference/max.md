---
title: __max
ms.date: 04/05/2018
api_name:
- __max
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 4cdfd99ec344cd357900d76dfc7f9400046e448a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170187"
---
# <a name="__max"></a>__max

Macro de préprocesseur qui retourne la plus grande de deux valeurs.

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

La macro **__max** compare deux valeurs et retourne la valeur de la plus grande. Les arguments peuvent être de n’importe quel type de données numérique, signé ou non signé. Les deux arguments et la valeur de retour doivent être du même type de données.

L’argument retourné est évalué deux fois par la macro. Cela peut provoquer des résultats inattendus si l’argument est une expression qui modifie sa valeur lors de son évaluation, par exemple `*p++`.

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Exemple

Pour plus d’informations, consultez l’exemple pour [__min](min.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>
