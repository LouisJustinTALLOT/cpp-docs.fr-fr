---
title: /std (Spécifier la version de la norme du langage)
ms.date: 05/16/2019
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 9bdeb92e03b3ae00258ac48a29cec42ef7e18e81
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241213"
---
# <a name="std-specify-language-standard-version"></a>/std (Spécifier la version de la norme du langage)

Activez les fonctionnalités du langage C++ prises en charge dans la version spécifiée de la norme du langage C++.

## <a name="syntax"></a>Syntaxe

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>Notes

L’option **/std** est disponible dans Visual Studio 2017 et ultérieur. Elle sert à contrôler les fonctionnalités de la norme du langage de programmation C++ spécifiques à une version ISO qui sont activées durant la compilation de votre code. Cette option vous permet de désactiver la prise en charge de certaines nouvelles fonctionnalités de langage et de bibliothèque susceptibles de casser votre code existant si celui-ci est conforme à une version particulière de la norme du langage. Spécifiée par défaut, l’option **/std:c++14** désactive les fonctionnalités de langage et de bibliothèque standard présentes dans les versions ultérieures de la norme du langage C++. Utilisez **/std:c++17** pour activer les fonctionnalités et le comportement spécifiques à la norme C++17. Pour activer explicitement les fonctionnalités de compilateur et de bibliothèque standard actuellement implémentées et figurant dans le prochain brouillon de la norme, utilisez **/std:c++latest**. Nécessitent des fonctionnalités C ++ 20 tous les **/std : c ++ dernière**; lorsque l’implémentation est terminée, un nouveau **/std : c ++ 20** option est activée.

L’option par défaut **/std:c++14** active l’ensemble des fonctionnalités C++14 implémentées par le compilateur MSVC. Cette option désactive la prise en charge par le compilateur et la bibliothèque standard des fonctionnalités qui ont été changées ou introduites dans les versions plus récentes de la norme du langage, à l’exception de certaines fonctionnalités C++17 déjà implémentées dans les versions précédentes du compilateur MSVC. Pour éviter que les utilisateurs ayant déjà créé des dépendances sur les fonctionnalités disponibles à compter de Visual Studio 2015 Update 2 ne subissent de changements cassants, ces fonctionnalités restent activées quand l’option **/std:c++14** est spécifiée :

- [Règles pour auto avec braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [typename dans template template-parameter](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Suppression des trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Attributs pour espaces de noms et énumérateurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [Littéraux de caractère u8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Pour plus d’informations sur les fonctionnalités C++14 et C++17 qui sont activées quand **/std:c++14**est spécifié, consultez les notes disponibles dans [Conformité du langage Visual C++](../../overview/visual-cpp-language-conformance.md).

L’option **/std:c++17** active l’ensemble complet des fonctionnalités C++17 implémentées par le compilateur MSVC. Cette option désactive la prise en charge par le compilateur et la bibliothèque standard des fonctionnalités modifiées ou nouvelles dans les versions de Working Draft et les mises à jour des défauts de C++ Standard postérieures à C++17.

L’option **/std:c++latest** active les fonctionnalités de bibliothèque et de langage post-C++17 actuellement implémentées dans le compilateur et les bibliothèques. Celles-ci peuvent inclure des fonctionnalités du brouillon de C++20 et des mises à jour visant à remédier aux défauts de la norme C++ qui ne figurent pas dans C++17, ainsi que des propositions expérimentales pour le brouillon de la norme. Pour obtenir la liste des fonctionnalités de langage et de bibliothèque prises en charge, consultez [Nouveautés de Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). L’option **/std:c++latest** n’active pas les fonctionnalités protégées par le commutateur **/experimental**, mais peut être tenue de les activer.

> [!IMPORTANT]
> Les fonctionnalités de compilateur et de bibliothèque activées par **/std:c++latest** représentent les fonctionnalités susceptibles d’apparaître dans une future norme C++, ainsi que les fonctionnalités C++20 approuvées. Les fonctionnalités qui n’ont pas été approuvées peuvent faire l’objet de changements cassants ou peuvent être supprimées sans préavis, et sont fournies en l’état. 

L’option **/std** en vigueur durant une compilation C++ peut être détectée au moyen de la macro de préprocesseur [\_MSVC\_LANG](../../preprocessor/predefined-macros.md). Pour plus d’informations, consultez [Macros de préprocesseur](../../preprocessor/predefined-macros.md).

Les options **/std:c++14** et **/std:c++latest** sont disponibles à compter de Visual Studio 2015 Update 3. L’option **/std:c++17** est disponible à compter de Visual Studio 2017 version 15.3. Comme indiqué ci-dessus, certains comportements de la norme C++17 sont activés par l’option **/std:c++14**, mais toutes les autres fonctionnalités C++17 sont activées par **/std:c++17**. Les fonctionnalités C++20 sont activées par **/std:latest** jusqu’à ce que l’implémentation soit terminée.

> [!NOTE]
> Selon le niveau de mise à jour ou la version du compilateur MSVC, les fonctionnalités C++17 peuvent ne pas être entièrement implémentées ou conformes quand vous spécifiez les options **/std:c++17**. Pour une vue d’ensemble de la conformité du langage C++ dans Visual C++ par version, consultez [Conformité du langage Visual C++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour obtenir des informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de configuration**, **C/C++** , **Langage**.

1. Dans **Norme du langage C++** , choisissez la norme de langage à prendre en charge dans le contrôle déroulant, puis choisissez **OK** or **Appliquer** pour enregistrer vos changements.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
