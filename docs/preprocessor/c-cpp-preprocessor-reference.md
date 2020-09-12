---
title: Informations de référence sur le préprocesseur C/C++
description: Référence pour le préprocesseur du compilateur Microsoft C/C++ dans Visual Studio.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e53f7270a71e5e7c3f456be7d55d49eaf352aecb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040741"
---
# <a name="cc-preprocessor-reference"></a>Informations de référence sur le préprocesseur C/C++

La *Référence du préprocesseur C/C++* décrit le préprocesseur tel qu’il est implémenté dans Microsoft C/c++. Le préprocesseur exécute des opérations préliminaires sur les fichiers C et C++ avant qu'ils soient passées au compilateur. Vous pouvez utiliser le préprocesseur pour compiler du code de façon conditionnelle, insérer des fichiers, spécifier des messages d’erreur au moment de la compilation et appliquer des règles propres à l’ordinateur à des sections de code.

Dans Visual Studio 2019, l’option du compilateur de [préprocesseur/experimental :](../build/reference/experimental-preprocessor.md) active une nouvelle implémentation du préprocesseur. La nouvelle implémentation est toujours en cours et est donc considérée comme expérimentale. Il est destiné à être conforme à C99, C11 et C++ 20. Pour plus d’informations, consultez [vue d’ensemble du nouveau préprocesseur MSVC](preprocessor-experimental-overview.md).

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
