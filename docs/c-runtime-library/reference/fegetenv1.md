---
description: 'En savoir plus sur : fegetenv'
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: f4d6ab3de440d2d8d7e145111339577f04699f8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322574"
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
Pointeur vers un objet **fenv_t** pour contenir les valeurs d’environnement à virgule flottante actuelles.

## <a name="return-value"></a>Valeur renvoyée

Retourne 0 si l’environnement à virgule flottante a été correctement stocké dans *penv*. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

La fonction **fegetenv** stocke l’environnement à virgule flottante actuel dans l’objet désigné par *penv*. L’environnement à virgule flottante rassemble les indicateurs d’état et les modes de contrôle qui affectent les calculs à virgule flottante. Cela inclut le mode de la direction de l’arrondi et les indicateurs d’état pour les exceptions de virgule flottante.  Si *penv* ne pointe pas vers un objet **fenv_t** valide, le comportement suivant n’est pas défini.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
