---
title: _getmbcp
ms.date: 4/2/2020
api_name:
- _getmbcp
- _o__getmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getmbcp
- getmbcp
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
ms.openlocfilehash: 96bf24bbff836849de1b7689ed69bd45871f275a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913618"
---
# <a name="_getmbcp"></a>_getmbcp

Récupère la page de codes actuelle.

## <a name="syntax"></a>Syntaxe

```C
int _getmbcp( void );
```

## <a name="return-value"></a>Valeur de retour

Retourne la page de codes multioctets actuelle. Si la valeur de retour est égale à 0, une page de codes sur un octet est en cours d’utilisation.

## <a name="remarks"></a>Notes 

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getmbcp**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_setmbcp](setmbcp.md)<br/>
