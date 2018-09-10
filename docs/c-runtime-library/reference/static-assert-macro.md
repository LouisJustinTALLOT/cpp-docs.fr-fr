---
title: _STATIC_ASSERT, macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- _STATIC_ASSERT
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8eda76666679b133b2d5486d21cd4c8e24d1fdf3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105079"
---
# <a name="staticassert-macro"></a>_STATIC_ASSERT, macro

Évalue une expression au moment de la compilation et génère une erreur lorsque le résultat est **FALSE**.

## <a name="syntax"></a>Syntaxe

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Expression (pointeurs inclus) qui prend la valeur différente de zéro à (**TRUE**) ou 0 (**FALSE**).

## <a name="remarks"></a>Notes

Cette macro ressemble à la [macros Assert et _ASSERTE](assert-asserte-assert-expr-macros.md), sauf que *booleanExpression* est évaluée au moment de la compilation et non lors de l’exécution. Si *booleanExpression* prend la valeur **FALSE** (0), [erreur du compilateur C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) est généré.

## <a name="example"></a>Exemple

Dans cet exemple, nous vérifions si le [sizeof](../../c-language/sizeof-operator-c.md) un **int** est supérieure ou égale à 2 octets et si le [sizeof](../../c-language/sizeof-operator-c.md) un **long** est 1 octet. Le programme ne peut pas être compilé et générera [erreur du compilateur C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) , car un **long** est supérieure à 1 octet.

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>Configuration requise

|Macro|En-tête requis|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR, macros](assert-asserte-assert-expr-macros.md)<br/>
