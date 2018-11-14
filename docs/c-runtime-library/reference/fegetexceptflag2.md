---
title: fegetexceptflag
ms.date: 04/05/2018
apiname:
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: 43259001bd05bb7df9e2e1636c174018dcdaef3c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522647"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Stocke l’état actuel des indicateurs d’exception de virgule flottante spécifiés.

## <a name="syntax"></a>Syntaxe

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>Paramètres

*pstatus*<br/>
Un pointeur vers un **fexcept_t** objet destiné à contenir les valeurs actuelles des indicateurs d’exception spécifiés par *, sauf*.

*sauf*<br/>
Les indicateurs d’exception de virgule flottante à stocker dans *pstatus*.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne la valeur 0. Sinon, retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

Le **fegetexceptflag** fonction stocke l’état actuel des indicateurs d’état de l’exception de virgule flottante spécifié par *, sauf* dans le **fexcept_t** objet vers lequel pointe *pstatus*.  *pstatus* doit pointer vers un valide **fexcept_t** objet ou le comportement suivant n’est pas défini. Le **fegetexceptflag** fonction prend en charge les macros d’exception suivantes, définies dans \<fenv.h > :

|Macros d’exception|Description|
|---------------------|-----------------|
|FE_DIVBYZERO|Une erreur de singularité ou de pôle s’est produite dans une opération à virgule flottante précédente ; une valeur infinie a été créée.|
|FE_INEXACT|La fonction a été forcée d’arrondir le résultat stocké d’une opération à virgule flottante précédente.|
|FE_INVALID|Une erreur de domaine s’est produite pendant une opération à virgule flottante précédente.|
|FE_OVERFLOW|Une erreur de plage s’est produite ; le résultat d’une opération à virgule flottante précédente était trop grand pour être représenté.|
|FE_UNDERFLOW|Le résultat d’une opération à virgule flottante précédente était trop petit pour être représenté avec une précision complète ; une valeur dénormalisée a été créée.|
|FE_ALLEXCEPT|Opération OR au niveau du bit de toutes les exceptions de virgule flottante prises en charge.|

Le *, sauf* argument peut être égal à zéro, une des macros d’exception à virgule flottante prises en charge, ou l’opérateur de bits ou de deux ou plusieurs des macros. L’effet de toute autre valeur d’argument est indéfini.

Pour utiliser cette fonction, vous devez désactiver les optimisations à virgule flottante qui peuvent empêcher l’accès à l’aide de la directive `#pragma fenv_access(on)` avant l’appel. Pour plus d'informations, consultez [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête C|En-tête C++|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h>|\<cfenv>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
