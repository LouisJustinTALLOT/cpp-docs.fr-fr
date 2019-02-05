---
title: _CIcos
ms.date: 04/11/2018
apiname:
- _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
ms.openlocfilehash: fef9ef9e197dcd6e8a1880c3acdfa2755ccf1ae1
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702724"
---
# <a name="cicos"></a>_CIcos

Calcule le cosinus de la valeur supérieure de la pile virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Notes

Cette version de la fonction [cos](../c-runtime-library/reference/cos-cosf-cosl.md) a une convention d’appel spécialisée que le compilateur comprend. Elle accélère l’exécution, car elle empêche la génération de copies et facilite l’allocation de registres.

La valeur obtenue est envoyée (push) en haut de la pile virgule flottante.

## <a name="requirements"></a>Spécifications

**Plateforme :** x86

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
