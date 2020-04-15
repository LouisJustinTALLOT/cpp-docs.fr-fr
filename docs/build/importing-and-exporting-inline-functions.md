---
title: Importation et exportation de fonctions inline
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: abb0443ab8fbd315524350caaff34e0250147ed2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328517"
---
# <a name="importing-and-exporting-inline-functions"></a>Importation et exportation de fonctions inline

Les fonctions importées peuvent être définies comme inline. L’effet est à peu près le même que la définition d’une fonction standard en ligne; les appels à la fonction sont étendus dans le code inline, un peu comme une macro. Ceci est principalement utile comme un moyen de soutenir les classes de C dans un DLL qui pourrait inlimer certaines de leurs fonctions de membre pour l’efficacité.

Une caractéristique d’une fonction en ligne importée est que vous pouvez prendre son adresse en C. Le compilateur renvoie l’adresse de la copie de la fonction en ligne résidant dans le DLL. Une autre caractéristique des fonctions inline importées est que vous pouvez initialiser les données locales statiques de la fonction importée, contrairement aux données importées à l’échelle mondiale.

> [!CAUTION]
> Vous devez faire preuve de prudence lors de la fourniture de fonctions en ligne importées, car elles peuvent créer la possibilité de conflits de version. Une fonction en ligne est étendue au code d’application; par conséquent, si vous réécrivez plus tard la fonction, elle ne se met pas à jour à moins que l’application elle-même ne soit recompilée. (Normalement, les fonctions DLL peuvent être mises à jour sans reconstruire les applications qui les utilisent.)

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exportation d’un DLL](exporting-from-a-dll.md)

- [Exportation à partir d’un DLL en utilisant . Fichiers DEF](exporting-from-a-dll-using-def-files.md)

- [Exportation d’un DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportation et importation à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Fonctions d’exportation CMD pour une utilisation dans les exécutables en langue C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Déterminer quelle méthode d’exportation utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l'aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](importing-and-exporting.md)
