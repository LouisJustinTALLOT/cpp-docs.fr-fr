---
description: 'En savoir plus sur : _RPT, _RPTF, _RPTW, _RPTFW macros'
title: _RPT, _RPTF, _RPTW, _RPTFW, macros
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
ms.openlocfilehash: 6cc20032454002b33b4f3d297db582af09c90805
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341436"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW, macros

Suit la progression d’une application en générant un rapport de débogage (version debug uniquement). Notez que *n* spécifie le nombre d’arguments dans *args* et peut avoir la valeur 0, 1, 2, 3, 4 ou 5.

## <a name="syntax"></a>Syntaxe

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type de rapport : **_CRT_WARN**, **_CRT_ERROR** ou **_CRT_ASSERT**.

*format*<br/>
Chaîne de contrôle de format utilisée pour créer le message utilisateur.

*args*<br/>
Arguments de substitution utilisés par le *format*.

## <a name="remarks"></a>Notes

Toutes ces macros acceptent les paramètres *reportType* et *format* . De plus, il peuvent aussi accepter jusqu’à quatre arguments supplémentaires, ce qui est indiqué par le nombre ajouté au nom de la macro. Par exemple, **_RPT0** et **_RPTF0** ne prennent pas d’arguments supplémentaires, **_RPT1** et **_RPTF1** prennent *Arg1*, **_RPT2** et **_RPTF2** prennent *Arg1* et **Arg2**, et ainsi de suite.

Les macros **_RPT** et **_RPTF** sont similaires à la fonction [printf](printf-printf-l-wprintf-wprintf-l.md) , car elles peuvent être utilisées pour suivre la progression d’une application pendant le processus de débogage. Toutefois, ces macros sont plus flexibles que **printf** , car elles n’ont pas besoin d’être placées dans des instructions **#ifdef** pour les empêcher d’être appelées dans une version commerciale d’une application. Cette flexibilité est obtenue à l’aide de la macro [_DEBUG](../../c-runtime-library/debug.md) ; les macros **_RPT** et **_RPTF** sont disponibles uniquement lorsque l’indicateur **_DEBUG** est défini. Lorsque **_DEBUG** n’est pas défini, les appels à ces macros sont supprimés lors du prétraitement.

Les macros **_RPTW** et **_RPTFW** sont des versions à caractères larges de ces macros. Ils sont semblables à **wprintf** et prennent des chaînes à caractères larges comme arguments.

Les macros **_RPT** appellent la fonction [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) pour générer un rapport de débogage avec un message utilisateur. Les macros **_RPTW** appellent la fonction **_CrtDbgReportW** pour générer le même rapport avec des caractères larges. Les macros **_RPTF** et **_RPTFW** créent un rapport de débogage avec le fichier source et le numéro de ligne où la macro de rapport a été appelée, en plus du message utilisateur. Le message utilisateur est créé en remplaçant les arguments **arg**[*n*] dans la chaîne de *format* , à l’aide des mêmes règles que celles définies par la fonction [printf](printf-printf-l-wprintf-wprintf-l.md) .

**_CrtDbgReport** ou **_CrtDbgReportW** génère le rapport de débogage et détermine ses destinations en fonction des modes de rapport et du fichier actuellement définis pour *reportType*. Les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md) servent à définir les destinations de chaque type de rapport.

Si une macro **_RPT** est appelée et que ni **_CrtSetReportMode** ni **_CrtSetReportFile** n’a été appelé, les messages s’affichent comme suit.

|Type de rapport|Destination de sortie|
|-----------------|------------------------|
|**_CRT_WARN**|Le texte d’avertissement ne s’affiche pas.|
|**_CRT_ERROR**|Fenêtre contextuelle. Comme si `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` avait été spécifié.|
|**_CRT_ASSERT**|Identique à **_CRT_ERROR**.|

Lorsque la destination est une fenêtre de message de débogage et que l’utilisateur choisit le bouton **Réessayer** , **_CrtDbgReport** ou **_CrtDbgReportW** retourne 1, ce qui amène ces macros à démarrer le débogueur, à condition que le débogage juste-à-temps (JIT) soit activé. Pour plus d’informations sur l’utilisation de ces macros comme mécanisme de gestion des erreurs de débogage, consultez [Utilisation de macros pour la vérification et la création de rapports](/visualstudio/debugger/macros-for-reporting).

Deux autres macros génèrent un rapport de débogage. La macro [_ASSERT](assert-asserte-assert-expr-macros.md) génère un rapport, mais seulement quand l’argument d’expression est évalué à FALSE. [_ASSERTE](assert-asserte-assert-expr-macros.md) est exactement comme **_ASSERT**, mais elle comprend l’expression qui a échoué dans le rapport généré.

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-----------|---------------------|
|Macros **_RPT**|\<crtdbg.h>|
|Macros **_RPTF**|\<crtdbg.h>|
|Macros **_RPTW**|\<crtdbg.h>|
|Macros **_RPTFW**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

Bien qu’il s’agisse de macros et qu’elles soient obtenues en incluant Crtdbg.h, l’application doit établir une liaison avec l’une des bibliothèques de débogage, car ces macros appellent d’autres fonctions de runtime.

## <a name="example"></a>Exemple

Consultez l’exemple présenté dans la rubrique [_ASSERT](assert-asserte-assert-expr-macros.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
