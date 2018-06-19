---
title: _ASSERT, _ASSERTE, _ASSERT_EXPR, macros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa84e5c032cefa49ef3a9d21d3bbfc2073d02e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399736"
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)

Évaluer une expression et générer un rapport de débogage lorsque le résultat est **False** (version debug uniquement).

## <a name="syntax"></a>Syntaxe

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Paramètres

*booleanExpression* une expression scalaire (expressions de pointeur comprises) qui prend la valeur différente de zéro (true) ou 0 (false).

*message* large chaîne à afficher dans le cadre du rapport.

## <a name="remarks"></a>Notes

Le **_ASSERT_EXPR**, **_ASSERT** et **_ASSERTE** macros fournissent une application avec un mécanisme propre et simple pour vérifier des hypothèses pendant le processus de débogage. Elles sont très flexibles, car vous n’avez pas besoin de les placer entre des instructions `#ifdef` pour les empêcher d’être appelées dans une version commerciale d’une application. Cette flexibilité s’obtient grâce à la macro [_DEBUG](../../c-runtime-library/debug.md) . **_ASSERT_EXPR**, **_ASSERT** et **_ASSERTE** sont disponibles uniquement quand **_DEBUG** est définie au moment de la compilation. Lorsque **_DEBUG** est ne pas défini, les appels à ces macros sont supprimés lors du prétraitement.

**_ASSERT_EXPR**, **_ASSERT** et **_ASSERTE** évaluer leurs *booleanExpression* argument et si le résultat est **false**(0), elles affichent un message de diagnostic et appellent [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) pour générer un rapport de débogage. Le **_ASSERT** macro imprime un message de diagnostic simple, **_ASSERTE** inclut une représentation sous forme de chaîne de l’expression a échoué dans le message, et **_ASSERT_EXPR** inclut le *message* chaîne dans le message de diagnostic. Ces macros ne font rien lorsque *booleanExpression* prend la valeur différente de zéro.

**_ASSERT_EXPR**, **_ASSERT** et **_ASSERTE** appeler **_CrtDbgReportW**, ce qui entraîne l’ensemble de la sortie en caractères larges. **_ASSERTE** imprime correctement les caractères Unicode dans *booleanExpression* et **_ASSERT_EXPR** imprime les caractères Unicode dans *message*.

Étant donné que la **_ASSERTE** macro Spécifie l’expression qui a échoué, et **_ASSERT_EXPR** permet que vous spécifiez un message dans le rapport généré, elles permettent aux utilisateurs d’identifier le problème sans faire référence à la code source de l’application. Toutefois, un inconvénient est que chaque *message* imprimé par **_ASSERT_EXPR** et chaque expression évaluée par **_ASSERTE** est inclus dans la sortie (version débogage) fichier de votre application comme une constante de chaîne. Par conséquent, si un grand nombre d’appels sont effectués à **_ASSERT_EXPR** ou **_ASSERTE**, ces expressions peuvent augmenter considérablement la taille de votre fichier de sortie.

Sauf indication contraire avec les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md) , les messages s’affichent dans une boîte de dialogue contextuelle, ce qui équivaut à définir :

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** génère le rapport de débogage et détermine sa ou ses destinations, selon le mode rapport actuel ou les modes et les fichiers définis pour le **_CRT_ASSERT** type de rapport. Par défaut, les erreurs et les échecs d’assertion sont dirigés vers une fenêtre de message de débogage. Les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md) servent à définir les destinations de chaque type de rapport.

Lorsque la destination est une fenêtre de message de débogage et l’utilisateur clique sur le **réessayer** bouton, **_CrtDbgReportW** retourne 1, à l’origine de la **_ASSERT_EXPR**, **_ ASSERT** et **_ASSERTE** macros pour démarrer le débogueur si le débogage juste-à-temps (JIT) est activé.

Pour plus d’informations sur le processus de création de rapports, consultez la fonction [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md). Pour plus d’informations sur la résolution des échecs d’assertion et l’utilisation de ces macros comme mécanisme de gestion des erreurs de débogage consultez [Utilisation de macros pour la vérification et la création de rapports](/visualstudio/debugger/macros-for-reporting).

Outre la **_ASSERT** macros, le [assert](assert-macro-assert-wassert.md) macro peut être utilisée pour vérifier la logique du programme. Cette macro est disponible dans les versions Debug et Release des bibliothèques. Les macros de débogage [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) sont également disponibles pour générer un rapport de débogage, mais elles n’évaluent pas d’expression. Le **_RPT** macros génèrent un rapport simple. Le **_RPTF** macros incluent le nombre de fichiers et de la ligne source où la macro de rapport a été appelée dans le rapport généré. Versions à caractères larges de ces macros sont disponibles (**_RPTW**, **_RPTFW**). Les versions à caractères larges sont identiques aux versions à caractères étroits, sauf que des chaînes de caractères sont utilisées pour tous les paramètres de chaînes et la sortie.

Bien que **_ASSERT_EXPR**, **_ASSERT** et **_ASSERTE** sont des macros et sont disponibles en incluant \<crtdbg.h >, l’application doit être liée à un débogage version de la bibliothèque Runtime C lorsque **_DEBUG** est définie, car ces macros appellent d’autres fonctions d’exécution.

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>Exemple

Dans ce programme, les appels sont effectués à la **_ASSERT** et **_ASSERTE** macros pour tester la condition `string1 == string2`. Si la condition échoue, ces macros affichent un message de diagnostic. Le **_RPT** et **_RPTF** groupe de macros est également utilisé dans ce programme, en guise d’alternative à la **printf** (fonction).

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[assert (macro), _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW, macros](rpt-rptf-rptw-rptfw-macros.md)<br/>
