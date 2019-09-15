---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938460"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

Spécifie la ou les destinations pour un type de rapport spécifique généré par _ **CrtDbgReport** et toutes les macros qui appellent _ [CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md), telles que _ Assert [, _ asserte, _ASSERT_EXPR macros](assert-asserte-assert-expr-macros.md), [Assert, _ asserte, _ ASSERT_EXPR macros](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _RPTFW macros](rpt-rptf-rptw-rptfw-macros.md), et [_RPT, _RPTF, _RPTW, _RPTFW macros](rpt-rptf-rptw-rptfw-macros.md) (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type de rapport : **_CRT_WARN**, **_CRT_ERROR**et **_CRT_ASSERT**.

*reportMode*<br/>
Nouveau mode de rapport ou modes pour *reportType*.

## <a name="return-value"></a>Valeur de retour

Une fois l’opération terminée, _ **CrtSetReportMode** retourne le ou les modes de rapport précédents pour le type de rapport spécifié dans *reportType*. Si une valeur non valide est passée en tant que *reportType* ou si un mode non valide est spécifié pour *reportMode*, _ **CrtSetReportMode** appelle le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne-1. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

_ **CrtSetReportMode** spécifie la destination de sortie pour _ **CrtDbgReport**. Étant donné que les macros _ [Assert](assert-asserte-assert-expr-macros.md), _ [asserte](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md)et [_RPTF](rpt-rptf-rptw-rptfw-macros.md) appellent _ **CrtDbgReport**, _ **CrtSetReportMode** spécifie la destination de sortie du texte spécifié avec ces macros.

Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à _ **CrtSetReportMode** sont supprimés lors du prétraitement.

Si vous n’appelez pas _ **CrtSetReportMode** pour définir la destination de sortie des messages, les valeurs par défaut suivantes sont appliquées :

- Les erreurs et les échecs d’assertion sont dirigés vers une fenêtre de message de débogage.

- Les avertissements émanant des applications Windows sont envoyés à la fenêtre de sortie du débogueur.

- Les avertissements issus des applications de console ne sont pas affichés.

Le tableau suivant répertorie les types de rapport définis dans Crtdbg.h.

|Type de rapport|Description|
|-----------------|-----------------|
|**_CRT_WARN**|Avertissements, messages et informations qui ne nécessitent pas une attention immédiate.|
|**_CRT_ERROR**|Erreurs, problèmes irrécupérables et problèmes qui requièrent une attention immédiate.|
|**_CRT_ASSERT**|Échecs d’assertion (expressions déclarées qui prennent la **valeur false**).|

La fonction _ **CrtSetReportMode** affecte le nouveau mode de rapport spécifié dans *reportMode* au type de rapport spécifié dans *reportType* et retourne le mode de rapport défini précédemment pour *reportType*. Le tableau suivant répertorie les options disponibles pour *reportMode* et le comportement résultant de _ **CrtDbgReport**. Ces options sont définies sous forme d’indicateurs binaires dans Crtdbg.h.

|Mode de rapport|Comportement de _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Écrit le message dans la fenêtre de sortie du débogueur.|
|**_CRTDBG_MODE_FILE**|Écrit le message dans un handle de fichier fourni par l’utilisateur. [_CrtSetReportFile](crtsetreportfile.md) doit être appelée pour définir le flux ou fichier spécifique à utiliser comme destination.|
|**_CRTDBG_MODE_WNDW**|Crée une boîte de message pour afficher le message avec les boutons [abandonner](abort.md), **Réessayer**et **Ignorer** .|
|**_CRTDBG_REPORT_MODE**|Retourne *reportMode* pour le *reportType*spécifié :<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

Chaque type de rapport peut être signalé à l’aide d’un, deux ou trois modes ou sans aucun mode. Ainsi, plusieurs destinations peuvent être définies pour un même type de rapport. Par exemple, le fragment de code suivant entraîne l’envoi d’échecs d’assertion à la fois à une fenêtre de message de débogage et à **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

En outre, vous pouvez contrôler séparément le(s) mode(s) de création de rapports pour chaque type de rapport. Par exemple, il est possible de spécifier qu’un *reportType* de **_CRT_WARN** soit envoyé à une chaîne de débogage de sortie, tandis que **_CRT_ASSERT** est affiché à l’aide d’une fenêtre de message de débogage et envoyée à **stderr**, comme illustré précédemment.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliotheque** Versions de débogage des fonctionnalités de la [bibliothèque CRT](../../c-runtime-library/crt-library-features.md) uniquement.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
