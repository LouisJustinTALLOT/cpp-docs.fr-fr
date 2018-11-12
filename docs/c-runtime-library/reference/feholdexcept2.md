---
title: feholdexcept
ms.date: 04/05/2018
apiname:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 26097398b9f9d498ab4c56690dc9c6cbb950bafb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525735"
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
Pointeur vers un **fenv_t** objet destiné à contenir une copie de l’environnement à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Retourne zéro si et seulement si la fonction peut correctement activer la gestion des exceptions à virgule flottante sans interruption.

## <a name="remarks"></a>Notes

Le **feholdexcept** fonction est utilisée pour stocker l’état de l’environnement à virgule flottante actuel dans le **fenv_t** objet vers lequel pointe *penv*, définir l’environnement interrompt pas l’exécution sur les exceptions de virgule flottante. Il s’agit du mode sans interruption.  Ce mode reste actif jusqu’à ce que l’environnement soit restauré à l’aide de [fesetenv](fesetenv1.md) ou [feupdateenv](feupdateenv.md).

Vous pouvez utiliser cette fonction au début d’une sous-routine qui a besoin de masquer une ou plusieurs exceptions de virgule flottante à l’appelant. Pour signaler une exception, vous pouvez simplement désactiver les exceptions indésirables à l’aide de [feclearexcept](feclearexcept1.md) puis mettre fin à la mode sans interruption avec un appel à **feupdateenv**.

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
