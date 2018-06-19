---
title: _CrtSetReportFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3df4f54ad8e191dac7110a914bdde1cec888ff9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402336"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

Une fois que vous utilisez [_CrtSetReportMode](crtsetreportmode.md) pour spécifier **_CRTDBG_MODE_FILE**, vous pouvez spécifier le handle de fichier pour recevoir le texte du message. **_CrtSetReportFile** est également utilisé par [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) pour spécifier la destination du texte (version debug uniquement).

## <a name="syntax"></a>Syntaxe

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Paramètres

*reportType*<br/>
Type de rapport : **_CRT_WARN**, **_CRT_ERROR**, et **_CRT_ASSERT**.

*reportFile*<br/>
Nouveau fichier de rapport pour *reportType*.

## <a name="return-value"></a>Valeur de retour

Opération réussie, **_CrtSetReportFile** retourne le précédent fichier de rapport défini pour le type de rapport spécifié dans *reportType*. Si une valeur non valide est passée pour *reportType*, cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **_CRTDBG_HFILE_ERROR**. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

**_CrtSetReportFile** est utilisé avec le [_CrtSetReportMode](crtsetreportmode.md) fonction pour définir l’ou les destinations d’un type spécifique généré par **_CrtDbgReport**. Lorsque **_CrtSetReportMode** a été appelé pour affecter le **_CRTDBG_MODE_FILE** d’un type spécifique, le mode de création de rapports **_CrtSetReportFile** doit ensuite être appelé à définir le fichier spécifique ou un flux de données à utiliser comme destination. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetReportFile** sont supprimés lors du prétraitement.

La liste suivante présente les options disponibles pour *reportFile* et le comportement résultant de **_CrtDbgReport**. Ces options sont définies sous forme d’indicateurs binaires dans Crtdbg.h.

- **handle de fichier**

   Handle vers le fichier qui sera la destination des messages. Aucune tentative n’est effectuée pour vérifier la validité du handle. Vous devez ouvrir et fermer le handle vers le fichier. Par exemple :

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

   Écrit un message à **stderr**, ce qui peut être redirigé comme suit :

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Écrit un message à **stdout**, que vous pouvez rediriger.

- **_CRTDBG_REPORT_FILE**

   Retourne le mode de rapport actuel.

Le fichier de rapport utilisé par chaque type de rapport peut être contrôlé séparément. Par exemple, il est possible de spécifier qu’un *reportType* de **_CRT_ERROR** signalée à **stderr**, pendant un *reportType* de **_CRT_ASSERT** signalée à un handle de fichier défini par l’utilisateur ou un flux.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

**Bibliothèques :** uniquement les versions de débogage des [fonctions de bibliothèque CRT](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
