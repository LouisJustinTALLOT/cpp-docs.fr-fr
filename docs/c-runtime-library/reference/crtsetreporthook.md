---
description: 'En savoir plus sur : _CrtSetReportHook'
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 1e99e17b3a245dfe78e5a0f7367e422f4dc97600
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342242"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

Installe une fonction de création de rapports définie par le client en la raccordant au processus de création de rapports de débogage du runtime C (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Paramètres

*reportHook*<br/>
Nouvelle fonction de création de rapports définie par le client à raccorder au processus de création de rapports de débogage du runtime C.

## <a name="return-value"></a>Valeur renvoyée

Retourne la fonction de création de rapports précédente définie par le client.

## <a name="remarks"></a>Notes

**_CrtSetReportHook** permet à une application d’utiliser sa propre fonction de création de rapports dans le processus de création de rapports de la bibliothèque de débogage du runtime C. Ainsi, chaque fois que [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) est appelé pour générer un rapport de débogage, la fonction de création de rapports de l’application est appelée en premier. Cette fonctionnalité permet à une application d’effectuer des opérations telles que le filtrage des rapports de débogage pour qu’elle puisse se concentrer sur des types d’allocation spécifiques ou envoyer un rapport à des destinations non disponibles à l’aide de **_CrtDbgReport**. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetReportHook** sont supprimés lors du prétraitement.

Pour obtenir une version plus robuste de **_CrtSetReportHook**, consultez [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md).

La fonction **_CrtSetReportHook** installe la nouvelle fonction de création de rapports définie par le client spécifiée dans *reportHook* et retourne le hook défini par le client précédent. L’exemple suivant montre comment un raccordement de rapport défini par le client doit être prototypé :

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

où *reportType* est le type de rapport de débogage (**_CRT_WARN**, **_CRT_ERROR** ou **_CRT_ASSERT**), *message* est le message utilisateur de débogage entièrement assemblé à contenir dans le rapport, et **returnValue** est la valeur spécifiée par la fonction de création de rapports définie par le client qui doit être retournée par **_CrtDbgReport**. Pour obtenir une description complète des types de rapports disponibles, consultez la fonction [_CrtSetReportMode](crtsetreportmode.md).

Si la fonction de création de rapports définie par le client gère complètement le message de débogage de sorte qu’aucun autre rapport n’est requis, la fonction doit retourner la **valeur true**. Quand la fonction retourne **false**, **_CrtDbgReport** est appelé pour générer le rapport de débogage à l’aide des paramètres actuels pour le type de rapport, le mode et le fichier. En outre, en spécifiant la valeur de retour **_CrtDbgReport** dans **returnValue**, l’application peut également contrôler si une interruption de débogage se produit. Pour obtenir une description complète de la façon dont le rapport de débogage est configuré et généré, consultez **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md)et **_CrtDbgReport**.

Pour plus d’informations sur l’utilisation d’autres fonctions d’exécution compatibles avec le raccordement et sur l’écriture de vos propres fonctions de raccordement définies par le client, consultez [Écriture de fonctions de raccordement de débogage](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Si votre application est compilée avec **/CLR** et que la fonction de création de rapports est appelée une fois que l’application a quitté main, le CLR lève une exception si la fonction de création de rapports appelle des fonctions CRT.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
