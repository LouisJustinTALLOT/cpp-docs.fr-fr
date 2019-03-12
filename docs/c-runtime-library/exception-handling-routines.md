---
title: Routines de la gestion des exceptions
ms.date: 11/04/2016
f1_keywords:
- c.exceptions
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
ms.openlocfilehash: 8def356793906074e6fc4b8d7a139ce1915a5f9b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749137"
---
# <a name="exception-handling-routines"></a>Routines de la gestion des exceptions

Utilisez les fonctions de gestion des exceptions C++ pour la récupération après des événements inattendus pendant l’exécution du programme.

## <a name="exception-handling-functions"></a>Fonctions de gestion des exceptions

|Fonction|Utilisez|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Gérer les exceptions Win32 (exceptions structurées en C) comme des exceptions typées C++|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Installer votre propre routine d’arrêt qui doit être appelée par **terminate**|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Installe votre propre fonction d’arrêt qui doit être appelée par **unexpected**|
|[terminate](../c-runtime-library/reference/terminate-crt.md)|Appelé automatiquement dans certaines circonstances une fois que l’exception est levée. La fonction **terminate** appelle **abort** ou la fonction que vous spécifiez à l’aide de **set_terminate**|
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Appelle **terminate** ou la fonction que vous spécifiez à l’aide de **set_unexpected**. La fonction **unexpected** n’est pas utilisée dans l’implémentation actuelle de gestion des exceptions C++|

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
