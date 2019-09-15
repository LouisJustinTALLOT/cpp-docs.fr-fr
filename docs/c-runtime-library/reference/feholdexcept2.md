---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941188"
---
# <a name="feholdexcept"></a>feholdexcept

Enregistre l’environnement à virgule flottante actuel dans l’objet spécifié, supprime les indicateurs d’état à virgule flottante et, si possible, place l’environnement à virgule flottante en mode sans interruption.

## <a name="syntax"></a>Syntaxe

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Paramètres

*penv*<br/>
Pointeur vers un objet **fenv_t** pour contenir une copie de l’environnement à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Retourne zéro si et seulement si la fonction est en mesure d’activer la gestion des exceptions de virgule flottante non arrêtée.

## <a name="remarks"></a>Notes

La fonction **feholdexcept** est utilisée pour stocker l’état de l’environnement à virgule flottante actuel dans l’objet **fenv_t** pointé par *penv*et pour définir l’environnement de façon à ce qu’il n’interrompe pas l’exécution sur les exceptions à virgule flottante. Il s’agit du mode sans interruption.  Ce mode reste actif jusqu’à ce que l’environnement soit restauré à l’aide de [fesetenv](fesetenv1.md) ou [feupdateenv](feupdateenv.md).

Vous pouvez utiliser cette fonction au début d’une sous-routine qui a besoin de masquer une ou plusieurs exceptions de virgule flottante à l’appelant. Pour signaler une exception, vous pouvez simplement effacer les exceptions indésirables à l’aide de [feclearexcept,](feclearexcept1.md) puis mettre fin au mode non-arrêt avec un appel à **feupdateenv**.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
