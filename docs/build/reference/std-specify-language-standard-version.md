---
title: /std (Spécifier la version de la norme du langage)
description: L’option de compilateur MSVC/STD spécifie la norme du langage C ou C++ prise en charge par le compilateur.
ms.date: 10/29/2020
f1_keywords:
- /std
- -std
- /std:c++14
- /std:c++17
- /std:c11
- /std:c17
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 208789071ff028107d3c7311c3b5c6cf3eea7c1d
ms.sourcegitcommit: 4abc6c4c9694f91685cfd77940987e29a51e3143
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238471"
---
# <a name="std-specify-language-standard-version"></a>`/std` (Spécifier la version du langage standard)

Activez les fonctionnalités du langage C et C++ prises en charge à partir de la version spécifiée de la norme du langage C ou C++.

## <a name="syntax"></a>Syntaxe

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**\
> **`/std:c11`**\
> **`/std:c17`**

## <a name="remarks"></a>Notes

L' **`/std`** option est disponible dans Visual Studio 2017 et versions ultérieures. Il est utilisé pour contrôler les fonctionnalités standard du langage de programmation ISO C ou C++ spécifiques à la version qui sont activées pendant la compilation de votre code. Cette option vous permet de désactiver la prise en charge de certaines nouvelles fonctionnalités de langage et de bibliothèque : celles qui peuvent endommager votre code existant qui est conforme à une version particulière de la norme du langage.

### <a name="c-standards-support"></a>Prise en charge des normes C++

Par défaut, **`/std:c++14`** est spécifié, ce qui désactive les fonctionnalités de la bibliothèque de langue et de la bibliothèque standard qui se trouvent dans les versions ultérieures de la norme du langage C++. Utilisez  **`/std:c++17`** pour activer les fonctionnalités et le comportement spécifiques à c++ 17. Pour activer explicitement le compilateur actuellement implémenté et les fonctionnalités de la bibliothèque standard proposées pour la prochaine ébauche standard, utilisez **`/std:c++latest`** . Toutes les fonctionnalités C++ 20 requièrent **`/std:c++latest`** ; lorsque l’implémentation est terminée, une nouvelle **`/std:c++20`** option est activée.

L’option par défaut **`/std:c++14`** active l’ensemble des fonctionnalités c++ 14 implémentées par le compilateur MSVC. Cette option désactive la prise en charge du compilateur et de la bibliothèque standard pour les fonctionnalités modifiées ou nouvelles dans les versions plus récentes de la norme du langage. Elle ne désactive pas certaines fonctionnalités C++ 17 déjà implémentées dans les versions précédentes du compilateur MSVC. Pour éviter les modifications avec rupture pour les utilisateurs qui ont déjà pris des dépendances sur les fonctionnalités disponibles dans ou avant Visual Studio 2015 Update 2, ces fonctionnalités restent activées lorsque l' **`/std:c++14`** option est spécifiée :

