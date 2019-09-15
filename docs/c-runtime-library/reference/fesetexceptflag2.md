---
title: fesetexceptflag
ms.date: 04/05/2018
api_name:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
ms.openlocfilehash: 29a6b36b0744bec30463fe55df05fe26180b93fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941088"
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
Pointeur vers un objet **fexcept_t** contenant les valeurs pour lesquelles définir les indicateurs d’état d’exception. L’objet peut être défini par un appel précédent à [fegetexceptflag](fegetexceptflag2.md).

*excepts*<br/>
Indicateurs d’état d’exception de virgule flottante à définir.

## <a name="return-value"></a>Valeur de retour

Si tous les indicateurs d’état d’exception spécifiés sont définis correctement, retourne 0. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

La fonction **fesetexceptflag** définit l’état des indicateurs d’état d’exception de virgule flottante spécifiés par à l' *exception* des valeurs correspondantes définies dans l’objet **fexcept_t** pointé par *pstatus*.  Elle ne déclenche pas les exceptions. Le pointeur *pstatus* doit pointer vers un objet **fexcept_t** valide, ou le comportement suivant n’est pas défini. La fonction **fesetexceptflag** prend en charge ces valeurs de macros d’exception dans \< *except*, défini dans fenv. h >:

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALLEXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

L’argument *EXCEPTS* peut être égal à zéro, l’une des macros d’exception de virgule flottante prises en charge ou l’opération de bits or d’au moins deux macros. L’effet de toute autre valeur d’argument est indéfini.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>
