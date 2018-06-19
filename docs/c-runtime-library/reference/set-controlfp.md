---
title: _set_controlfp | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_controlfp
apilocation:
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
apitype: DLLExport
f1_keywords:
- set_controlfp
- _set_controlfp
dev_langs:
- C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2647e9719c2aa3fe303393fcc1da55de0385581
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406418"
---
# <a name="setcontrolfp"></a>_set_controlfp

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

*masque*<br/>
Masque des bits du nouveau mot de contrôle à définir.

## <a name="return-value"></a>Valeur de retour

Aucun

## <a name="remarks"></a>Notes

Le **_set_controlfp** fonction est similaire à **_control87**, mais il affecte uniquement le mot de contrôle à virgule flottante *newControl*. Les bits contenus dans les valeurs indiquent l’état de contrôle à virgule flottante. L’état de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante. Vous pouvez également masquer ou afficher les exceptions de virgule flottante à l’aide de **_set_controlfp**. Pour plus d’informations, consultez [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md).

Cette fonction est déconseillée lors de la compilation avec [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) , car le common language runtime prend uniquement en charge la précision en virgule flottante par défaut.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|Compatibilité|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|Processeur x86 uniquement|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