- [Règles pour `auto` avec accolades-init-lists](https://wg21.link/n3922)

- [`typename` dans le modèle template-Parameters](https://wg21.link/n4051)

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

### <a name="c-standards-support"></a>Prise en charge des normes C

Par défaut, lorsque le code est compilé en tant que C, le compilateur MSVC n’est pas conforme à une norme C particulière. Il implémente ANSI C89 avec plusieurs extensions Microsoft, dont certaines font partie d’ISO C99. Certaines extensions Microsoft peuvent être désactivées à l’aide de l' [`/Za`](za-ze-disable-language-extensions.md) option du compilateur, mais d’autres restent en vigueur. Il n’est pas possible de spécifier la conformité stricte C89.

À compter de Visual Studio 2019 version 16,8, vous pouvez spécifier **`/std:c11`** ou **`/std:c17`** pour le code compilé en tant que C. Ces options spécifient les modes de conformité qui correspondent aux normes ISO C11 et ISO C17. Étant donné que le nouveau préprocesseur est nécessaire pour prendre en charge ces normes, les **`/std:c11`** Options du compilateur et permettent de **`/std:c17`** définir l' [`/Zc:preprocessor`](zc-preprocessor.md) option automatiquement. Si vous souhaitez utiliser le préprocesseur traditionnel (hérité) pour C11 ou C17, vous devez définir l’option de **`/Zc:preprocessor-`** compilateur explicitement. La définition de l' **`/Zc:preprocessor-`** option peut entraîner un comportement inattendu et n’est pas recommandée.

> [!NOTE]
> Au moment de la publication, les dernières bibliothèques SDK Windows et UCRT ne prennent pas encore en charge le code C11 et C17. Une version préliminaire des SDK Windows et UCRT est requise. Pour plus d’informations et pour obtenir des instructions d’installation, consultez [install C11 and C17 support in Visual Studio](../../overview/install-c17-support.md).

Lorsque vous spécifiez **`/std:c11`** ou **`/std:c17`** , MSVC prend en charge toutes les fonctionnalités requises de C11 et C17. Les options du compilateur activent la prise en charge de ces fonctionnalités :

- [`_Pragma`](../../preprocessor/pragma-directives-and-the-pragma-keyword.md#the-_pragma-preprocessing-operator-c99-c11)

- **`restrict`**

- **`_Noreturn`** les \<stdnoreturn.h>

- **`_Alignas`** , **`_Alignof`** et \<stdalign.h>

- **`_Generic`** les \<tgmath.h>

- **`_Static_assert`**

L’IDE utilise les paramètres C pour IntelliSense et la mise en surbrillance du code lorsque vos fichiers sources ont une *`.c`* extension de fichier ou lorsque vous spécifiez l' [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) option de compilateur. Actuellement, la mise en surbrillance IntelliSense n’est disponible que pour les mots clés, et non pour les macros introduites par les en-têtes standard.

Étant donné que C17 est en grande partie une version de correctif de bogue ISO C11, la prise en charge de MSVC pour C11 comprend déjà tous les rapports d’erreurs appropriés. À l’heure actuelle, il n’existe aucune différence entre les versions C11 et C17, à l’exception de la `__STDC_VERSION__` macro. Il se développe à `201112L` pour C11 et `201710L` pour C17.

Le compilateur ne prend pas en charge les fonctionnalités facultatives de la norme ISO C11. Plusieurs de ces fonctionnalités facultatives de C11 étaient des fonctionnalités requises de C99 que MSVC n’a pas implémentées pour des raisons architecturales. Vous pouvez utiliser les macros de test de fonctionnalité comme `__STDC_NO_VLA__` pour détecter les niveaux de prise en charge du compilateur pour les fonctionnalités individuelles. Pour plus d’informations sur les macros prédéfinies spécifiques à C, consultez [macros prédéfinies](../../preprocessor/predefined-macros.md).

- Il n’existe pas de prise en charge du multithreading, atomique ou complexe dans la version 16,8 de Visual Studio 2019.

- `aligned_alloc` la prise en charge est manquante, en raison de l’implémentation du tas Windows. L’alternative consiste à utiliser [`_aligned_malloc`](../../c-runtime-library/reference/aligned-malloc.md) .

- La prise en charge de la récupération d’urgence 400 est actuellement désactivée pour `realloc` , car cette modification rompt l’Abi.

- La prise en charge du tableau de longueur variable (VLA) n’est pas planifiée. Les tableaux de longueur variable sont souvent moins efficaces que les tableaux de taille fixe comparables. Elles sont également inefficaces par rapport aux allocations de mémoire de tas équivalentes, si elles sont implémentées en toute sécurité et en toute sécurité. VLAs fournissent des vecteurs d’attaque comparables à `gets()` , qui est déconseillé et planifié pour la suppression.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de configuration** , **C/C++** , **Langage** .

1. Dans la **norme du langage C++** (ou pour c, **norme du langage c** ), choisissez la norme du langage à prendre en charge dans le contrôle de liste déroulante, puis cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
