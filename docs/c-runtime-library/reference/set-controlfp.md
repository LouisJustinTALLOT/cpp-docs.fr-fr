---
description: 'En savoir plus sur : _set_controlfp'
title: _set_controlfp
ms.date: 04/05/2018
api_name:
- _set_controlfp
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 44316cb4114d06ced1b3d67a261bc8d3ceb1aee6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288865"
---
# <a name="_set_controlfp"></a>_set_controlfp

Définit le mot de contrôle à virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Paramètres

*newControl*<br/>
Nouvelles valeurs en bits du mot de contrôle.

*filtrage*<br/>
Masque des bits du nouveau mot de contrôle à définir.

## <a name="return-value"></a>Valeur renvoyée

Aucun.

## <a name="remarks"></a>Notes

La fonction **_set_controlfp** est semblable à **_control87**, mais elle définit uniquement le mot de contrôle à virgule flottante sur *newControl*. Les bits contenus dans les valeurs indiquent l’état de contrôle à virgule flottante. L’état de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante. Vous pouvez également masquer ou démasquer les exceptions de virgule flottante à l’aide de **_set_controlfp**. Pour plus d’informations, consultez [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md).

Cette fonction est déconseillée lors de la compilation avec [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , car la Common Language Runtime prend en charge uniquement la précision en virgule flottante par défaut.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|Compatibilité|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|Processeur x86 uniquement|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
