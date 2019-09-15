---
title: __pctype_func
ms.date: 11/04/2016
api_name:
- __pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: f5dae74dd601df1dc737293a181eca60f5cd23f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944038"
---
# <a name="__pctype_func"></a>__pctype_func

Récupère un pointeur vers un tableau d’informations de classification des caractères.

## <a name="syntax"></a>Syntaxe

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers un tableau d’informations de classification des caractères.

## <a name="remarks"></a>Notes

Les informations contenues dans le tableau de classification des caractères est réservé exclusivement à un usage interne et utilisé par diverses fonctions de classification des caractères de type `char`. Pour plus d’informations, consultez la section `Remarks` de [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Voir aussi

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
