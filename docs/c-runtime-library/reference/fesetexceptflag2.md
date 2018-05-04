---
title: fesetexceptflag | Documents Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eef8ba1c91e6db4f0d620ef820a6487b3b17e649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="fesetexceptflag"></a>fesetexceptflag

Définit les indicateurs d’état à virgule flottante spécifiés dans l’environnement à virgule flottante actuel.

## <a name="syntax"></a>Syntaxe

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>Paramètres

*pstatus*<br/>
Pointeur vers un **fexcept_t** objet contenant les valeurs pour définir des indicateurs d’état de l’exception. L’objet peut être défini par un appel précédent à [fegetexceptflag](fegetexceptflag2.md).

*sauf*<br/>
Indicateurs d’état d’exception de virgule flottante à définir.

## <a name="return-value"></a>Valeur de retour

Si tous les indicateurs d’état d’exception spécifiés sont définis correctement, retourne 0. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

Le **fesetexceptflag** fonction définit l’état des indicateurs d’état de l’exception de virgule flottante spécifié par *, sauf* pour les valeurs correspondantes définies dans le **fexcept_t** objet vers lequel pointe *pstatus*.  Elle ne déclenche pas les exceptions. Le *pstatus* pointeur doit pointer vers un valide **fexcept_t** objet ou le comportement suivant n’est pas défini. Le **fesetexceptflag** fonction prend en charge ces valeurs de macros d’exception dans *, sauf*, défini dans \<fenv.h > :

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALLEXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

Le *, sauf* argument peut être égal à zéro, un de l’exception à virgule flottante prises en charge des macros ou l’opérateur de bits ou de deux ou plusieurs des macros. L’effet de toute autre valeur d’argument est indéfini.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
