---
description: 'En savoir plus sur : fesetenv'
title: fesetenv
ms.date: 04/05/2018
api_name:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 662634e467eb224af813f60ab4434d4857d21d50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289437"
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
Pointeur vers un objet **fenv_t** qui contient un environnement à virgule flottante tel qu’il est défini par un appel à [fegetenv](fegetenv1.md) ou [feholdexcept](feholdexcept2.md). Vous pouvez également spécifier l’environnement à virgule flottante de démarrage par défaut à l’aide de la macro **FE_DFL_ENV** .

## <a name="return-value"></a>Valeur renvoyée

Retourne 0 si l’environnement a été correctement défini. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

La fonction **fesetenv** définit l’environnement à virgule flottante actuel à partir de la valeur stockée dans l’objet **fenv_t** pointé par *penv*. L’environnement à virgule flottante rassemble les indicateurs d’état et les modes de contrôle qui affectent les calculs à virgule flottante. Cela inclut le mode d’arrondi et les indicateurs d’état pour les exceptions de virgule flottante.  Si *penv* n’est pas **FE_DFL_ENV** ou ne pointe pas vers un objet **fenv_t** valide, le comportement suivant n’est pas défini.

Un appel à cette fonction définit les indicateurs d’état d’exception qui se trouvent dans l’objet *penv* , mais il ne déclenche pas ces exceptions.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
