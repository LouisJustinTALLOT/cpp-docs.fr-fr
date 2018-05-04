---
title: _RPT, _RPTF, _RPTW, _RPTFW Macros | Microsoft Docs
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a53a069138b4e54988be008917e5ca2b24fa0a6c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW, macros

Suit la progression d’une application en générant un rapport de débogage (version debug uniquement). Notez que *n* Spécifie le nombre d’arguments dans *args* et peut être 0, 1, 2, 3, 4 ou 5.

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

*reportType* type de rapport : **_CRT_WARN**, **_CRT_ERROR**, ou **_CRT_ASSERT**.

*format* chaîne de contrôle de Format utilisée pour créer le message de l’utilisateur.

*args* utilisés par des arguments de Substitution *format*.

## <a name="remarks"></a>Notes

Toutes ces macros prennent le *reportType* et *format* paramètres. De plus, il peuvent aussi accepter jusqu’à quatre arguments supplémentaires, ce qui est indiqué par le nombre ajouté au nom de la macro. Par exemple, **_RPT0** et **_RPTF0** ne prendre aucun argument supplémentaire, **_RPT1** et **_RPTF1** prendre *arg1*, **_RPT2** et **_RPTF2** prendre *arg1* et **arg2**, et ainsi de suite.

Le **_RPT** et **_RPTF** macros sont similaires à la [printf](printf-printf-l-wprintf-wprintf-l.md) fonctionne, car ils peuvent être utilisés pour suivre la progression de l’application pendant le processus de débogage. Toutefois, ces macros sont plus souples que **printf** , car ils n’avez pas besoin d’être mises entre **#ifdef** instructions pour les empêcher d’être appelée dans une version commerciale d’une application. Cette souplesse est obtenue à l’aide de la [_DEBUG](../../c-runtime-library/debug.md) macro ; le **_RPT** et **_RPTF** macros sont disponibles uniquement quand le **_DEBUG** indicateur est défini. Lorsque **_DEBUG** est ne pas défini, les appels à ces macros sont supprimés lors du prétraitement.

Le **_RPTW** et **_RPTFW** macros sont des versions à caractères larges de ces macros. Ils sont similaires aux **wprintf** et prennent des chaînes de caractères larges en tant qu’arguments.

Le **_RPT** macros appel le [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) fonction pour générer un rapport de débogage avec un message de l’utilisateur. Le **_RPTW** macros appel le **_CrtDbgReportW** afin de générer le même rapport avec les caractères larges. Le **_RPTF** et **_RPTFW** macros créent un rapport de débogage avec le nombre de fichiers et de la ligne source où la macro de rapport a été appelée, par ailleurs dans le message de l’utilisateur. Le message utilisateur est créé en substituant le **arg**[*n*] arguments dans le *format* chaîne, en utilisant les mêmes règles définies par le [printf](printf-printf-l-wprintf-wprintf-l.md)(fonction).

**_CrtDbgReport** ou **_CrtDbgReportW** génère le rapport de débogage et détermine sa destinations basées sur les modes de rapport actuel et le fichier défini pour *reportType*. Les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md) servent à définir les destinations de chaque type de rapport.

Si un **_RPT** macro est appelée et ni **_CrtSetReportMode** ni **_CrtSetReportFile** a été appelée, les messages sont affichés comme suit.

|Type de rapport|Destination de sortie|
|-----------------|------------------------|
|**_CRT_WARN**|Le texte d’avertissement ne s’affiche pas.|
|**_CRT_ERROR**|Fenêtre contextuelle. Comme si `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` avait été spécifié.|
|**_CRT_ASSERT**|Identique à **_CRT_ERROR**.|

Lorsque la destination est une fenêtre de message de débogage et que l’utilisateur choisit le **réessayer** bouton, **_CrtDbgReport** ou **_CrtDbgReportW** retourne 1, à l’origine de ces macros, pour démarrer le débogueur, sous réserve que le débogage juste-à-temps (JIT) est activé. Pour plus d’informations sur l’utilisation de ces macros comme mécanisme de gestion des erreurs de débogage, consultez [Utilisation de macros pour la vérification et la création de rapports](/visualstudio/debugger/macros-for-reporting).

Deux autres macros génèrent un rapport de débogage. La macro [_ASSERT](assert-asserte-assert-expr-macros.md) génère un rapport, mais seulement quand l’argument d’expression est évalué à FALSE. [_ASSERTE](assert-asserte-assert-expr-macros.md) est exactement comme **_ASSERT**, mais inclut l’expression qui a échoué dans le rapport généré.

## <a name="requirements"></a>Spécifications

|Macro|En-tête requis|
|-----------|---------------------|
|**_RPT** macros|\<crtdbg.h>|
|**_RPTF** macros|\<crtdbg.h>|
|**_RPTW** macros|\<crtdbg.h>|
|**_RPTFW** macros|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

Bien qu’il s’agisse de macros et qu’elles soient obtenues en incluant Crtdbg.h, l’application doit établir une liaison avec l’une des bibliothèques de débogage, car ces macros appellent d’autres fonctions de runtime.

## <a name="example"></a>Exemple

Consultez l’exemple présenté dans la rubrique [_ASSERT](assert-asserte-assert-expr-macros.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
