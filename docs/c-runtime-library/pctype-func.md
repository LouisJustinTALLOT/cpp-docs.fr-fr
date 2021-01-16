---
description: 'En savoir plus sur : __pctype_func'
title: __pctype_func
ms.date: 1/14/2021
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 492f4a4c6ff5a23c05c15267d7ac00f72bc6eb94
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242954"
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

## <a name="remarks"></a>Remarques

Les informations contenues dans la table de classification des caractères sont réservées à un usage interne et sont utilisées par différentes fonctions qui classent les caractères de type **`char`** . Pour plus d’informations, consultez la section `Remarks` de [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Voir aussi

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
