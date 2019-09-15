---
title: _CIsin
ms.date: 04/10/2018
api_name:
- _CIsin
api_location:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CIsin
- _CIsin
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
ms.openlocfilehash: 66f26e9fa4dd08d18b15deca4efa40c236e092c9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944544"
---
# <a name="_cisin"></a>_CIsin

Calcule le sinus de la valeur supérieure de la pile virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIsin();
```

## <a name="remarks"></a>Notes

Cette version intrinsèque de la fonction [sin](../c-runtime-library/reference/sin-sinf-sinl.md) a une convention d’appel spécialisée que le compilateur comprend. Elle accélère l’exécution, car elle empêche la génération de copies et facilite l’allocation de registres.

La valeur obtenue est envoyée (push) en haut de la pile virgule flottante.

## <a name="requirements"></a>Configuration requise

**Plateforme :** x86

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)<br/>
