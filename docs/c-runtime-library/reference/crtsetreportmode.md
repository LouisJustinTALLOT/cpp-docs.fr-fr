---
title: _CrtSetReportMode
ms.date: 11/04/2016
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: 2096d39a8ba316fc76c97517a16e34231940e7f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335293"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

Spécifie l’ou les destinations d’un type de rapport spécifique généré par **_CrtDbgReport** et toutes les macros qui appellent [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md), tel que [_ASSERT, _ASSERTE, _ASSERT_EXPR (macros)](assert-asserte-assert-expr-macros.md), [_ASSERT, _ASSERTE, _ASSERT_EXPR (Macros)](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _RPTFW (Macros)](rpt-rptf-rptw-rptfw-macros.md), et [_RPT, _RPTF, _RPTW, _RPTFW, Macros](rpt-rptf-rptw-rptfw-macros.md) (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type de rapport : **_CRT_WARN**, **_CRT_ERROR**, et **_CRT_ASSERT**.

*reportMode*<br/>
Nouveau mode de rapport ou des modes de *reportType*.

## <a name="return-value"></a>Valeur de retour

Opération réussie, **_CrtSetReportMode** retourne l’ou les modes rapport précédente pour le type de rapport spécifié dans *reportType*. Si une valeur non valide est transmise comme *reportType* ou un mode non valide est spécifié pour *reportMode*, **_CrtSetReportMode** appelle le Gestionnaire de paramètre non valide en tant que décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne -1. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

**_CrtSetReportMode** spécifie la destination de sortie pour **_CrtDbgReport**. Étant donné que les macros [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md), et [_RPTF](rpt-rptf-rptw-rptfw-macros.md) appeler **_CrtDbgReport**, **_CrtSetReportMode** spécifie la destination de sortie du texte spécifié avec ces macros.

Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetReportMode** sont supprimés lors du prétraitement.

Si vous n’appelez pas **_CrtSetReportMode** pour définir la destination de sortie des messages, puis les valeurs par défaut suivantes sont appliquées :

- Les erreurs et les échecs d’assertion sont dirigés vers une fenêtre de message de débogage.

- Les avertissements émanant des applications Windows sont envoyés à la fenêtre de sortie du débogueur.

- Les avertissements issus des applications de console ne sont pas affichés.

Le tableau suivant répertorie les types de rapport définis dans Crtdbg.h.

|Type de rapport|Description|
|-----------------|-----------------|
|**_CRT_WARN**|Avertissements, messages et informations qui ne nécessitent pas une attention immédiate.|
|**_CRT_ERROR**|Erreurs, problèmes irrécupérables et problèmes qui requièrent une attention immédiate.|
|**_CRT_ASSERT**|Échecs d’assertion (expressions déclarées évaluées à **FALSE**).|

Le **_CrtSetReportMode** fonction assigne le nouveau mode de rapport spécifié dans *reportMode* pour le type de rapport spécifié dans *reportType* et retourne le précédemment défini mode de rapport pour *reportType*. Le tableau suivant répertorie les options disponibles pour *reportMode* et le comportement résultant de **_CrtDbgReport**. Ces options sont définies sous forme d’indicateurs binaires dans Crtdbg.h.

|Mode de rapport|Comportement de _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Écrit le message dans la fenêtre de sortie du débogueur.|
|**_CRTDBG_MODE_FILE**|Écrit le message dans un handle de fichier fourni par l’utilisateur. [_CrtSetReportFile](crtsetreportfile.md) doit être appelée pour définir le flux ou fichier spécifique à utiliser comme destination.|
|**_CRTDBG_MODE_WNDW**|Crée une boîte de message pour afficher le message avec le [abandonner](abort.md), **de nouvelle tentative**, et **ignorer** boutons.|
|**_CRTDBG_REPORT_MODE**|Retourne *reportMode* spécifié *reportType*:<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

Chaque type de rapport peut être signalé à l’aide d’un, deux ou trois modes ou sans aucun mode. Ainsi, plusieurs destinations peuvent être définies pour un même type de rapport. Par exemple, le fragment de code suivant provoque des échecs d’assertion à envoyer vers les deux une fenêtre de message de débogage et en **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

En outre, vous pouvez contrôler séparément le(s) mode(s) de création de rapports pour chaque type de rapport. Par exemple, il est possible de spécifier qu’un *reportType* de **_CRT_WARN** être envoyé à une chaîne de débogage de sortie, tandis que **_CRT_ASSERT** être affichées à l’aide d’une fenêtre de message de débogage et envoyées à **stderr**, comme illustré précédemment.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** Les versions Debug de [fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md) uniquement.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
