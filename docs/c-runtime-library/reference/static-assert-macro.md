---
description: 'En savoir plus sur : macro _STATIC_ASSERT'
title: _STATIC_ASSERT, macro
ms.date: 11/04/2016
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
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: bbdb615cccfb245868d4c282acf86c9228ea574b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171197"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT, macro

Évaluer une expression au moment de la compilation et générer une erreur lorsque le résultat est **false**.

## <a name="syntax"></a>Syntaxe

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Expression (pointeurs inclus) qui prend une valeur différente de zéro (**true**) ou 0 (**false**).

## <a name="remarks"></a>Notes

Cette macro ressemble aux [macros _ASSERT et _ASSERTE](assert-asserte-assert-expr-macros.md), à l’exception du fait que *booleanExpression* est évalué au moment de la compilation plutôt qu’au moment de l’exécution. Si *booleanExpression* prend la **valeur false** (0), l' [Erreur du compilateur C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) est générée.

## <a name="example"></a>Exemple

Dans cet exemple, nous vérifions si [](../../c-language/sizeof-operator-c.md) le sizeof **`int`** est supérieur ou égal à 2 octets et si le [sizeof](../../c-language/sizeof-operator-c.md) a **`long`** est 1 octet. Le programme ne se compilera pas et générera une [Erreur du compilateur C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) , car un **`long`** est supérieur à 1 octet.

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

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE _ASSERT_EXPR macros](assert-asserte-assert-expr-macros.md)<br/>
