---
title: __max | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d223f4288ccf40646e8f560cec7243b7e8f9f649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398417"
---
# <a name="max"></a>__max

Une macro de préprocesseur qui retourne le plus grand des deux valeurs.

## <a name="syntax"></a>Syntaxe

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Paramètres

*un*, *b*<br/>
Valeurs de tout type numérique à comparer.

## <a name="return-value"></a>Valeur de retour

**__max** retourne le plus grand de ses arguments.

## <a name="remarks"></a>Notes

Le **__max** macro compare deux valeurs et retourne la valeur de la plus grande. Les arguments peuvent être de n’importe quel type de données numérique, signé ou non signé. Les deux arguments et la valeur de retour doivent être du même type de données.

L’argument retourné est évaluée deux fois par la macro. Cela peut entraîner des résultats inattendus si l’argument est une expression qui modifie sa valeur lorsqu’elle est évaluée, tels que `*p++`.

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Exemple

Pour plus d’informations, consultez l’exemple pour [__min](min.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>