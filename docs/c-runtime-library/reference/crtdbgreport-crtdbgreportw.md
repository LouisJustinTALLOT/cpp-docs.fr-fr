---
title: _CrtDbgReport, _CrtDbgReportW | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3d42638ec36ffa98f0e6f1ed968eba39d64b9f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080192"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Génère un rapport avec un message de débogage et envoie ce rapport vers trois destinations possibles (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type de rapport : **_CRT_WARN**, **_CRT_ERROR**, et **_CRT_ASSERT**.

*filename*<br/>
Pointeur vers le nom du fichier source où l’assertion/rapport s’est produite ou **NULL**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’assertion/rapport s’est produite ou **NULL**.

*moduleName*<br/>
Pointeur vers le nom du module (.exe ou .dll) où l'assertion ou le rapport s'est produit.

*format*<br/>
Pointeur vers la chaîne de contrôle de format utilisée pour créer le message utilisateur.

*argument*<br/>
Arguments de substitution facultatifs utilisés par *format*.

## <a name="return-value"></a>Valeur de retour

Pour toutes les destinations de rapport, **_CrtDbgReport** et **_CrtDbgReportW** retourner -1 si une erreur se produit et 0 si aucune erreur est rencontrée. Cependant, quand la destination du rapport est une fenêtre de message de débogage et que l’utilisateur clique sur le bouton **Réessayer**, ces fonctions retournent 1. Si l’utilisateur clique sur le bouton **Abandonner** dans la fenêtre Message de débogage, ces fonctions sont immédiatement abandonnées et ne retournent aucune valeur.

Le [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) déboguer les macros appel **_CrtDbgReport** pour générer leur débogage rapports. Les versions à caractères larges de ces macros, ainsi que [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) et [_RPTFW](rpt-rptf-rptw-rptfw-macros.md), utilisez **_CrtDbgReportW** à générer leurs rapports de débogage. Lorsque **_CrtDbgReport** ou **_CrtDbgReportW** retourne 1, ces macros démarrent le débogueur, autant que le débogage juste-à-temps (JIT) est activé.

## <a name="remarks"></a>Notes

**_CrtDbgReport** et **_CrtDbgReportW** peut envoyer le rapport de débogage vers trois destinations différentes : un fichier de rapport de débogage, un moniteur de débogage (le débogueur Visual Studio) ou une fenêtre de message de débogage. Deux fonctions de configuration, [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md), sont utilisées pour spécifier la ou les destinations de chaque type de rapport. Ces fonctions permettent de contrôler séparément la ou les destinations de chaque type de rapport. Par exemple, il est possible de spécifier qu’un *reportType* de **_CRT_WARN** uniquement être envoyé vers le moniteur de débogage, tandis qu’un *reportType* de **_CRT_ASSERT** être envoyé à une fenêtre de message de débogage et un fichier de rapport défini par l’utilisateur.

**_CrtDbgReportW** est la version à caractères larges de **_CrtDbgReport**. Tous ses paramètres de sortie et de chaîne se trouvent dans des chaînes à caractères larges ; sinon, il est identique à la version à caractères codés sur un octet.

**_CrtDbgReport** et **_CrtDbgReportW** créer le message de l’utilisateur pour le rapport de débogage en substituant le *argument*[**n**] arguments dans le *format* de chaîne, à l’aide des mêmes règles définies par le **printf** ou **wprintf** fonctions. Ces fonctions, puis génèrent le rapport de débogage et déterminent l’ou les destinations, en fonction des modes de rapport actuel et le fichier définis pour *reportType*. Lorsque le rapport est envoyé vers une fenêtre de message de débogage, le *filename*, **lineNumber**, et *moduleName* sont inclus dans les informations affichées dans la fenêtre.

Le tableau suivant répertorie les options disponibles pour le mode de rapport ou les modes et les fichiers et le comportement résultant de **_CrtDbgReport** et **_CrtDbgReportW**. Ces options sont définies sous forme d’indicateurs binaires dans \<crtdbg.h>.

|Mode de rapport|Fichier de rapport|**_CrtDbgReport**, **_CrtDbgReportW** comportement|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Non applicable|Écrit un message à l’aide de l’API Windows [OutputDebugString](https://msdn.microsoft.com/library/windows/desktop/aa363362.aspx).|
|**_CRTDBG_MODE_WNDW**|Non applicable|Appelle l’API Windows [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) pour créer une boîte de message et afficher le message avec des boutons **Abandonner**, **Réessayer** et **Ignorer**. Si un utilisateur clique sur **abandonner**, **_CrtDbgReport** ou **_CrtDbgReport** abandonne immédiatement l’opération. Si un utilisateur clique sur **Réessayer**, la valeur 1 est retournée. Si un utilisateur clique sur **ignorer**, l’exécution se poursuit et **_CrtDbgReport** et **_CrtDbgReportW** retournent 0. Notez que le fait de cliquer sur **Ignorer** alors qu’il existe une condition d’erreur entraîne souvent un « comportement indéfini ».|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Écrit un message fourni par l’utilisateur **gérer**, à l’aide de la Windows [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) API et ne vérifie pas la validité du handle de fichier ; l’application est chargée d’ouvrir le fichier de rapport et de passage d’un fichier valid handle.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Écrit un message **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Écrit un message **stdout**.|

Le rapport peut être envoyé à une, deux ou trois destinations ou à aucune. Pour plus d’informations sur la spécification du ou des modes de rapport et du fichier de rapport, consultez les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md). Pour plus d’informations sur l’utilisation des macros de débogage et des fonctions de création de rapports, consultez [Macros pour la création de rapports](/visualstudio/debugger/macros-for-reporting).

Si votre application a besoin de davantage de flexibilité que celle fournie par **_CrtDbgReport** et **_CrtDbgReportW**, vous pouvez écrire votre propre création de rapports fonction et la raccorder dans la déclaration de bibliothèque Runtime C mécanisme à l’aide de la [_CrtSetReportHook](crtsetreporthook.md) (fonction).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** et **_CrtDbgReportW** sont des extensions Microsoft. Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

Consultez [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) pour obtenir un exemple de la façon de modifier la fonction de rapport.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
