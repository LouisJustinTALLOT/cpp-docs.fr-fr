---
description: 'En savoir plus sur : feraiseexcept'
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 8e7a06006cfdc768fdaa306bc293857f1c375b90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124941"
---
# <a name="feraiseexcept"></a>feraiseexcept

Déclenche les exceptions de virgule flottante spécifiées.

## <a name="syntax"></a>Syntaxe

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Paramètres

*sauf*<br/>
Exceptions de virgule flottante à déclencher.

## <a name="return-value"></a>Valeur renvoyée

Si toutes les exceptions spécifiées sont correctement déclenchées, retourne 0.

## <a name="remarks"></a>Notes

La fonction **feraiseexcept** tente de déclencher les exceptions à virgule flottante spécifiées par *except*.   La fonction **feraiseexcept** prend en charge les macros d’exception suivantes, définies dans \<fenv.h> :

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALL_EXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

L’argument *EXCEPTS* peut être zéro, l’une des valeurs de macro d’exception ou l’opération de bits or d’au moins deux des macros d’exception prises en charge. Si une des macros d’exception spécifiées est FE_OVERFLOW ou FE_UNDERFLOW, l’exception FE_INEXACT peut être déclenchée en tant qu’effet secondaire.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

**Spécifique à Microsoft :** Les exceptions spécifiées dans *except* sont générées dans l’ordre FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Toutefois, FE_INEXACT peut être déclenché lorsque FE_OVERFLOW ou FE_UNDERFLOW est déclenché, même s’il n’est pas spécifié dans *except*.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
