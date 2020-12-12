---
description: 'En savoir plus sur : inclusion de noms de fichiers entre crochets'
title: Intégration des noms de fichiers entre crochets
ms.date: 11/04/2016
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
ms.openlocfilehash: e54792b5feb7d5419896641c25a4367e97d80977
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182045"
---
# <a name="including-bracketed-filenames"></a>Intégration des noms de fichiers entre crochets

**ANSI 3.8.2** Méthode utilisée pour localiser les fichiers à inclure

Pour les caractéristiques du fichier placées entre crochets pointus, le préprocesseur n'effectue pas de recherche dans les répertoires des fichiers parents. Le fichier « parent » est le fichier qui contient la directive [#include](../preprocessor/hash-include-directive-c-cpp.md). Au lieu de cela, il commence par rechercher le fichier dans les répertoires spécifiés sur la ligne de commande du compilateur située après /I. Si l'option /I est absente ou échoue, le préprocesseur utilise la variable d'environnement INCLUDE pour rechercher tous les fichiers Include entre crochets pointus. La variable d’environnement INCLUDE peut contenir plusieurs chemins séparés par des points-virgules (**;**). Si plusieurs répertoires figurent dans l'option /I ou la variable d'environnement INCLUDE, le préprocesseur les traite dans l'ordre dans lequel ils apparaissent.

## <a name="see-also"></a>Voir aussi

[Directives de prétraitement](../c-language/preprocessing-directives.md)
