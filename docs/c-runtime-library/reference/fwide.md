---
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
ms.openlocfilehash: 2e986ba5ab28072f4933e555eea32a5893c8df56
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956218"
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

*stream*<br/>
Pointeur vers la structure de **fichier** (ignoré).

*mode*<br/>
La nouvelle largeur du flux : positive pour un caractère large, négative pour un octet, zéro pour laisser inchangé. (Cette valeur est ignorée.)

## <a name="return-value"></a>Valeur de retour

Cette fonction retourne actuellement simplement le *mode*.

## <a name="remarks"></a>Notes

La version actuelle de cette fonction n’est pas conforme à la norme.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).