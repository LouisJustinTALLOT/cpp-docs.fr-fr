---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942280"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

Une fois que vous avez utilisé _ [CrtSetReportMode](crtsetreportmode.md) pour spécifier **_CRTDBG_MODE_FILE**, vous pouvez spécifier le descripteur de fichier pour recevoir le texte du message. **_CrtSetReportFile** est également utilisé par _ [CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) pour spécifier la destination du texte (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type de rapport : **_CRT_WARN**, **_CRT_ERROR**et **_CRT_ASSERT**.

*reportFile*<br/>
Nouveau fichier de rapport pour *reportType*.

## <a name="return-value"></a>Valeur de retour

Une fois l’opération terminée, **_CrtSetReportFile** retourne le fichier de rapport précédent défini pour le type de rapport spécifié dans *reportType*. Si une valeur non valide est passée pour *reportType*, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **_CRTDBG_HFILE_ERROR**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

**_CrtSetReportFile** est utilisé avec la fonction _ [CrtSetReportMode](crtsetreportmode.md) pour définir la ou les destinations d’un type de rapport spécifique généré par _ **CrtDbgReport**. Lorsque _ **CrtSetReportMode** a été appelé pour affecter le mode de création de rapports **_CRTDBG_MODE_FILE** pour un type de rapport spécifique, **_CrtSetReportFile** doit ensuite être appelé pour définir le fichier ou le flux spécifique à utiliser comme destination. Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetReportFile** sont supprimés lors du prétraitement.

La liste suivante répertorie les options disponibles pour *ReportFile* et le comportement résultant de _ **CrtDbgReport**. Ces options sont définies sous forme d’indicateurs binaires dans Crtdbg.h.

- **handle de fichier**

   Handle vers le fichier qui sera la destination des messages. Aucune tentative n’est effectuée pour vérifier la validité du handle. Vous devez ouvrir et fermer le handle vers le fichier. Par exemple :

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   Écrit un message dans **stderr**, qui peut être redirigé comme suit :

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Écrit un message dans **stdout**, que vous pouvez rediriger.

- **_CRTDBG_REPORT_FILE**

   Retourne le mode de rapport actuel.

Le fichier de rapport utilisé par chaque type de rapport peut être contrôlé séparément. Par exemple, il est possible de spécifier qu’un *reportType* de **_CRT_ERROR** soit signalé à **stderr**, tandis qu’un *reportType* de **_CRT_ASSERT** être signalé à un flux ou un handle de fichier défini par l’utilisateur.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout**et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliotheque** Versions de débogage des fonctionnalités de la [bibliothèque CRT](../../c-runtime-library/crt-library-features.md) uniquement.

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
