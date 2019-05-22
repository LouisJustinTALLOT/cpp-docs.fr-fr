---
title: Tableau de conformité du langage Microsoft C++
ms.date: 05/19/2019
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: c36256988e2698cb6f04e0ab71dbf6211b596033
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934169"
---
# <a name="microsoft-c-language-conformance-table"></a>Tableau de conformité du langage Microsoft C++

Cette rubrique récapitule la conformité aux normes de langage ISO C++03, C++11, C++14, C++17 et C++20 des fonctionnalités du compilateur et des fonctions de la bibliothèque standard pour le compilateur Microsoft C++ dans Visual Studio 2019 et versions antérieures. À chaque nom de fonctionnalité du compilateur et de la bibliothèque standard correspond un lien vers le document de proposition de norme ISO C++ qui décrit la fonctionnalité en question (sous réserve de disponibilité de ce document au moment de la publication). La colonne Prise en charge indique la première version de Visual Studio à prendre en charge la fonctionnalité.

Pour plus d’informations sur les améliorations de la conformité et les autres changements dans Visual Studio 2017 ou Visual Studio 2019, définissez le sélecteur de version dans le coin supérieur gauche de cette page, puis consultez [Améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md) et [Nouveautés de Visual C++ dans Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Pour passer en revue les changements de conformité dans les versions antérieures, consultez [Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md) et [Nouveautés de Visual C++ entre 2003 et 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Pour connaître l’actualité de l’équipe C++, visitez le [blog de l’équipe C++](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Aucun changement binaire cassant n’a été effectué entre Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019.

## <a name="compiler-features"></a>Fonctionnalités du compilateur

|Domaine de fonctionnalités| |
|----|---|
|__Fonctionnalités du langage principal C++03/11__|__Prise en charge__|
|&nbsp;&nbsp;Tout le reste|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Recherche de noms en deux phases|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 SFINAE sur les expressions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 Préprocesseur C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Partiel <sup>[C](#note_C)</sup>|
|__Fonctionnalités du langage principal C++14__|__Prise en charge__|
|&nbsp;&nbsp;[N3323 Formulation optimisée pour les conversions contextuelles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 Littéraux binaires](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 Types de retour auto et decltype(auto)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init-captures](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 Expressions lambda génériques](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 \[\[attribut\]\] déconseillé](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Désallocation dimensionnée](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 Séparateurs de chiffres](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 Modèles de variables](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 Fonctions constexpr étendues](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017 15.0|
|&nbsp;&nbsp;[N3653 Initialiseurs de membres par défaut pour les agrégats](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017 15.0|
|__C++17 Fonctionnalités du langage principal C++17__|__Prise en charge__|
|&nbsp;&nbsp;[N4086 Suppression des trigraphes](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 Nouvelles règles pour auto avec braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 typename dans les paramètres template template](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 Attributs pour espaces de noms et énumérateurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 Littéraux de caractère u8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4230 Définitions d’espaces de noms imbriqués](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 static_assert court](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 15.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 Boucles For basées sur une plage généralisées](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 15.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 \[\[attribut\]\] fallthrough](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 15.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 Suppression du mot clé register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 Suppression de l’opérateur ++ pour bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 Capture de *this par valeur](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 Utilisation d’espaces de noms d’attribut sans répétition](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 \_\_has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 direct-list-init des énumérations fixes à partir d’entiers](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 Expressions lambda de constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 \[\[attribut\]\] nodiscard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 \[\[attribut\]\] maybe_unused](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 Liaisons structurées](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 Instructions if constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[P0305R1 Instructions de sélection avec des initialiseurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Littéraux hexadécimaux à virgule flottante](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 Autorisation de plusieurs arguments de modèle sans type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 Expressions fold](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 Suppression des spécifications d’exceptions dynamiques](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 Ajout de noexcept au système de type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 Allocation de mémoire dynamique à alignement accru](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 Variables inline](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 Mise en correspondance de paramètres template template avec des arguments compatibles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 Suppression de certaines réductions unaires vides](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 Correction des conversions de qualifications](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 Initialisation d’agrégats étendue](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0091R3 Déduction d’arguments de modèle pour les modèles de classe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br/>&nbsp;&nbsp;[P0512R0 Problèmes de déduction d’arguments de modèle de classe](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 Déclaration de paramètres de modèle sans type avec auto](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 Élision de copie garantie](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0136R1 Reformulation de l’héritage des constructeurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 Affinement de l’ordre d’évaluation des expressions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br/>&nbsp;&nbsp;[P0400R0 Ordre d’évaluation des arguments de la fonction](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 Expansions de pack dans les déclarations using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 Écartement d’attributs non reconnus](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|


|Domaine de fonctionnalités| |
|----|---|
|__Fonctionnalités du langage principal C++17 (rapport de défauts)__|__Prise en charge__|
|&nbsp;&nbsp;[P0702R1 Résolution de la déduction d’argument de modèle de classe pour les ctors de la liste d’initialiseurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 Simplification de la capture lambda implicite](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Non|
|&nbsp;&nbsp;[P0961R1 Assouplissement des règles de recherche d’un point de personnalisation de liaisons structurées](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|VS 2019 16.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0962R2 Assouplissement des règles de recherche d’un point de personnalisation de boucle range-for](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Non|
|&nbsp;&nbsp;[P0969R0 Autorisation des liaisons structurées aux membres accessibles](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|VS 2019 16.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0859R0 CWG 1581 : Quand les fonctions membres constexpr sont-elles définies ?](https://wg21.link/P0859R0)|Non|
|&nbsp;&nbsp;[P0929R2 Vérification des types de classe abstraite](https://wg21.link/P0929R2)|Non|
|&nbsp;&nbsp;[P1009R2 Déduction de la taille du tableau des nouvelles expressions](https://wg21.link/P1009R2)|Non|
|&nbsp;&nbsp;[P1286R2 Contra CWG DR1778](https://wg21.link/P1286R2)|Non|

|Domaine de fonctionnalités| |
|----|---|
|__Fonctionnalités du langage principal C++20__|__Prise en charge__|
|&nbsp;&nbsp;[P0704R1 Résolution des pointeurs const lvalue qualifiés ref vers des membres](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0972R0 noexcept pour \<chrono> zero(), min(), max()](https://wg21.link/P0972R0)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1330R0 Modification du membre actif d’une union à l’intérieur de constexpr](https://wg21.link/P1330R0)|VS 2017 15.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0329R4 Initialisation désignée](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0409R2 Autorisation de capture lambda \[=, this\]](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0515R3 Opérateur de comparaison triple (spaceship) <=>](https://wg21.link/P0515R3) et [P0905R1 Symétrie pour le spaceship](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0905r1.html)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0941R2 Macros de test de fonctionnalité](https://wg21.link/P0941R2)|VS 2019 16.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1008R1 Interdiction des agrégats avec les constructeurs déclarés par l’utilisateur](https://wg21.link/P1008R1)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0846R0 Modèles ADL et de fonction qui ne sont pas visibles](https://wg21.link/P0846R0)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0641R2 Incompatibilité de const avec le constructeur de copie par défaut](https://wg21.link/P0641R2)|Partial|
|&nbsp;&nbsp;[P0306R4 Ajout de \_\_VA_OPT\_\_ pour l’omission et la suppression de virgules](https://wg21.link/P0306R4) et [P1042R1 \_\_clarifications de la formulation\_\_ VA_OPT](https://wg21.link/P1042R1)|Non|
|&nbsp;&nbsp;[P0315R4 Autorisation de lambdas dans des contextes non évalués](https://wg21.link/P0315R4)|Non|
|&nbsp;&nbsp;[P0409R2 Autorisation de capture lambda \[=, this\]](https://wg21.link/P0409R2)|Non|
|&nbsp;&nbsp;[P0428R2 Syntaxe de modèle familier pour les expressions lambda génériques](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Non|
|&nbsp;&nbsp;[P0479R5 \[\[attributs\]\] probables \[\[ et \]\]peu probables](https://wg21.link/P0479R5)|Non|
|&nbsp;&nbsp;[P0542R5 Contrats](https://wg21.link/P0542R5)|Non|
|&nbsp;&nbsp;[P0614R1 Boucles range-based for avec initialiseurs](https://wg21.link/P0614R1)|Non|
|&nbsp;&nbsp;[P0624R2 Lambdas sans état constructibles et assignables par défaut](https://wg21.link/P0624R2)|Non|
|&nbsp;&nbsp;[P0634R3 À bas les typename !](https://wg21.link/P0634R3)|Non|
|&nbsp;&nbsp;[P0683R1 Initialiseurs de membres par défaut pour les champs de bits](https://wg21.link/P0683R1)|Non|
|&nbsp;&nbsp;[P0692R1 Assouplissement des contrôles d’accès sur les spécialisations](https://wg21.link/P0692R1)|Non|
|&nbsp;&nbsp;[P0722R3 Suppression dimensionnée efficace des classes dimensionnées variables](https://wg21.link/P0722R3)|Non|
|&nbsp;&nbsp;[P0732R2 Types de classe dans les paramètres de modèle sans type](https://wg21.link/P0732R2)|Non|
|&nbsp;&nbsp;[P0734R0 Concepts](https://wg21.link/P0734R0)|Non|
|&nbsp;&nbsp;[P0780R2 Autorisation de l’expansion de package dans une init-capture lambda](https://wg21.link/P0780R2)|Non|
|&nbsp;&nbsp;[P0806R2 Déconseiller cette capture implicite via \[=\]](https://wg21.link/P0806R2)|Non|
|&nbsp;&nbsp;[P0840R2 \[\[attribut\]\] no_unique_address](https://wg21.link/P0840R2)|Non|
|&nbsp;&nbsp;[P0857R0 Résolution des lacunes de fonctionnalités dans des contraintes](https://wg21.link/P0857R0)|Non|
|&nbsp;&nbsp;[P0892R2 Conditional explicite](https://wg21.link/P0892R2)|Non|
|&nbsp;&nbsp;[P0912R5 Coroutines](https://wg21.link/P0912R5)|Non|
|&nbsp;&nbsp;[P0960R3 Autoriser l’initialisation d’agrégats à partir de la liste des valeurs entre parenthèses](https://wg21.link/P0960R3)|Non|
|&nbsp;&nbsp;[P1002R1 Blocs try-catch des fonctions constexpr](https://wg21.link/P1002R1)|Non|
|&nbsp;&nbsp;[P1041R4 Transformer les littéraux de chaîne char16_t/char32_t en UTF-16/32](https://wg21.link/P1041R4)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1064R0 Autorisation d’appels de fonction virtuels dans les expressions constantes](https://wg21.link/P1064R0)|Non|
|&nbsp;&nbsp;[P1073R3 Fonctions immédiates](https://wg21.link/P1073R3)|Non|
|&nbsp;&nbsp;[P1084R2 Les exigencesde type de retour du jour sont insuffisantes](https://wg21.link/P1084R2)|Non|
|&nbsp;&nbsp;[P1091R3 Extension des liaisons structurées pour ressembler davantage à des déclarations de variable](https://wg21.link/P1091R3)|Non|
|&nbsp;&nbsp;[P1094R2 Espaces de noms inline imbriqués](https://wg21.link/P1094R2)|Non|
|&nbsp;&nbsp;[P1103R3 Modules](https://wg21.link/P1103R3)|Non|
|&nbsp;&nbsp;[P1120R0 Améliorations de la cohérence pour <=> et d’autres opérateurs de comparaison](https://wg21.link/P1120R0)|Non|
|&nbsp;&nbsp;[P1139R2 Problèmes de formulation d’adresse liés à la norme ISO 10646](https://wg21.link/P1139R2)|Non|
|&nbsp;&nbsp;[P1141R2 Encore une nouvelle approche pour les déclarations contraintes](https://wg21.link/P1141R2)|Non|
|&nbsp;&nbsp;[P1185R2 \<=\> != ==](https://wg21.link/P1185R2)|Non|
|&nbsp;&nbsp;[P1236R1 Les entiers signés sont un complément de deux](https://wg21.link/P1236R1)|Non|
|&nbsp;&nbsp;[P1289R1 Contrôle d’accès des conditions de contrat](https://wg21.link/P1289R1)|Non|
|&nbsp;&nbsp;[P1323R2 Post-conditions de contrat et déduction de type de retour](https://wg21.link/P1323R2)|Non|
|&nbsp;&nbsp;[P1327R1 Autorisation de dynamic_cast et d’ID de type polymorphe dans les expressions constantes](https://wg21.link/P1327R1)|Non|
|&nbsp;&nbsp;[P1353R0 Macros de test de fonctionnalité manquants](https://wg21.link/P1353R0)|Non|
|&nbsp;&nbsp;[P1381R1 Capture de référence des liaisons structurées](https://wg21.link/P1381R1)|Non|

## <a name="standard-library-features"></a>Fonctionnalités de bibliothèque standard

|Domaine de fonctionnalités| |
|---|---|
|__Fonctionnalités de bibliothèque standard C++20__|__Prise en charge__|
|&nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8)|Non|
|&nbsp;&nbsp;[P0020R6 atomic\<float>, atomic\<double>, atomic\<long double>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Non|
|&nbsp;&nbsp;[P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br/>&nbsp;&nbsp;[P0753R2 Manipulateurs osyncstream](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Non|
|&nbsp;&nbsp;[P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Non|
|&nbsp;&nbsp;[P0202R3 constexpr pour \<algorithm> et exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Non|
|&nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0318r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6)|Non|
|&nbsp;&nbsp;[P0340R3 underlying_type compatible avec SFINAE](https://wg21.link/P0340R3)|Non|
|&nbsp;&nbsp;[P0355R7 \<Calendriers et fuseaux horaires chrono>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Non|
|&nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5)|Non|
|&nbsp;&nbsp;[P0357R3 Prise en charge de types incomplets dans reference_wrapper](https://wg21.link/P0357R3)|Non|
|&nbsp;&nbsp;[P0415R1 constexpr pour \<complex> (à nouveau)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Non|
|&nbsp;&nbsp;[P0439R0 Classe enum memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Non|
|&nbsp;&nbsp;[P0457R2 starts_with()/ends_with() pour basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0458R2 contains() pour les conteneurs associatifs ordonnés et non ordonnés](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0458r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0463R1 endian](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Non|
|&nbsp;&nbsp;[P0475R1 Élision de copie garantie pour la construction par morceaux](https://wg21.link/P0475R1)|Non|
|&nbsp;&nbsp;[P0476R2 <bit> bit_cast](https://wg21.link/P0476R2)|Non|
|&nbsp;&nbsp;[P0482R6 char8_t : Un type pour les caractères et chaînes UTF-8](https://wg21.link/P0482R6)|Non|
|&nbsp;&nbsp;[P0487R1 Opérateur de résolution>>(basic_istream &,CharT*)](https://wg21.link/P0487R1)|Non|
|&nbsp;&nbsp;[P0528R3 Comparaison et échange atomique avec remplissage de Bits](https://wg21.link/P0528R3)|Non|
|&nbsp;&nbsp;[P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0556R3 <bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3)|Non|
|&nbsp;&nbsp;[P0591R4 Fonctions utilitaires pour la construction de Uses-Allocator](https://wg21.link/P0591R4)|Non|
|&nbsp;&nbsp;[P0600R1 \[\[nodiscard\]\] pour STL (première partie)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Non|
|&nbsp;&nbsp;[P0608R3 Amélioration du constructeur de conversion/opérateur d’assignation de variante](https://wg21.link/P0608R3)|Non|
|&nbsp;&nbsp;[P0616R0 Utilisation de move() dans \<numeric>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Non|
|&nbsp;&nbsp;[P0619R4 Suppression des fonctionnalités déconseillées de C++17 dans C++20](https://wg21.link/P0619R4)|Non|
|&nbsp;&nbsp;[P0646R1 list/forward_list remove()/remove_if()/unique() size_type de retour](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0646r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Non|
|&nbsp;&nbsp;[P0655R1 visit<R>()](https://wg21.link/P0655R1)|Non|
|&nbsp;&nbsp;[P0674R1 make_shared() pour tableaux](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Non|
|&nbsp;&nbsp;[P0718R2 atomic\<shared_ptr\<T>>, atomic\<weak_ptr\<T>>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Non|
|&nbsp;&nbsp;[P0738R2 Nettoyage de istream_iterator](https://wg21.link/P0738R2)|Non|
|&nbsp;&nbsp;[P0754R2 \<version>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Non|
|&nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1)|Non|
|&nbsp;&nbsp;[P0767R1 Dépréciation de is_pod](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Non|
|&nbsp;&nbsp;[P0768R1 Prise en charge des bibliothèques pour l’opérateur de comparaison spaceship \<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Non|
|&nbsp;&nbsp;[P0769R2 shift_left(), shift_right()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0769r2.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0771R1 noexcept pour le constructeur de déplacement de std::function](https://wg21.link/P0771R1)|Non|
|&nbsp;&nbsp;[P0777R1 Prévention des dégradations inutiles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0809R0 Comparaison de conteneurs non ordonnés](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0811R3 midpoint(), lerp()](https://wg21.link/P0811R3)|Non|
|&nbsp;&nbsp;[P0858R0 Exigences de l’itérateur constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0879R0 constexpr pour les fonctions de permutation](https://wg21.link/P0879R0)|Non|
|&nbsp;&nbsp;[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0896R4 \<Plages\>](https://wg21.link/P0896R4)|Non|
|&nbsp;&nbsp;[P0898R3 Concepts de bibliothèque standard](https://wg21.link/P0898R3)|Non|
|&nbsp;&nbsp;[P0912R5 Prise en charge de la bibliothèque pour les coroutines](https://wg21.link/P0912R5)|Non|
|&nbsp;&nbsp;[P0919R3 Recherche hétérogène pour les conteneurs non ordonnés](https://wg21.link/P0919R3)|Non|
|&nbsp;&nbsp;[P0920R2 Recherche de valeurs de hachage précalculées](https://wg21.link/P0920R2)|Non|
|&nbsp;&nbsp;[P0935R0 Éradication des constructeurs inutilement explicites par défaut](https://wg21.link/P0935R0)|Non|
|&nbsp;&nbsp;[P0966R1 string::reserve() ne doit pas être réduit](https://wg21.link/P0966R1)|Non|
|&nbsp;&nbsp;[P1001R2 execution::unseq](https://wg21.link/P1001R2)|Non|
|&nbsp;&nbsp;[P1006R1 constexpr pour pointer_traits<T*>::pointer_to()](https://wg21.link/P1006R1)|Non|
|&nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3)|Non|
|&nbsp;&nbsp;[P1020R1 Création de pointeur intelligent avec initialisation par défaut](https://wg21.link/P1020R1)|Non|
|&nbsp;&nbsp;[P1023R0 constexpr pour comparaisons std::array](https://wg21.link/P1023R0)|Non|
|&nbsp;&nbsp;[P1032R1 constexpr divers](https://wg21.link/P1032R1)|Non|
|&nbsp;&nbsp;[P1164R1 Rendre create_directory() intuitif (rapport)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1165R1 Propagation cohérente d’état allocateurs dans l’opérateur+() de basic_string](https://wg21.link/P1165R1)|Non|
|&nbsp;&nbsp;[P1209R0 erase_if(), erase()](https://wg21.link/P1209R0)|Non|
|&nbsp;&nbsp;[P1227R2 std::ssize() signé, span::size non signé](https://wg21.link/P1227R2)|Non|
|&nbsp;&nbsp;[P1285R0 Amélioration des exigences d’exhaustivité pour les caractéristiques de type](https://wg21.link/P1285R0)|Non|
|&nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1)|Non|
|__Fonctionnalités de bibliothèque standard C++17__|__Prise en charge__|
|&nbsp;&nbsp;[LWG 2221 Opérateur de sortie formaté pour nullptr](https://cplusplus.github.io/LWG/issue2221)|VS 2019 16.1|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 Conversions sécurisées dans unique_ptr\<T[]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 Suppression d’auto_ptr, random_shuffle() et du matériau \<functional> ancien](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 Nettoyages noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 reference_wrapper copiable de manière triviale](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() pour map/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 Affectation unique_ptr contrainte de façon précise](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4387 Amélioration de pair et tuple](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (sans contrainte de temps)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 Prise en charge des types incomplets dans vector/list/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 Suppression de l’affectation polymorphic_allocator](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<string_view>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<tuple> apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Library Fundamentals: Boyer-Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Résolution des types de retour de la fonction de recherche](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 Suppression des spécifications d’exceptions dynamiques](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0004R1 Suppression d’alias iostreams déconseillés](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br/>&nbsp;&nbsp;[P0358R1 Correctifs pour not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0006R0 Modèles de variable pour les caractéristiques de type (is_same_v, etc.).](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 Caractéristiques de type des opérateurs logiques (association, etc.).](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0024R2 Algorithmes parallèles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br/>&nbsp;&nbsp;[P0336R1 Renommage des stratégies d’exécution parallèle](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br/>&nbsp;&nbsp;[P0394R4 Les algorithmes parallèles doivent utiliser terminate() pour les exceptions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br/>&nbsp;&nbsp;[P0452R1 Unification des \<algorithmes parallèles numeric>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0031R0 constexpr pour \<array> (de nouveau) et \<iterator>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0032R3 Interface homogène pour variant/any/optional](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0033R1 Reformulation d’enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0040R3 Extension des outils de gestion de mémoire](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0063R3 Bibliothèque standard C11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[P0067R5 Conversions de chaîne élémentaires](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup>[charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0083R3 Transfert de mappages et d’ensembles](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br/>&nbsp;&nbsp;[P0508R0 Clarification d’insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Type de retour emplace](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, etc.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R0 lock_guard variadique](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R2 Changement de nom de l’élément variadique lock\_guard en scoped\_lock](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0174R2 Dépréciation de composants de bibliothèque rudimentaires](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0218R1 \<système de fichiers>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br/>&nbsp;&nbsp;[P0219R1 Chemins relatifs du système de fichiers](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br/>&nbsp;&nbsp;[P0317R1 Mise en cache de l’entrée d’annuaire pour le système de fichiers](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br/>&nbsp;&nbsp;[P0392R0 Prise en charge de string_view dans les chemins du système de fichiers](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br/>&nbsp;&nbsp;[P0430R2 Prise en charge des systèmes de fichiers non POSIX](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br/>&nbsp;&nbsp;[P0492R2 Résolution des commentaires NB pour le système de fichiers](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[E](#note_E)</sup>|
|&nbsp;&nbsp;[P0220R1 Spécification Library Fundamentals V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6 <sup>[F](#note_F)</sup>|
|&nbsp;&nbsp;[P0226R1 Fonctions mathématiques spéciales](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0254R2 Intégration de string_view et std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup>[17](#note_17),&nbsp;[octets](#note_byte)</sup>|
|&nbsp;&nbsp;[P0302R1 Suppression de la prise en charge d’un allocateur dans std::function](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0307R2 Fonctionnalité optional>=](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0393R3 Variante supériorité/égalité](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0403R1 UDL pour \<string_view> ("meow"sv, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br/>&nbsp;&nbsp;[P0497R0 Résolution de shared_ptr pour les tableaux](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0418R2 Spécifications compare_exchange memory_order atomiques](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0426R1 constexpr pour char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0433R2 Intégration de la déduction de modèle pour les modèles de classe dans la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br/>&nbsp;&nbsp;[P0739R0 Amélioration de l’intégration de la déduction d’argument de modèle de classe dans la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0435R1 Remaniant de common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br/>&nbsp;&nbsp;[P0548R1 Adaptation de common\_type et de duration](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0504R0 Retour sur in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0505R0 constexpr pour \<chrono> (de nouveau)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0510R0 Rejet des variantes vides, de tableaux, de références et de types incomplets](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0513R0 Empoisonnement du hachage](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br/>&nbsp;&nbsp;[P0599R1 Hash noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 Marquage de la copie de shared_future comme noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 Construction de future_error à partir de future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 Dépréciation de shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0558R1 Résolution des incohérences des classes de base nommées \<atomic](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)T>|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2)|Non|
|&nbsp;&nbsp;[P0602R4 Propagation de la trivialité copie/déplacement dans variant/facultatif](https://wg21.link/P0602R4)|VS 2017 15.3<sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0604R0 Remplacement de is\_callable/result\_of par invoke\_result, is\_invocable, is\_nothrow\_invocable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 Variables inline pour la bibliothèque standard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 Dépréciation de \<codecvt>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0682R1 Réparation de conversions de chaînes élémentaires](https://wg21.link/P0682R1)|VS 2015 15.7 <sup>[17](#note_17)</sup>|
|__Fonctionnalités de bibliothèque standard C++14__|__Prise en charge__|
|&nbsp;&nbsp;[N3462 Utilisation de result_of compatible avec SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr pour \<complex>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr pour \<chrono>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr pour \<array>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr pour \<initializer_list>, \<tuple>, \<utility>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 UDL pour \<chrono>, \<string> (1729ms, "meow"s, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Itérateurs « en avant » null](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Recherche associative hétérogène](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (avec contrainte de temps)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 Résolution des fonctions membres constexpr sans const](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 equal(), is_permutation(), mismatch() à double plage](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Désallocation dimensionnée](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 UDL pour \<complex> (3.14i, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr pour \<functional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 Renommage de shared_mutex (avec contrainte de temps) en shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Spécifications minimales d’éléments conteneurs](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 Foncteurs d’opérateurs transparents (less\<>, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Modèles d’alias pour \<type_traits> (decay_t, etc.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|

Un groupe de documents répertoriés ensemble indique qu’une fonctionnalité a été approuvée dans la norme, puis qu’un ou plusieurs documents visant à améliorer ou à développer cette fonctionnalité ont aussi été approuvés. Ces fonctionnalités sont implémentées ensemble.

### <a name="supported-values"></a>Valeurs prises en charge

__Non__  signifie que la fonctionnalité n’est pas encore implémentée.<br/>
__Partielle__ signifie que l’implémentation est incomplète. Pour plus d’informations, consultez la section Notes.<br/>
__VS 2010__ indique des fonctionnalités prises en charge dans Visual Studio 2010.<br/>
__VS 2013__ indique des fonctionnalités prises en charge dans Visual Studio 2013.<br/>
__VS 2015__ indique les fonctionnalités prises en charge dans Visual Studio 2015 RTM.<br/>
__Visual Studio 2015.2__ et __VS 2015.3__ indiquent des fonctionnalités prises en charge dans Visual Studio 2015 Update 2 et Visual Studio 2015 Update 3, respectivement.<br/>
__VS 2017 15.0__ indique les fonctionnalités prises en charge dans Visual Studio 2017 version 15.0 (RTW).<br/>
__VS 2017 15.3__ indique des fonctionnalités prises en charge dans Visual Studio 2017 version 15.3.<br/>
__VS 2017 15.5__ indique des fonctionnalités prises en charge dans Visual Studio 2017 version 15.5.<br/>
__VS 2017 15.7__ indique les fonctionnalités prises en charge dans Visual Studio 2017 version 15.7.<br/>
__VS 2019 16.0__ indique les fonctionnalités prises en charge dans Visual Studio 2019 version 16.0 (RTW).<br/>
__VS 2019 16.1__ indique les fonctionnalités prises en charge dans Visual Studio 2019 version 16.1.<br/>

### <a name="notes"></a>Notes

<a name="note_A"></a>__A__ En mode [/std:c++14](../build/reference/std-specify-language-standard-version.md), les spécifications d’exceptions dynamiques restent non implémentées, et `throw()` est toujours traité comme un synonyme de `__declspec(nothrow)`. Dans C++17, la plupart des spécifications d’exceptions dynamiques ont été supprimées par P0003R5, laissant un vestige : `throw()` est déconseillé et doit se comporter comme synonyme de `noexcept`. En mode [/std:c++17](../build/reference/std-specify-language-standard-version.md), MSVC est désormais conforme à la norme en donnant à `throw()` le même comportement que `noexcept`, comme la mise en œuvre par terminaison.

L’option de compilateur [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) requiert l’ancien comportement de `__declspec(nothrow)`. Il est vraisemblable que `throw()` soit supprimé de C++20. Pour faciliter la migration de code en réponse à ces changements dans la norme et notre implémentation, de nouveaux avertissements du compilateur pour les problèmes de spécification d’exception ont été ajoutés sous [/std:c++17](../build/reference/std-specify-language-standard-version.md) et [/permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a>__B__ Pris en charge dans le mode [/permissive-](../build/reference/permissive-standards-conformance.md) dans Visual Studio 2017 15.7. Pour plus d’informations, consultez [Prise en charge d’une recherche de nom en deux phases avec MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a>__C__ La prise en charge par le compilateur des règles de préprocesseur C99 est incomplète dans Visual Studio 2017. Les macros variadiques sont prises en charge, mais le comportement du préprocesseur présente de nombreux bogues. Nous restructurons actuellement le préprocesseur, et nous distribuerons à titre expérimental ces changements en mode [/permissive-](../build/reference/permissive-standards-conformance.md) sous peu.

<a name="note_D"></a>__D__ Pris en charge sous [/std:c++14](../build/reference/std-specify-language-standard-version.md) avec un avertissement pouvant être supprimé, C4984.

<a name="note_E"></a>__E__ Il s’agit d’une toute nouvelle implémentation, incompatible avec la version précédente de `std::experimental`, exigée par la prise en charge de symlink, les correctifs de bogues et les changements apportés à la norme. Actuellement, l’inclusion de \<filesystem> fournit le nouveau `std::filesystem` et le `std::experimental::filesystem` précédent, et l’inclusion de \<experimental/filesystem> fournit uniquement l’ancienne implémentation expérimentale. L’implémentation expérimentale sera supprimée de la prochaine version de rupture avec ABI des bibliothèques.

<a name="note_F"></a>__F__ Les fonctionnalités qui n’ont pas été terminées dans Visual Studio 2015 sont indiquées autre part dans ce tableau.

<a name="note_G"></a>__G__ Pris en charge par une fonction intrinsèque du compilateur.

<a name="note_14"></a>__14__ Ces fonctionnalités C++17/20 sont toujours activées, même quand [/std:c++14](../build/reference/std-specify-language-standard-version.md) (valeur par défaut) est spécifié. Soit parce que la fonctionnalité a été implémentée avant l’introduction des options **/std**, soit parce que l’implémentation conditionnelle était trop complexe.

<a name="note_17"></a>__17__ Ces fonctionnalités sont activées par l’option du compilateur [/std:c++17](../build/reference/std-specify-language-standard-version.md) (ou [/std:c++latest](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a>__20__ Ces fonctionnalités sont activées par l’option du compilateur [/std:c++17](../build/reference/std-specify-language-standard-version.md). Lorsque l’implémentation C++20 est terminée, une nouvelle option de compilateur **/std : c ++ 20** sera ajoutée.

<a name="note_byte"></a>__byte__ `std::byte` est activé par [/std:c++17](../build/reference/std-specify-language-standard-version.md) (ou [/std:c++latest](../build/reference/std-specify-language-standard-version.md)), mais étant donné qu’il peut entrer en conflit avec les en-têtes du SDK Windows dans certains cas, il comporte une macro d’annulation affinée. Il peut être désactivé en définissant `_HAS_STD_BYTE` sur `0`.

<a name="note_C11"></a>__C11__ Le CRT universel implémentait les parties de la bibliothèque standard C11 qui étaient requises par C++17, à l’exception des spécificateurs de conversion alternatifs C99 `strftime()` E/O, du mode exclusif C11 `fopen()` et de C11 `aligned_alloc()`. Ce dernier est peu susceptible d’être implémenté, car C11 spécifiait `aligned_alloc()` d’une manière non compatible avec l’implémentation Microsoft de `free()`, à savoir, que `free()` doit être en mesure de gérer les allocations très alignées.

<a name="note_rem"></a>__rem__ Fonctionnalités supprimées lorsque l’option du compilateur [/std:c++17](../build/reference/std-specify-language-standard-version.md) (ou [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) est spécifiée. Ces fonctionnalités peuvent être réactivées pour faciliter la transition vers des modes de langage plus récents à l’aide des macros suivants : `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`, et `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ `from_chars()` et `to_chars()` sont disponibles pour les entiers. La chronologie correspondant aux virgules flottantes `from_chars()` et `to_chars()` se présente comme suit :
- VS 2017 15.7 : Entier `from_chars()` et `to_chars()`.
- VS 2017 15.8 : Virgule flottante `from_chars()`.
- VS 2017 15.9 : La virgule flottante `to_chars()` est surchargée pour la décimale la plus courte.
- VS 2019 16.0 : La virgule flottante `to_chars()` est surchargée pour l’hexadécimale la plus courte et l’hexadécimale de précision.
- VS 2019 16.2 : La virgule flottante `to_chars()` est surchargée pour les précisions corrigées et scientifiques.
- Pas encore implémenté : La virgule flottante `to_chars()` est surchargée pour la précision générale. 

<a name ="note_parallel"></a> __parallel__ La bibliothèque d’algorithmes parallèles de C++17 est terminée. Cela ne signifie pas que chaque algorithme est parallélisé dans chaque cas. Les algorithmes les plus importants ont été parallélisés, et des signatures de stratégie d’exécution sont fournies même lorsque les algorithmes ne sont pas parallélisés. L’en-tête interne central de notre implémentation, yvals_core.h, contient les « notes d’algorithmes parallèles » suivantes : C++ permet une implémentation qui implémente des algorithmes parallèles comme appels aux algorithmes de série.  Cette implémentation parallélise plusieurs appels d’algorithme courants, mais pas tous.

Les algorithmes suivants sont parallélisés :

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Actuellement, les éléments suivants ne sont pas parallélisés :

- Aucune amélioration apparente n’a été apportée aux performances du parallélisme sur le matériel cible. La bande passante de mémoire de tous les algorithmes qui copient ou permutent simplement des éléments sans aucune branche est généralement limitée :
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Une certaine confusion existe concernant les exigences du parallélisme ; probablement dans la catégorie ci-dessus :
  - `generate`, `generate_n`
- Des soupçons existent quant à la possibilité d’établir un parallélisme efficace :
  - `partial_sort`, `partial_sort_copy`
- Pas encore évalué ; le parallélisme, qui peut être implémenté dans une version ultérieure, est censé être bénéfique :
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
[Améliorations de la conformité de C++ dans Visual Studio](cpp-conformance-improvements.md)<br/>
[Nouveautés de Visual C++ dans Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historique des modifications de Visual C++ entre 2003 et 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Nouveautés de Visual C++ entre 2003 et 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Blog de l’équipe C++](https://devblogs.microsoft.com/cppblog/)
