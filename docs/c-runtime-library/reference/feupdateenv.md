---
title: feupdateenv
ms.date: 04/05/2018
apiname:
- feupdateenv
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
apitype: HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 6d553d6899f55f5bdfb3ff313e88abfcb56ab4ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334072"
---
# <a name="feupdateenv"></a>feupdateenv

Enregistre les exceptions de virgule flottante déclenchées, restaure l’état de l’environnement à virgule flottante spécifié, puis lève les exceptions de virgule flottante enregistrées.

## <a name="syntax"></a>Syntaxe

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Paramètres

*penv*<br/>
Pointeur vers un **fenv_t** objet qui contient un environnement à virgule flottante en tant que jeu par un appel à [fegetenv](fegetenv1.md) ou [feholdexcept](feholdexcept2.md). Vous pouvez également spécifier l’environnement à virgule flottante de démarrage par défaut à l’aide de la macro FE_DFL_ENV.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si toutes les actions se sont déroulées correctement. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

Le **feupdateenv** fonction effectue plusieurs actions. Tout d’abord, elle stocke automatiquement les indicateurs d’état d’exception de virgule flottante déclenchés actuels. Ensuite, il définit l’environnement à virgule flottante actuel à partir de la valeur stockée dans le **fenv_t** objet vers lequel pointe *penv*. Si *penv* n’est pas **FE_DFL_ENV** ou ne pointe pas vers une valide **fenv_t** de l’objet, le comportement suivant n’est pas défini. Enfin, **feupdateenv** lève les exceptions de virgule flottante stockées localement.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
