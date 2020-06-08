---
title: /std (Spécifier la version de la norme du langage)
ms.date: 06/04/2020
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: ddb0fc9ad4880ed317a28d7aec5eba1669eabbc5
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507064"
---
# <a name="std-specify-language-standard-version"></a>/std (Spécifier la version de la norme du langage)

Activez les fonctionnalités du langage C++ prises en charge dans la version spécifiée de la norme du langage C++.

## <a name="syntax"></a>Syntaxe

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**]

## <a name="remarks"></a>Remarques

L' **`/std`** option est disponible dans Visual Studio 2017 et versions ultérieures. Il est utilisé pour contrôler les fonctionnalités standard du langage de programmation ISO C++ spécifiques à la version qui sont activées pendant la compilation de votre code. Cette option vous permet de désactiver la prise en charge de certaines nouvelles fonctionnalités de langage et de bibliothèque : celles qui peuvent endommager votre code existant qui est conforme à une version particulière de la norme du langage. Par défaut, **`/std:c++14`** est spécifié, ce qui désactive les fonctionnalités de la bibliothèque de langue et de la bibliothèque standard qui se trouvent dans les versions ultérieures de la norme du langage C++. Utilisez **`/std:c++17`** pour activer les fonctionnalités et le comportement spécifiques à c++ 17. Pour activer explicitement le compilateur actuellement implémenté et les fonctionnalités de la bibliothèque standard proposées pour la prochaine ébauche standard, utilisez **`/std:c++latest`** . Toutes les fonctionnalités C++ 20 requièrent **`/std:c++latest`** ; lorsque l’implémentation est terminée, une nouvelle **`/std:c++20`** option est activée.

L’option par défaut **`/std:c++14`** active l’ensemble des fonctionnalités c++ 14 implémentées par le compilateur MSVC. Cette option désactive la prise en charge du compilateur et de la bibliothèque standard pour les fonctionnalités modifiées ou nouvelles dans les versions plus récentes de la norme du langage. Elle ne désactive pas certaines fonctionnalités C++ 17 déjà implémentées dans les versions précédentes du compilateur MSVC. Pour éviter les modifications avec rupture pour les utilisateurs qui ont déjà pris des dépendances sur les fonctionnalités disponibles dans ou avant Visual Studio 2015 Update 2, ces fonctionnalités restent activées lorsque l' **`/std:c++14`** option est spécifiée :

- [Règles pour auto avec braced-init-lists](https://wg21.link/n3922)

- [typename dans template template-parameter](https://wg21.link/n4051)

- [Suppression des trigraphes](https://wg21.link/n4086)

- [Attributs pour espaces de noms et énumérateurs](https://wg21.link/n4266)

- [Littéraux de caractère u8](https://wg21.link/n4267)

Liste des fonctionnalités C++ 14 et C++ 17 qui sont activées lorsque vous spécifiez **`/std:c++14`** est disponible. Pour plus d’informations, consultez les notes dans la [table de conformité du langage Microsoft C++](../../overview/visual-cpp-language-conformance.md).

L' **`/std:c++17`** option active le jeu complet de fonctionnalités c++ 17 implémentées par le compilateur MSVC. Cette option désactive la prise en charge du compilateur et de la bibliothèque standard pour les fonctionnalités nouvelles ou modifiées après C++ 17. Cela comprend les modifications postérieures à C + + 17 dans les versions du brouillon de travail et les mises à jour de défauts de la norme C++.

L' **`/std:c++latest`** option active les fonctionnalités de la bibliothèque et du langage postérieurs à C + + 17 actuellement implémentées dans le compilateur et les bibliothèques. Ces fonctionnalités peuvent inclure des modifications du brouillon de travail C++ 20, des mises à jour de défauts qui ne sont pas incluses dans C++ 17 et des propositions expérimentales pour la norme préliminaire. Pour obtenir la liste des fonctionnalités de langage et de bibliothèque prises en charge, consultez [Nouveautés de Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). L' **`/std:c++latest`** option n’active pas les fonctionnalités protégées par le **`/experimental`** commutateur, mais peut être nécessaire pour les activer.

> [!IMPORTANT]
> Les fonctionnalités du compilateur et de la bibliothèque activées par **`/std:c++latest`** représentent des fonctionnalités qui peuvent apparaître dans une future norme c++, ainsi que des fonctionnalités c++ 20 qui sont approuvées. Les fonctionnalités qui n’ont pas été approuvées peuvent faire l’objet de changements cassants ou peuvent être supprimées sans préavis, et sont fournies en l’état.

L' **`/std`** option en vigueur au cours d’une compilation C++ peut être détectée à l’aide de la macro de préprocesseur [ \_ MSVC \_ lang](../../preprocessor/predefined-macros.md) . Pour plus d’informations, consultez [Macros de préprocesseur](../../preprocessor/predefined-macros.md).

Les **`/std:c++14`** **`/std:c++latest`** options et sont disponibles à partir de la mise à jour 3 de Visual Studio 2015. L' **`/std:c++17`** option est disponible à partir de Visual Studio 2017 version 15,3. Comme indiqué ci-dessus, certains comportements standard C++ 17 sont activés par l' **`/std:c++14`** option, mais toutes les autres fonctionnalités c++ 17 sont activées par **`/std:c++17`** . Les fonctionnalités c++ 20 sont activées par **`/std:c++latest`** jusqu’à ce que l’implémentation soit terminée.

> [!NOTE]
> Selon la version du compilateur MSVC ou le niveau de mise à jour, les fonctionnalités C++ 17 peuvent ne pas être entièrement implémentées ou entièrement conformes lorsque vous spécifiez les **`/std:c++17`** options. Pour obtenir une vue d’ensemble de la conformité du langage C++ dans Visual C++ par version Release, consultez [table de conformité du langage Microsoft c++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de configuration**, **C/C++**, **Langage**.

1. Dans **Norme du langage C++**, choisissez la norme de langage à prendre en charge dans le contrôle déroulant, puis choisissez **OK** or **Appliquer** pour enregistrer vos changements.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
