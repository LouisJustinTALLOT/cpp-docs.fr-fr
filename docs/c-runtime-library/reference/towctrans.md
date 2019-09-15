---
title: towctrans
ms.date: 11/04/2016
api_name:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: d63fc343647cd0f949f282e2a64d4a0636e62bd7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957426"
---
# <a name="towctrans"></a>towctrans

Transforme un caractère.

## <a name="syntax"></a>Syntaxe

```C
wint_t towctrans(
   wint_t c,
   wctrans_t category
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère que vous souhaitez transformer.

*category*<br/>
Identificateur qui contient la valeur de retour de [wctrans](wctrans.md).

## <a name="return-value"></a>Valeur de retour

Le caractère *c*, après que **towctrans** a utilisé la règle de transformation dans la *catégorie*.

## <a name="remarks"></a>Notes

La valeur de *Category* doit avoir été retournée par un appel antérieur réussi à [wctrans](wctrans.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez **wctrans** pour obtenir un exemple qui utilise **towctrans**.

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
