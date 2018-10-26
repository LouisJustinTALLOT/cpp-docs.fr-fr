---
title: -std (spécifier la Version de langue Standard) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2017
ms.topic: reference
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
dev_langs:
- C++
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32bbcd47c4ce22882941b6fa9c02373bab32eeb1
ms.sourcegitcommit: 938d118d02543c822a5f58c84d6119d23339e43c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135992"
---
# <a name="std-specify-language-standard-version"></a>/STD (spécifier la Version de langue Standard)

Activer prise en charge des fonctionnalités du langage C++ à partir de la version spécifiée de la norme du langage C++.

## <a name="syntax"></a>Syntaxe

> / std : [c ++ 14 | c ++ 17 | c ++ latest]

## <a name="remarks"></a>Notes

Le **/STD** option est disponible dans Visual Studio 2017 et versions ultérieures. Il est utilisé pour contrôler les fonctionnalités de langage standard est activées pendant la compilation de votre code de programmation spécifique à la version ISO C++. Cette option vous permet de désactiver la prise en charge de certaines nouvelles fonctionnalités de langage et la bibliothèque qui peut entraîner la rupture votre code existant qui est conforme à une version particulière du langage standard. Par défaut, **/std : c ++ 14** est spécifié, qui désactive les fonctionnalités de langage et bibliothèque standard trouvées dans les versions ultérieures du langage C++ standards. Utilisez **/std : c ++ 17** pour activer les fonctionnalités de spécifique à la norme C ++ 17 et le comportement. Pour activer explicitement le dernier pris en charge de compilateur et les fonctionnalités de la bibliothèque standard, utilisez **/std : c ++ dernière**.

La valeur par défaut **/std : c ++ 14** option Active l’ensemble des fonctionnalités C ++ 14 implémentées par le compilateur Visual C++. Cette option désactive la prise en charge de bibliothèque standard pour les fonctionnalités qui sont modifiées ou nouvelles dans les versions plus récentes du langage standard, à l’exception de certaines fonctionnalités C ++ 17 déjà implémentées dans les versions précédentes du compilateur Visual C++ et de compilateur. Pour éviter d’interrompre des modifications pour les utilisateurs qui ont déjà pris des dépendances sur les fonctionnalités disponibles à compter de Visual Studio 2015 Update 2, ces fonctionnalités restent activées, lorsque le **/std : c ++ 14** option est spécifiée :

- [Règles pour auto avec braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName dans les paramètres template template](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Suppression des trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Attributs pour espaces de noms et énumérateurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [littéraux de caractère U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Pour plus d’informations sur les fonctionnalités C ++ 14 et C ++ 17 sont activés lorsque **/std : c ++ 14** est spécifié, voir les notes de [Visual C++ Language Conformance](../../visual-cpp-language-conformance.md).

Le **/std : c ++ 17** option permet à l’ensemble complet des fonctionnalités C ++ 17 implémentées par le compilateur Visual C++. Cette option désactive la prise en charge par le compilateur et la bibliothèque standard des fonctionnalités modifiées ou nouvelles dans les versions de Working Draft et les mises à jour des défauts de C++ Standard postérieures à C++17.

Le **/std : c ++ dernière** option Active l’ensemble des fonctionnalités de langage et la bibliothèque C++ implémentée par Visual C++ pour suivre le plus récent C ++ 20 Working Draft et defect mises à jour de la norme C++ qui ne figurent pas dans C ++ 17. Ce commutateur permet d’obtenir le post-fonctionnalités de langage C ++ 17 prises en charge par le compilateur et la bibliothèque standard. Pour obtenir la liste des langues prises en charge et les fonctionnalités de la bibliothèque, consultez [quelles sont les nouveautés de Visual C++](../../what-s-new-for-visual-cpp-in-visual-studio.md). Le **/std : c ++ dernière** option ne permet pas de fonctionnalités protégées par le **/ expérimentale** basculer.

Le **/std** option en vigueur pendant une compilation C++ peut être détectée à l’aide de la [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) macro de préprocesseur. Pour plus d’informations, consultez [Macros de préprocesseur](../../preprocessor/predefined-macros.md).

Le **/std : c ++ 14** et **/std : c ++ dernière** options sont disponibles depuis Visual C++ 2015 Update 3. Le **/std : c ++ 17** option est disponible à compter de Visual C++ 2017 version 15.3. Comme indiqué précédemment, certaines C ++ 17 standard comportement est activé par le **/std : c ++ 14** option, mais toutes les autres fonctionnalités C ++ 17 sont activées par **/std : c ++ 17**.

> [!NOTE]
> Selon le niveau du compilateur de la Visual C++ version ou mise à jour, certaines fonctionnalités C ++ 14 ou C ++ 17 ne peuvent pas être entièrement implémentées ou entièrement conforme lorsque vous spécifiez le **/std : c ++ 14** ou **/std : c ++ 17** options. Par exemple, le compilateur Visual C++ 2017 RTM ne prend pas entièrement en charge C ++ 14 conforme à `constexpr`, l’expression SFINAE ou la recherche de nom de la phase 2. Pour une vue d’ensemble de la conformité du langage C++ dans Visual C++ en version release, consultez [Visual C++ Language Conformance](../../visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez **propriétés de Configuration**, **C/C++**, **langage**.

1. Dans **norme du langage C++**, choisissez la norme du langage à prendre en charge à partir du contrôle de liste déroulante, puis choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
