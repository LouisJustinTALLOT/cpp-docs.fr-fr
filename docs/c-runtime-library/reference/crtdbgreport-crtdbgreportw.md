---
title: _CrtDbgReport, _CrtDbgReportW
ms.date: 11/04/2016
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
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: b5579a8996950c5f3e923f67ed2a5e667bb566fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500000"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

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
Type de rapport: **_CRT_WARN**, **_CRT_ERROR**et **_CRT_ASSERT**.

*filename*<br/>
Pointeur vers le nom du fichier source où l’assertion/rapport s’est produit ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’assertion/rapport s’est produit ou **null**.

*moduleName*<br/>
Pointeur vers le nom du module (.exe ou .dll) où l'assertion ou le rapport s'est produit.

*format*<br/>
Pointeur vers la chaîne de contrôle de format utilisée pour créer le message utilisateur.

*argument*<br/>
Arguments de substitution facultatifs utilisés par le *format*.

## <a name="return-value"></a>Valeur de retour

Pour toutes les destinations de rapport, _ **CrtDbgReport** et **_CrtDbgReportW** retournent-1 si une erreur se produit et 0 si aucune erreur n’est rencontrée. Cependant, quand la destination du rapport est une fenêtre de message de débogage et que l’utilisateur clique sur le bouton **Réessayer**, ces fonctions retournent 1. Si l’utilisateur clique sur le bouton **Abandonner** dans la fenêtre Message de débogage, ces fonctions sont immédiatement abandonnées et ne retournent aucune valeur.

Les macros de débogage [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) appellent _ **CrtDbgReport** pour générer leurs rapports de débogage. Les versions à caractères larges de ces macros, ainsi que _ Assert [,](assert-asserte-assert-expr-macros.md)_ asserte, [_RPTW](rpt-rptf-rptw-rptfw-macros.md) et [_RPTFW](rpt-rptf-rptw-rptfw-macros.md), utilisent **_CrtDbgReportW** pour générer leurs rapports de débogage. Quand _ **CrtDbgReport** ou **_CrtDbgReportW** retourne 1, ces macros démarrent le débogueur, à condition que le débogage juste-à-temps (JIT) soit activé.

## <a name="remarks"></a>Notes

_ **CrtDbgReport** et **_CrtDbgReportW** peuvent envoyer le rapport de débogage vers trois destinations différentes: un fichier de rapport de débogage, un moniteur de débogage (le débogueur Visual Studio) ou une fenêtre de message de débogage. Deux fonctions de configuration, [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md), sont utilisées pour spécifier la ou les destinations de chaque type de rapport. Ces fonctions permettent de contrôler séparément la ou les destinations de chaque type de rapport. Par exemple, il est possible de spécifier qu’un *reportType* de **_CRT_WARN** est envoyé à l’analyse de débogage uniquement, tandis qu’un *reportType* de **_CRT_ASSERT** être envoyé à une fenêtre de message de débogage et à un fichier de rapport défini par l’utilisateur.

**_CrtDbgReportW** est la version à caractères larges de _ **CrtDbgReport**. Tous ses paramètres de sortie et de chaîne se trouvent dans des chaînes à caractères larges ; sinon, il est identique à la version à caractères codés sur un octet.

_ **CrtDbgReport** et **_CrtDbgReportW** créent le message utilisateur pour le rapport de débogage en substituant l' *argument*[**n**] arguments dans la chaîne de *format* , à l’aide des mêmes règles définies par **printf** ou  **wprintf** , fonctions. Ces fonctions génèrent ensuite le rapport de débogage et déterminent la ou les destinations en fonction des modes de rapport et du fichier définis pour *reportType*. Quand le rapport est envoyé à une fenêtre de message de débogage, les *noms*de fichiers, **LineNumber**et *modulename* sont inclus dans les informations affichées dans la fenêtre.

Le tableau suivant répertorie les options disponibles pour le ou les modes de rapport et le fichier et le comportement résultant de _ **CrtDbgReport** et **_CrtDbgReportW**. Ces options sont définies sous forme d’indicateurs binaires dans \<crtdbg.h>.

|Mode de rapport|Fichier de rapport|**_CrtDbgReport**, **_CrtDbgReportW** behavior|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Non applicable|Écrit un message à l’aide de l’API Windows [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw).|
|**_CRTDBG_MODE_WNDW**|Non applicable|Appelle l’API Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) pour créer une boîte de message et afficher le message avec des boutons **Abandonner**, **Réessayer** et **Ignorer**. Si un utilisateur clique sur **abandonner**, _ **CrtDbgReport** ou _ **CrtDbgReport** est immédiatement abandonné. Si un utilisateur clique sur **Réessayer**, la valeur 1 est retournée. Si un utilisateur clique sur **Ignorer**, l’exécution se poursuit et _ **CrtDbgReport** et **_CrtDbgReportW** retournent 0. Notez que le fait de cliquer sur **Ignorer** alors qu’il existe une condition d’erreur entraîne souvent un « comportement indéfini ».|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Écrit un message dans un **handle**fourni par l’utilisateur, à l’aide de l’API Windows [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) et ne vérifie pas la validité du descripteur de fichier. l’application est chargée d’ouvrir le fichier de rapport et de passer un handle de fichier valide.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Écrit un message dans **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Écrit un message dans **stdout**.|

Le rapport peut être envoyé à une, deux ou trois destinations ou à aucune. Pour plus d’informations sur la spécification du ou des modes de rapport et du fichier de rapport, consultez les fonctions [_CrtSetReportMode](crtsetreportmode.md) et [_CrtSetReportFile](crtsetreportfile.md). Pour plus d’informations sur l’utilisation des macros de débogage et des fonctions de création de rapports, consultez [Macros pour la création de rapports](/visualstudio/debugger/macros-for-reporting).

Si votre application a besoin d’une plus grande flexibilité que celle fournie par _ **CrtDbgReport** et **_CrtDbgReportW**, vous pouvez écrire votre propre fonction de création de rapports et la raccorder au mécanisme de création de rapports de la bibliothèque Runtime C à l’aide de _ [crtsetreporthook](crtsetreporthook.md) fonctionnalités.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

_ **CrtDbgReport** et **_CrtDbgReportW** sont des extensions Microsoft. Pour plus d'informations, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
