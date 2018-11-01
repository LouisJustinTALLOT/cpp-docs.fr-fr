---
title: feraiseexcept
ms.date: 04/05/2018
apiname:
- feraiseexcept
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
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 581dd4026a20ce7221945c5815af3ae102f132fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532247"
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

## <a name="return-value"></a>Valeur de retour

Si toutes les exceptions spécifiées sont correctement déclenchées, retourne 0.

## <a name="remarks"></a>Notes

Le **feraiseexcept** fonction tente de déclencher des exceptions de virgule flottante spécifiées par *, sauf*.   Le **feraiseexcept** fonction prend en charge les macros d’exception suivantes, définies dans \<fenv.h > :

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALLEXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

Le *, sauf* argument peut être égal à zéro, une des valeurs de macro d’exception, ou l’opérateur de bits ou de deux ou plusieurs des macros d’exception prises en charge. Si une des macros d’exception spécifiées est FE_OVERFLOW ou FE_UNDERFLOW, l’exception FE_INEXACT peut être déclenchée en tant qu’effet secondaire.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

**Microsoft Specific :** les exceptions spécifiées dans *, sauf* sont déclenchés dans l’ordre FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Toutefois, FE_INEXACT peut être déclenchée quand FE_OVERFLOW ou FE_UNDERFLOW est déclenchée, même si non spécifié dans *, sauf*. **Fin de la section spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
