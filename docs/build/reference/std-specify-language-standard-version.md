---
title: /STD (spécifier la Version de langue Standard)
ms.date: 11/26/2018
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 32c63240f578b6170ae351cdf0cd1628167464b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317885"
---
# <a name="std-specify-language-standard-version"></a>/STD (spécifier la Version de langue Standard)

Activer prise en charge des fonctionnalités du langage C++ à partir de la version spécifiée de la norme du langage C++.

## <a name="syntax"></a>Syntaxe

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>Notes

Le **/STD** option est disponible dans Visual Studio 2017 et versions ultérieures. Il est utilisé pour contrôler les fonctionnalités de langage standard est activées pendant la compilation de votre code de programmation spécifique à la version ISO C++. Cette option vous permet de désactiver la prise en charge de certaines nouvelles fonctionnalités de langage et la bibliothèque qui peut entraîner la rupture votre code existant qui est conforme à une version particulière du langage standard. Par défaut, **/std : c ++ 14** est spécifié, qui désactive les fonctionnalités de langage et bibliothèque standard trouvées dans les versions ultérieures du langage C++ standards. Utilisez **/std : c ++ 17** pour activer les fonctionnalités de spécifique à la norme C ++ 17 et le comportement. Pour activer explicitement le compilateur actuellement implémenté et les fonctionnalités de la bibliothèque standard proposées pour le projet de norme suivant, utilisez **/std : c ++ dernière**.

La valeur par défaut **/std : c ++ 14** option Active l’ensemble des fonctionnalités C ++ 14 implémentées par le compilateur MSVC. Cette option désactive le compilateur et prise en charge de bibliothèque standard pour les fonctionnalités qui sont modifiées ou nouvelles dans les versions plus récentes du langage standard, à l’exception de certaines fonctionnalités C ++ 17 déjà implémentées dans les versions précédentes du compilateur MSVC. Pour éviter d’interrompre des modifications pour les utilisateurs qui ont déjà pris des dépendances sur les fonctionnalités disponibles à compter de Visual Studio 2015 Update 2, ces fonctionnalités restent activées, lorsque le **/std : c ++ 14** option est spécifiée :

- [Règles pour auto avec braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName dans les paramètres template template](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Suppression des trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Attributs pour espaces de noms et énumérateurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [littéraux de caractère U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Pour plus d’informations sur les fonctionnalités C ++ 14 et C ++ 17 sont activés lorsque **/std : c ++ 14** est spécifié, voir les notes de [Visual C++ Language Conformance](../../overview/visual-cpp-language-conformance.md).

Le **/std : c ++ 17** option permet à l’ensemble complet des fonctionnalités C ++ 17 implémentées par le compilateur MSVC. Cette option désactive la prise en charge par le compilateur et la bibliothèque standard des fonctionnalités modifiées ou nouvelles dans les versions de Working Draft et les mises à jour des défauts de C++ Standard postérieures à C++17.

Le **/std : c ++ dernière** option permet la publication-C ++ 17 fonctionnalités de langage et de bibliothèque actuellement implémentées dans le compilateur et les bibliothèques. Ceux-ci peuvent inclure des fonctionnalités à partir de C ++ 20 Working Draft et defect mises à jour de la norme C++ ne sont pas inclus dans C ++ 17, ainsi que des propositions expérimentales pour le projet de norme. Pour obtenir la liste des langues prises en charge et les fonctionnalités de la bibliothèque, consultez [quelles sont les nouveautés de Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). Le **/std : c ++ dernière** option ne permet pas de fonctionnalités protégées par le **/ expérimentale** basculer, mais peut être nécessaire pour leur permettre de.

> [!IMPORTANT]
> Les compilateur et la bibliothèque les fonctionnalités activées par **/std : c ++ dernière** sont fournies en tant que-est et sans prise en charge. Ils sont soumis aux modifications avec rupture ou suppression sans préavis. Ils constituent un aperçu des fonctionnalités de langage qui peuvent apparaître dans la prochaine version de la norme, mais la norme est un travail en cours. Utilisez **/std : c ++ 17** à utiliser les fonctionnalités de la toute dernière norme ISO C++.

Le **/std** option en vigueur pendant une compilation C++ peut être détectée à l’aide de la [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) macro de préprocesseur. Pour plus d’informations, consultez [Macros de préprocesseur](../../preprocessor/predefined-macros.md).

Le **/std : c ++ 14** et **/std : c ++ dernière** options sont disponibles depuis Visual C++ 2015 Update 3. Le **/std : c ++ 17** option est disponible à compter de Visual C++ 2017 version 15.3. Comme indiqué précédemment, certaines C ++ 17 standard comportement est activé par le **/std : c ++ 14** option, mais toutes les autres fonctionnalités C ++ 17 sont activées par **/std : c ++ 17**.

> [!NOTE]
> Selon le niveau du compilateur de la MSVC version ou mise à jour, certaines fonctionnalités C ++ 14 ou C ++ 17 ne peuvent pas être entièrement implémentées ou entièrement conforme lorsque vous spécifiez le **/std : c ++ 14** ou **/std : c ++ 17** options. Par exemple, le compilateur Visual C++ 2017 RTM ne prend pas entièrement en charge C ++ 14 conforme à `constexpr`, l’expression SFINAE ou la recherche de nom de la phase 2. Pour une vue d’ensemble de la conformité du langage C++ dans Visual C++ en version release, consultez [Visual C++ Language Conformance](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **propriétés de Configuration**, **C/C++**, **langage**.

1. Dans **norme du langage C++**, choisissez la norme du langage à prendre en charge à partir du contrôle de liste déroulante, puis choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
