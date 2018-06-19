---
title: Routines de gestion des exceptions │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eea92c5bfdb54b6c15ae2ae643b2d23b397a3bf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389073"
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
