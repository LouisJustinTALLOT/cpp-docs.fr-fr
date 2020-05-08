---
title: _CItan
ms.date: 4/2/2020
api_name:
- _CItan
- _o__CItan
api_location:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CItan
- CItan
helpviewer_keywords:
- CItan intrinsic
- _CItan intrinsic
ms.assetid: d1ea3113-50a2-45a6-b6bc-680fcdcc0928
ms.openlocfilehash: 65cce8b094a1508566e2de7162b9e8e76712742a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918335"
---
# <a name="_citan"></a>_CItan

Calcule la tangente de la valeur supérieure de la pile virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CItan();
```

## <a name="remarks"></a>Notes 

Cette version de la fonction [tan](../c-runtime-library/reference/tan-tanf-tanl.md) a une convention d’appel spécialisée que le compilateur comprend. Elle accélère l’exécution, car elle empêche la génération de copies et facilite l’allocation de registres.

La valeur obtenue est envoyée (push) en haut de la pile virgule flottante.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Spécifications

**Plateforme :** x86

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)<br/>
