---
title: fesetenv | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fesetenv
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
- fesetenv
- fenv/fesetenv
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd761f505c602aad44c5e00df223d4a6c983e851
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397244"
---
# <a name="fesetenv"></a>fesetenv

Définit l’environnement à virgule flottante actuel.

## <a name="syntax"></a>Syntaxe

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Paramètres

*penv*<br/>
Pointeur vers un **fenv_t** objet qui contient un environnement à virgule flottante en tant que jeu par un appel à [fegetenv](fegetenv1.md) ou [feholdexcept](feholdexcept2.md). Vous pouvez également spécifier l’environnement à virgule flottante de démarrage par défaut à l’aide de la **FE_DFL_ENV** (macro).

## <a name="return-value"></a>Valeur de retour

Retourne 0 si l’environnement a été correctement défini. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

Le **fesetenv** fonction définit l’environnement actuel et à virgule flottante à partir de la valeur stockée dans le **fenv_t** objet pointé par *penv*. L’environnement à virgule flottante rassemble les indicateurs d’état et les modes de contrôle qui affectent les calculs à virgule flottante. Cela inclut le mode d’arrondi et les indicateurs d’état pour les exceptions de virgule flottante.  Si *penv* n’est pas **FE_DFL_ENV** ou ne pointe pas vers un valide **fenv_t** de l’objet, le comportement suivant n’est pas défini.

Un appel à cette fonction définit l’exception des indicateurs d’état qui se trouvent dans le *penv* objet, mais il ne déclenche pas ces exceptions.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
