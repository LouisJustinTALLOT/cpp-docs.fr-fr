---
title: _ASSERT, _ASSERTE, _ASSERT_EXPR (macros)
ms.date: 11/04/2016
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: efdf7852734d8367d053b1300cd32b8a9195d0cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943756"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)

Évaluer une expression et générer un rapport de débogage lorsque le résultat est **false** (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Paramètres

*booleanExpression*<br/>
Expression scalaire (expressions de pointeur comprises) évaluée à une valeur différente de zéro (true) ou égale à zéro (false).

*message*<br/>
Large chaîne à afficher dans le cadre du rapport.

## <a name="remarks"></a>Notes

Les macros **_ASSERT_EXPR**, _ **Assert** et **asserte** fournissent une application avec un mécanisme propre et simple pour vérifier les hypothèses pendant le processus de débogage. Elles sont très flexibles, car vous n’avez pas besoin de les placer entre des instructions `#ifdef` pour les empêcher d’être appelées dans une version commerciale d’une application. Cette flexibilité s’obtient grâce à la macro [_DEBUG](../../c-runtime-library/debug.md) . **_ASSERT_EXPR**, _ **Assert** et _ **asserte** sont uniquement disponibles quand **_ DEBUG** est défini au moment de la compilation. Lorsque **_ DEBUG** n’est pas défini, les appels à ces macros sont supprimés lors du prétraitement.

**_ASSERT_EXPR**, _ **Assert** et _ **asserte** évaluent leur argument *booleanExpression* et, lorsque le résultat est **false** (0), ils affichent un message de diagnostic et appellent [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) pour générer un rapport de débogage. La macro _ **Assert** imprime un message de diagnostic simple, _ **asserte** comprend une représentation sous forme de chaîne de l’expression qui a échoué dans le message et **_ASSERT_EXPR** comprend la chaîne de *message* dans le message de diagnostic. Ces macros ne font rien lorsque *booleanExpression* a une valeur différente de zéro.

**_ASSERT_EXPR**, _ **Assert** et _ **Assert** Invoke **_CrtDbgReportW**, qui entraîne l’affichage de toutes les sorties en caractères larges. _ **Asserte** d’imprimer correctement les caractères Unicode dans *booleanExpression* et **_ASSERT_EXPR** imprime les caractères Unicode dans le *message*.

Étant donné que la macro _ **asserte** spécifie l’expression qui a échoué, et **_ASSERT_EXPR** vous permet de spécifier un message dans le rapport généré, elles permettent aux utilisateurs d’identifier le problème sans faire référence au code source de l’application. Toutefois, il existe un inconvénient dans le fait que chaque *message* imprimé par **_ASSERT_EXPR** et chaque expression évaluée par _ **asserte** est inclus dans le fichier de sortie (version de débogage) de votre application sous la forme d’une constante de chaîne. Par conséquent, si un grand nombre d’appels sont effectués sur **_ASSERT_EXPR** ou _ **asserte**, ces expressions peuvent augmenter la taille de votre fichier de sortie.

Sauf indication contraire avec les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md) , les messages s’affichent dans un boîte de dialogue contextuelle, ce qui équivaut à définir :

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** génère le rapport de débogage et détermine sa ou ses destinations, en fonction du ou des modes de rapport actifs et du fichier défini pour le type de rapport **_CRT_ASSERT** . Par défaut, les erreurs et les échecs d’assertion sont dirigés vers une fenêtre de message de débogage. Les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md) servent à définir les destinations de chaque type de rapport.

Lorsque la destination est une fenêtre de message de débogage et que l’utilisateur clique sur le bouton **Réessayer** , **_CrtDbgReportW** retourne 1, ce qui amène les macros **_ASSERT_EXPR**, _ **Assert** et **asserte** à démarrer le débogueur, à condition que le débogage juste-à-temps (JIT) est activé.

Pour plus d’informations sur le processus de création de rapports, consultez la fonction [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) . Pour plus d’informations sur la résolution des échecs d’assertion et l’utilisation de ces macros comme mécanisme de gestion des erreurs de débogage consultez [Utilisation de macros pour la vérification et la création de rapports](/visualstudio/debugger/macros-for-reporting).

Outre les macros _ [Assert](assert-macro-assert-wassert.md) , vous pouvez utiliser la macro Assert pour vérifier la **logique du programme** . Cette macro est disponible dans les versions Debug et Release des bibliothèques. Les macros de débogage [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) sont également disponibles pour générer un rapport de débogage, mais elles n’évaluent pas d’expression. Les macros **_RPT** génèrent un rapport simple. Les macros **_RPTF** incluent le fichier source et le numéro de ligne où la macro de rapport a été appelée dans le rapport généré. Les versions à caractères larges de ces macros sont disponibles ( **_RPTW**, **_RPTFW**). Les versions à caractères larges sont identiques aux versions à caractères étroits, sauf que des chaînes de caractères sont utilisées pour tous les paramètres de chaînes et la sortie.

Bien que **_ASSERT_EXPR**, _ **Assert** et _ **asserte** soient des \<macros et qu’elles soient disponibles en incluant CRTDBG. h >, l’application doit établir une liaison avec une version Debug de la bibliothèque Runtime C lorsque **_ DEBUG** est défini, car ces macros appellent d’autres fonctions d’exécution.

## <a name="requirements"></a>Configuration requise

|Macro|En-tête requis|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ ASSERT, _** **ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>Exemple

Dans ce programme, des appels sont effectués aux macros _ **Assert** et _ **Assert** pour tester la condition `string1 == string2`. Si la condition échoue, ces macros affichent un message de diagnostic. Le groupe de macros **_RPT** et **_RPTF** est également testé dans ce programme, comme alternative à la fonction **printf** .

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
