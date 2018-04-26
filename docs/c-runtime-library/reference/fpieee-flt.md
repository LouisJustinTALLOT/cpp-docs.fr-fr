---
title: _fpieee_flt | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _fpieee_flt
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
- fpieee_flt
- _fpieee_flt
dev_langs:
- C++
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da55d2940f38a90dfa5c69d71d394e865bb3b4c0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="fpieeeflt"></a>_fpieee_flt

Appelle un gestionnaire d'interruptions défini par l'utilisateur pour les exceptions à virgule flottante IEEE.

## <a name="syntax"></a>Syntaxe

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>Paramètres

*excCode*<br/>
Code d’exception.

*excInfo*<br/>
Pointeur désignant la structure d’informations sur les exceptions Windows NT.

*Gestionnaire*<br/>
Pointeur vers la routine du gestionnaire d'interruptions IEEE de l'utilisateur.

## <a name="return-value"></a>Valeur de retour

La valeur de retour de **_fpieee_flt** est la valeur retournée par *gestionnaire*. Ainsi, la routine de filtre IEEE peut être utilisée dans la clause d'exception d'un mécanisme de gestion structurée des exceptions (SEH).

## <a name="remarks"></a>Notes

Le **_fpieee_flt** fonction appelle un gestionnaire d’interruptions défini par l’utilisateur pour les exceptions à virgule flottante IEEE et lui fournit toutes les informations pertinentes. Cette routine sert de filtre d'exception dans le mécanisme SEH, qui appelle votre propre gestionnaire d'exceptions IEEE si nécessaire.

Le **_FPIEEE_RECORD** structure, définie dans Fpieee.h, contient des informations relatives à une exception à virgule flottante IEEE. Cette structure est passée au gestionnaire d’interruptions défini par l’utilisateur par **_fpieee_flt**.

|Champ _FPIEEE_RECORD|Description|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Précision**|Ces **non signé** **int** champs contiennent des informations sur l’environnement à virgule flottante au moment où l’exception s’est produite.|
|**Opération**|Cela **non signé** **int** champ indique le type d’opération qui a provoqué l’interruption. Si le type est une comparaison (**_FpCodeCompare**), vous pouvez fournir une des spéciale **_FPIEEE_COMPARE_RESULT** valeurs (telle que définie dans Fpieee.h) dans le **Result.Value** champ. Le type de conversion (**_FpCodeConvert**) indique que l’interruption s’est produite lors d’une opération de conversion en virgule flottante. Vous pouvez examiner le **Operand1** et **résultat** types afin de déterminer le type de conversion tenté.|
|**operand1**<br/>**operand2**<br/>**Résultat**|Ces **_FPIEEE_VALUE** structures indiquent les types et les valeurs des opérandes et résultat proposé. Chaque structure contient ces champs :<br /><br /> **OperandValid** - indicateur indiquant si la valeur de réponse est valide.<br />**Format** -type de données de la valeur correspondante. Le type de format peut être retourné même si la valeur correspondante n'est pas valide.<br />**Valeur** -valeur de données de résultat ou un opérande.|
|**Cause**<br/>**Activer**<br/>**État**|**_FPIEEE_EXCEPTION_FLAGS** contient un champ de bits par type d’exception de virgule flottante. Il existe une correspondance entre ces champs et les arguments utilisés pour masquer les exceptions fournies à [_controlfp](control87-controlfp-control87-2.md). La signification exacte de chaque bit dépend du contexte :<br /><br /> **Cause** -chaque bit d’ensemble indique l’exception particulière qui a été déclenchée.<br />**Activer** -chaque bit d’ensemble indique que l’exception particulière est actuellement masquée.<br />**État** -chaque bit d’ensemble indique que l’exception particulière est actuellement en attente. Cela inclut les exceptions qui n’ont pas été déclenchées, car elles ont été masquées par **_controlfp**.|

Les exceptions en attente désactivées sont déclenchées lorsque vous les activez. Cela peut entraîner un comportement indéfini lors de l’utilisation **_fpieee_flt** comme un filtre d’exception. Appelez toujours [_clearfp](clear87-clearfp.md) avant d’activer les exceptions à virgule flottante.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
