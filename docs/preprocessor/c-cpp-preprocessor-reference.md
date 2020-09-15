---
title: Informations de référence sur le préprocesseur C/C++
description: Référence pour le préprocesseur du compilateur Microsoft C/C++ dans Visual Studio.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e72146d8b88f5a4bffcaaa121f6851d740ec948b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075632"
---
# <a name="cc-preprocessor-reference"></a>Informations de référence sur le préprocesseur C/C++

La *Référence du préprocesseur C/C++* décrit le préprocesseur tel qu’il est implémenté dans Microsoft C/c++. Le préprocesseur exécute des opérations préliminaires sur les fichiers C et C++ avant qu'ils soient passées au compilateur. Vous pouvez utiliser le préprocesseur pour compiler du code de façon conditionnelle, insérer des fichiers, spécifier des messages d’erreur au moment de la compilation et appliquer des règles propres à l’ordinateur à des sections de code.

Dans Visual Studio 2019, l’option de compilateur [/Zc : preprocesseur](../build/reference/zc-preprocessor.md) fournit un préprocesseur C11 et C17 entièrement conforme. Il s’agit de la valeur par défaut lorsque vous utilisez l’indicateur `/std:c11` de compilateur ou `/std:c17` .

## <a name="in-this-section"></a>Contenu de cette section

[Préprocesseur](preprocessor.md)\
Fournit une vue d’ensemble des préprocesseurs traditionnels et nouveaux.

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)\
Décrit les directives généralement utilisées pour rendre les programmes sources faciles à modifier et à compiler dans différents environnements d'exécution.

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)\
Présente les quatre opérateurs propres au préprocesseur utilisés dans le contexte de la directive `#define`.

[Macros prédéfinies](../preprocessor/predefined-macros.md)\
Présente les macros prédéfinies telles qu’elles sont spécifiées par les normes C et C++ et par Microsoft C++.

[Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
Présente les pragmas, qui permettent à chaque compilateur d’offrir des fonctionnalités propres aux ordinateurs et aux systèmes d’exploitation tout en conservant une compatibilité globale avec les langages C et C++.

## <a name="related-sections"></a>Sections connexes

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)\
Fournit des documents de référence pour l'implémentation Microsoft du langage C++.

[Référence du langage C](../c-language/c-language-reference.md)\
Fournit des documents de référence pour l'implémentation Microsoft du langage C.

[Référence de build C/C++](../build/reference/c-cpp-building-reference.md)\
Fournit des liens vers des rubriques décrivant les options du compilateur et de l'éditeur de liens.

[Projets Visual Studio-C++](../build/creating-and-managing-visual-cpp-projects.md)\
Décrit l'interface utilisateur de Visual Studio qui vous permet de spécifier les répertoires dans lesquels le système de projet effectuera ses recherches pour trouver les fichiers de votre projet C++.
