---
title: __pctype_func
ms.date: 11/04/2016
apiname:
- __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: a152f3612373189c964aaca005fe3b989eec8694
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742019"
---
# <a name="pctypefunc"></a>__pctype_func

Récupère un pointeur vers un tableau d’informations de classification des caractères.

## <a name="syntax"></a>Syntaxe

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers un tableau d’informations de classification des caractères.

## <a name="remarks"></a>Remarques

Les informations contenues dans le tableau de classification des caractères est réservé exclusivement à un usage interne et utilisé par diverses fonctions de classification des caractères de type `char`. Pour plus d’informations, consultez la section `Remarks` de [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Voir aussi

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
