---
description: 'En savoir plus sur : fwide'
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
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
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 5cc49bb92421ac8899df9850c110a519d32b1d1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273746"
---
# <a name="fwide"></a>fwide

Non implémenté.

## <a name="syntax"></a>Syntaxe

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur vers la structure de **fichier** (ignoré).

*mode*<br/>
La nouvelle largeur du flux : positive pour un caractère large, négative pour un octet, zéro pour laisser inchangé. (Cette valeur est ignorée.)

## <a name="return-value"></a>Valeur renvoyée

Cette fonction retourne actuellement simplement le *mode*.

## <a name="remarks"></a>Notes

La version actuelle de cette fonction n’est pas conforme à la norme.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Pour plus d’informations, consultez [Compatibilité](../../c-runtime-library/compatibility.md).
