---
title: __pctype_func
ms.date: 4/2/2020
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 67447823b0322e647784cdbe0f3f7228e1c5fb34
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919244"
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

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Voir aussi

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
