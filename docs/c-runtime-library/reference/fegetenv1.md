---
title: fegetenv
ms.date: 04/05/2018
apiname:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: d3985e4dd2b3944bcdddb79605887def7ba15473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334409"
---
# <a name="fegetenv"></a>fegetenv

Stocke l’environnement à virgule flottante actuel dans l’objet spécifié.

## <a name="syntax"></a>Syntaxe

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Paramètres

*penv*<br/>
Pointeur vers un **fenv_t** objet destiné à contenir les valeurs d’environnement à virgule flottante actuel.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si l’environnement à virgule flottante a été stockée dans *penv*. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

Le **fegetenv** fonction stocke l’environnement à virgule flottante actuel dans l’objet vers lequel pointé *penv*. L’environnement à virgule flottante rassemble les indicateurs d’état et les modes de contrôle qui affectent les calculs à virgule flottante. Cela inclut le mode de la direction de l’arrondi et les indicateurs d’état pour les exceptions de virgule flottante.  Si *penv* ne pointe pas vers une valide **fenv_t** de l’objet, le comportement suivant n’est pas défini.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
