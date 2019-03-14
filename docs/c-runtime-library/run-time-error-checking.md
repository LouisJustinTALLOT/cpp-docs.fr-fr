---
title: Vérifications des erreurs d’exécution
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: ec07b9b0c6aa52187c3c24bff4cc51712dbf9fc8
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746459"
---
# <a name="run-time-error-checking"></a>Vérifications des erreurs d’exécution

La bibliothèque Runtime C contient les fonctions qui prennent en charge les vérifications d’erreurs d’exécution (RTC). La vérification des erreurs d’exécution vous permet de générer votre programme afin que certains types d’erreurs d’exécution soient signalés. Vous spécifiez la façon dont les erreurs sont signalées et les types d’erreurs qui doivent l’être. Pour plus d'informations, voir [Procédure : utiliser les vérifications natives à l’exécution](/visualstudio/debugger/how-to-use-native-run-time-checks).

Utilisez les fonctions suivantes pour personnaliser la façon dont votre programme effectue la vérification des erreurs d’exécution.

## <a name="run-time-error-checking-functions"></a>Fonctions de vérification des erreurs d’exécution

|Fonction|Utilisez|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Retourne une brève description d’un type de vérification des erreurs d’exécution.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Retourne le nombre total d’erreurs pouvant être détectées par les vérifications d’erreurs d’exécution.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Désigne une fonction comme gestionnaire de rapport pour les vérifications d’erreurs d’exécution.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Associe une erreur détectée par les vérifications d’erreurs d’exécution à un type.|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (Vérifications des erreurs au moment de l’exécution)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Routines de débogage](../c-runtime-library/debug-routines.md)<br/>
