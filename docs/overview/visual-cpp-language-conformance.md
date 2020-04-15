---
title: Tableau de conformité du langage Microsoft C++
description: Tableau des mises à jour de conformité Microsoft CMD par la version Visual Studio.
ms.date: 03/17/2020
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: 18f8db28fab83f795baced82a346f07d73256716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365236"
---
# <a name="microsoft-c-language-conformance-table"></a>Tableau de conformité du langage Microsoft C++

La conformité aux normes pour le compilateur Microsoft CMD dans Visual Studio (MSVC) est un travail en cours. Voici un résumé de notre conformité en langue et bibliothèque ISO Standard CMD par visual Studio version. Chaque compilateur et bibliothèque standard comportent des liens nom vers le document de proposition ISO Standard CMD qui décrit la fonctionnalité, si l’on est disponible au moment de la publication. La colonne **Support** répertorie la version Visual Studio dans laquelle le support de la fonctionnalité est apparu pour la première fois.

Pour plus de détails sur Visual Studio 2017 ou Visual Studio 2019 MSVC conformance improvements, voir [les améliorations de conformité C ' dans Visual Studio](cpp-conformance-improvements.md). Pour une liste d’autres modifications, voir [What’s New for Visual CMD dans Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md). Pour passer en revue les changements de conformité dans les versions antérieures, consultez [Historique des modifications de Visual C++](../porting/visual-cpp-change-history-2003-2015.md) et [Nouveautés de Visual C++ entre 2003 et 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md). Pour connaître l’actualité de l’équipe C++, visitez le [blog de l’équipe C++](https://devblogs.microsoft.com/cppblog/).

> [!NOTE]
> Aucun changement binaire cassant n’a été effectué entre Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019. Pour plus d’informations, voir [compatibilité binaire CMD entre Visual Studio 2015, 2017 et 2019](../porting/binary-compat-2015-2017.md)

## <a name="compiler-features"></a>Fonctionnalités du compilateur

|  |  |
|--|--|
| __Caractéristiques linguistiques de base de la C-03/11__ | __Pris en charge__ |
| &nbsp;&nbsp;Tout le reste | VS 2015 <sup>[A](#note_A)</sup> |
| &nbsp;&nbsp;Recherche de noms en deux phases | VS 2017 15.7 <sup>[B](#note_B)</sup> |
| &nbsp;&nbsp;[N2634 SFINAE sur les expressions](https://wg21.link/N2634) | VS 2017 15.7 |
| &nbsp;&nbsp;[N1653 Préprocesseur C99](https://wg21.link/N1653) | Partielle <sup> [C](#note_C)</sup> |
| __Caractéristiques linguistiques de base de la C-14__ | __Pris en charge__ |
| &nbsp;&nbsp;[N3323 Formulation optimisée pour les conversions contextuelles](https://wg21.link/N3323) | VS 2013 |
| &nbsp;&nbsp;[N3472 Littéraux binaires](https://wg21.link/N3472) | VS 2015 |
| &nbsp;&nbsp;[N3638 Types de retour auto et decltype(auto)](https://wg21.link/n3638) | VS 2015 |
| &nbsp;&nbsp;[N3648 init-captures](https://wg21.link/n3648) | VS 2015 |
| &nbsp;&nbsp;[N3649 Expressions lambda génériques](https://wg21.link/n3649) | VS 2015 |
| &nbsp;&nbsp;[Attribut déprécié \[ \[\] \] N3760](https://wg21.link/n3760) | VS 2015 |
| &nbsp;&nbsp;[N3778 Désallocation dimensionnée](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3781 Séparateurs de chiffres](https://wg21.link/n3781) | VS 2015 |
| &nbsp;&nbsp;[N3651 Modèles de variables](https://wg21.link/n3651) | VS 2015.2 |
| &nbsp;&nbsp;[N3652 Fonctions constexpr étendues](https://wg21.link/n3652) | VS 2017 15.0 |
| &nbsp;&nbsp;[N3653 Initialiseurs de membres par défaut pour les agrégats](https://wg21.link/n3653) | VS 2017 15.0 |
| __Caractéristiques linguistiques de base de la C-17__ | __Pris en charge__ |
| &nbsp;&nbsp;[N4086 Suppression des trigraphes](https://wg21.link/n4086) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N3922 Nouvelles règles pour auto avec braced-init-lists](https://wg21.link/n3922) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4051 typename dans les paramètres template template](https://wg21.link/n4051) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4266 Attributs pour espaces de noms et énumérateurs](https://wg21.link/n4266) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4267 Littéraux de caractère u8](https://wg21.link/n4267) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4230 Définitions d’espaces de noms imbriqués](https://wg21.link/n4230) | VS 2015.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N3928 static_assert court](https://wg21.link/n3928) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0184R0 Boucles For basées sur une plage généralisées](https://wg21.link/p0184r0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[Attribut P0188R1 \[ \[fallthrough\] \]](https://wg21.link/p0188r1) | VS 2017 15.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0001R1 Suppression du mot clé register](https://wg21.link/p0001r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0002R1 Suppression de l’opérateur ++ pour bool](https://wg21.link/p0002r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0018R3 Capture de *this par valeur](https://wg21.link/p0018r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0028R4 Utilisation d’espaces de noms d’attribut sans répétition](https://wg21.link/p0028r4) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0061R1 \_ \_has_include](https://wg21.link/p0061r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0138R2 direct-list-init des énumérations fixes à partir d’entiers](https://wg21.link/p0138r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0170R1 Expressions lambda de constexpr](https://wg21.link/p0170r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0189R1 \[ \[attribut\] \] nodiscard](https://wg21.link/p0189r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[Attribut P0212R1 \[ \[maybe_unused\] \]](https://wg21.link/p0212r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0217R3 Liaisons structurées](https://wg21.link/p0217r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0292R2 Instructions if constexpr](https://wg21.link/p0292r2) | VS 2017 15.3 <sup>[D](#note_D)</sup> |
| &nbsp;&nbsp;[P0305R1 Instructions de sélection avec des initialiseurs](https://wg21.link/p0305r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0245R1 Littéraux hexadécimaux à virgule flottante](https://wg21.link/p0245r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4268 Autoriser plus d’args modèles non-type](https://wg21.link/n4268) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4295 Expressions fold](https://wg21.link/n4295) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Suppression des spécifications d’exceptions dynamiques](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0012R1 Ajout de noexcept au système de type](https://wg21.link/p0012r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0035R4 Allocation de mémoire dynamique à alignement accru](https://wg21.link/p0035r4) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0386R2 Variables inline](https://wg21.link/p0386r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0522R0 Mise en correspondance de paramètres template template avec des arguments compatibles](https://wg21.link/p0522r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0036R0 Suppression de certaines réductions unaires vides](https://wg21.link/p0036r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[N4261 Fixation des conversions de qualification](https://wg21.link/n4261) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0017R1 Initialisation d’agrégats étendue](https://wg21.link/p0017r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0091R3 Déduction d’arguments de modèle pour les modèles de classe](https://wg21.link/p0091r3)<br/>&nbsp;&nbsp;[P0512R0 Problèmes de déduction d’arguments de modèle de classe](https://wg21.link/p0512r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0127R2 Déclaration de paramètres de modèle sans type avec auto](https://wg21.link/p0127r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0135R1 Élision de copie garantie](https://wg21.link/p0135r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0136R1 Reformulation de l’héritage des constructeurs](https://wg21.link/p0136r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0137R1 std::launder](https://wg21.link/p0137r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0145R3 Affinement de l’ordre d’évaluation des expressions](https://wg21.link/p0145r3)<br/>&nbsp;&nbsp;[P0400R0 Ordre d’évaluation des arguments de la fonction](https://wg21.link/p0400r0) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0195R2 Expansions de pack dans les déclarations using](https://wg21.link/p0195r2) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0283R2 Écartement d’attributs non reconnus](https://wg21.link/p0283r2) | VS 2015 <sup>[14](#note_14)</sup> |
| __Caractéristiques linguistiques de base (rapports de défaut)__ | __Pris en charge__ |
| &nbsp;&nbsp;[P0702R1 Résolution de la déduction d’argument de modèle de classe pour les ctors de la liste d’initialiseurs](https://wg21.link/p0702r1) | VS 2017 15,7 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0961R1 Assouplissement des règles de recherche d’un point de personnalisation de liaisons structurées](https://wg21.link/p0961r1) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0969R0 Autorisation des liaisons structurées aux membres accessibles](https://wg21.link/p0969r0) | VS 2019 16.0 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0588R1 Simplification de la capture lambda implicite](https://wg21.link/p0588r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1771R1 \[ \[nodiscard\] \] pour les constructeurs](https://wg21.link/p1771r1) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P1825R0 Formulation fusionnée pour P0527R1 et P1155R3, mouvements plus implicites](https://wg21.link/p1825r0) | VS 2019 16,4 <sup> [17](#note_17)</sup> |
| &nbsp;&nbsp;[P0929R2 Vérification des types de classe abstraite](https://wg21.link/P0929R2) | Non |
| &nbsp;&nbsp;[P0962R2 Assouplissement des règles de recherche d’un point de personnalisation de boucle range-for](https://wg21.link/p0962r1) | Non |
| &nbsp;&nbsp;[P0859R0 CWG 1581: Quand sont définis les fonctions des membres constexpr](https://wg21.link/p0859r0) | Non |
| &nbsp;&nbsp;[P1009R2 Déduction de la taille du tableau des nouvelles expressions](https://wg21.link/P1009R2) | Non |
| &nbsp;&nbsp;[P1286R2 Contra CWG DR1778](https://wg21.link/P1286R2) | Non |
| __Caractéristiques linguistiques de base de la C-20__ | __Pris en charge__ |
| &nbsp;&nbsp;[P0704R1 Résolution des pointeurs const lvalue qualifiés ref vers des membres](https://wg21.link/p0704r1) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1041R4 Transformer les littéraux de chaîne char16_t/char32_t en UTF-16/32](https://wg21.link/P1041R4) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1330R0 Modification du membre actif d’une union à l’intérieur de constexpr](https://wg21.link/P1330R0) | VS 2017 15.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0972R0 noexcept pour \<chrono> zero(), min(), max()](https://wg21.link/P0972R0) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0515R3 Opérateur de comparaison trilatérale (vaisseau spatial) <=>](https://wg21.link/P0515R3) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0941R2 Macros de test de fonctionnalité](https://wg21.link/P0941R2) | VS 2019 16.0 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1008R1 Interdiction des agrégats avec les constructeurs déclarés par l’utilisateur](https://wg21.link/P1008R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0329R4 Initialisation désignée](https://wg21.link/p0329r4) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0846R0 Modèles ADL et de fonction qui ne sont pas visibles](https://wg21.link/P0846R0) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0409R2 Autorisation de capture lambda \[=, this\]](https://wg21.link/p0409r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0428R2 Syntaxe de modèle familier pour les expressions lambda génériques](https://wg21.link/p0428r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0624R2 Lambdas sans état constructibles et assignables par défaut](https://wg21.link/P0624R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0780R2 Autorisation de l’expansion de package dans une init-capture lambda](https://wg21.link/P0780R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0806R2 Déprécier la capture implicite de ce via\[=\]](https://wg21.link/P0806R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1120R0 Améliorations de la cohérence pour <=> et d’autres opérateurs de comparaison](https://wg21.link/P1120R0) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1185R2 \< = \> !](https://wg21.link/P1185R2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0734R0 Concepts](https://wg21.link/P0734R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0857R0 Résolution des lacunes de fonctionnalités dans des contraintes](https://wg21.link/P0857R0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1084R2 Les exigencesde type de retour du jour sont insuffisantes](https://wg21.link/P1084R2) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0892R2 Conditional explicite](https://wg21.link/P0892R2) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1091R3 Extension des liaisons structurées pour ressembler davantage à des déclarations de variable](https://wg21.link/P1091R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1099R5 Utilisation de l’enum](https://wg21.link/P1099R5) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1186R3 Lorsque utilisez-vous réellement\<=>](https://wg21.link/P1186R3) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1630R1 Vaisseau spatial a besoin d’une mise au point](https://wg21.link/P1630R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0306R4 \_ \_Ajout de\_ \_ VA_OPT pour omission de virgule et suppression de virgule](https://wg21.link/P0306R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0614R1 Boucles range-based for avec initialiseurs](https://wg21.link/P0614R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0683R1 Initialiseurs de membres par défaut pour les champs de bits](https://wg21.link/P0683R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1002R1 Blocs try-catch des fonctions constexpr](https://wg21.link/P1002R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1161R3 Déprécier les utilisations de l’opérateur de virgule dans la sous-scripte des expressions](https://wg21.link/P1161R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1301R4 \[ \[nodiscard ("message")\]\]](https://wg21.link/P1301R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1703R1 Reconnaître les importations d’unités d’en-tête nécessite un prétraitement complet](https://wg21.link/P1703R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1946R0 Autoriser les comparaisons par défaut par valeur](https://wg21.link/P1946R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0641R2 Incompatibilité de const avec le constructeur de copie par défaut](https://wg21.link/P0641R2) | Partiel |
| &nbsp;&nbsp;[P0912R5 Coroutines](https://wg21.link/P0912R5) | Partiel |
| &nbsp;&nbsp;[P1103R3 Modules](https://wg21.link/P1103R3) | Partiel |
| &nbsp;&nbsp;[P0315R4 Autorisation de lambdas dans des contextes non évalués](https://wg21.link/P0315R4) | Non |
| &nbsp;&nbsp;[Conversions de permis P0388R4 en tableaux de limite inconnue](https://wg21.link/P0388R4) | Non |
| &nbsp;&nbsp;[P0479R5 \[ \[\] \] attributs probables et \[ \[improbables\] \]](https://wg21.link/P0479R5) | Non |
| &nbsp;&nbsp;[P0634R3 À bas les typename !](https://wg21.link/P0634R3) | Non |
| &nbsp;&nbsp;[P0692R1 Assouplissement des contrôles d’accès sur les spécialisations](https://wg21.link/P0692R1) | Non |
| &nbsp;&nbsp;[P0722R3 Suppression dimensionnée efficace des classes dimensionnées variables](https://wg21.link/P0722R3) | Non |
| &nbsp;&nbsp;[P0732R2 Types de classe dans les paramètres de modèle sans type](https://wg21.link/P0732R2) | Non |
| &nbsp;&nbsp;[P0735R1 Interaction de memory_order_consume avec séquences de sortie](https://wg21.link/P0735R1) | Non |
| &nbsp;&nbsp;[P0784R7 Plus de contenants constexpr](https://wg21.link/P0784R7) | Non |
| &nbsp;&nbsp;[Attribut P0840R2 \[ \[\] \] no_unique_address](https://wg21.link/P0840R2) | Non |
| &nbsp;&nbsp;[P0848R3 Fonctions spéciales conditionnellement triviales](https://wg21.link/P0848R3) | Non |
| &nbsp;&nbsp;[P0960R3 Autoriser l’initialisation d’agrégats à partir de la liste des valeurs entre parenthèses](https://wg21.link/P0960R3) | Non |
| &nbsp;&nbsp;[P1064R0 Autorisation d’appels de fonction virtuels dans les expressions constantes](https://wg21.link/P1064R0) | Non |
| &nbsp;&nbsp;[P1073R3 Fonctions immédiates](https://wg21.link/P1073R3) | Non |
| &nbsp;&nbsp;[P1094R2 Espaces de noms inline imbriqués](https://wg21.link/P1094R2) | Non |
| &nbsp;&nbsp;[P1139R2 Problèmes de formulation d’adresse liés à la norme ISO 10646](https://wg21.link/P1139R2) | Non |
| &nbsp;&nbsp;[P1141R2 Encore une nouvelle approche pour les déclarations contraintes](https://wg21.link/P1141R2) | Non |
| &nbsp;&nbsp;[P1143R2 constinit](https://wg21.link/P1143R2) | Non |
| &nbsp;&nbsp;[P1152R4 Déprécier volatile](https://wg21.link/P1152R4) | Non |
| &nbsp;&nbsp;[P1236R1 Les entiers signés sont un complément de deux](https://wg21.link/P1236R1) | Non |
| &nbsp;&nbsp;[P1327R1 Autorisation de dynamic_cast et d’ID de type polymorphe dans les expressions constantes](https://wg21.link/P1327R1) | Non |
| &nbsp;&nbsp;[P1331R2 Permettre une initialisation par défaut triviale dans les contextes constexpr](https://wg21.link/P1331R2) | Non |
| &nbsp;&nbsp;[P1353R0 Macros de test de fonctionnalité manquants](https://wg21.link/P1353R0) | Non |
| &nbsp;&nbsp;[P1381R1 Capture de référence des liaisons structurées](https://wg21.link/P1381R1) | Non |
| &nbsp;&nbsp;[P1452R2 Sur la sémantique non uniforme des exigences de retour-type](https://wg21.link/P1452R2) | Non |
| &nbsp;&nbsp;[P1616R1 Utilisation de TTP sans contrainte avec des modèles limités](https://wg21.link/P1616R1) | Non |
| &nbsp;&nbsp;[P1668R1 Permettre l’assemblage en ligne non évalué dans les fonctions constexpr](https://wg21.link/P1668R1) | Non |
| &nbsp;&nbsp;[P1766R1 Atténuer les modules mineurs maladies](https://wg21.link/P1766R1) | Non |
| &nbsp;&nbsp;[P1811R0 Assouplir les restrictions de redéfinition pour la robustesse de la ré-exportation](https://wg21.link/P1811R0) | Non |
| &nbsp;&nbsp;[P1814R0 CTAD pour modèles d’alias](https://wg21.link/P1814R0) | Non |
| &nbsp;&nbsp;[P1816R0 CTAD pour les agrégats](https://wg21.link/P1816R0) | Non |
| &nbsp;&nbsp;[P1874R1 Ordonnance d’initialisation dynamique des variables non locales dans les modules](https://wg21.link/P1874R1) | Non |
| &nbsp;&nbsp;[P1907R1 Incohérences avec paramètres de modèle non-type](https://wg21.link/P1907R1) | Non |
| &nbsp;&nbsp;[P1971R0 Core Changes for NB Commentaires à la réunion de novembre 2019 (Belfast)](https://wg21.link/P1971R0) | Non |
| &nbsp;&nbsp;[P1972R0 US105 Vérifiez la satisfaction des contraintes pour les non-modèles lors de la formation de pointeur pour fonctionner](https://wg21.link/P1972R0) | Non |
| &nbsp;&nbsp;[P1975R0 Fixation du libellé de l’agrégat-initialisation entre parenthèses](https://wg21.link/P1975R0) | Non |
| &nbsp;&nbsp;[Résolution P1979R0 aux ÉTATS-Unis086](https://wg21.link/P1979R0) | Non |
| &nbsp;&nbsp;[P1980R0 CA096: Déclaration correspondant aux clauses d’exige non-dépendantes](https://wg21.link/P1980R0) | Non |

## <a name="standard-library-features"></a>Fonctionnalités de bibliothèque standard

|  |  |
|--|--|
| __Caractéristiques de la bibliothèque standard de la C-20__ | __Pris en charge__ |
| &nbsp;&nbsp;[P0809R0 Comparaison de conteneurs non ordonnés](https://wg21.link/p0809r0) | VS 2010 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0858R0 Exigences de l’itérateur constexpr](https://wg21.link/p0858r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0777R1 Prévention des dégradations inutiles](https://wg21.link/p0777r1) | VS 2017 15.7 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P1164R1 Faire create_directory() Intuitive](https://wg21.link/P1164R1) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0550R2 remove_cvref](https://wg21.link/p0550r2) | VS 2019 16.0 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0318R1 unwrap_reference, unwrap_ref_decay](https://wg21.link/p0318r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0457R2 starts_with()/ends_with() pour basic_string/basic_string_view](https://wg21.link/p0457r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0458R2 contains() pour les conteneurs associatifs ordonnés et non ordonnés](https://wg21.link/p0458r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0646R1 list/forward_list remove()/remove_if()/unique() size_type de retour](https://wg21.link/p0646r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0769R2 shift_left(), shift_right()](https://wg21.link/p0769r2) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0887R1 type_identity](https://wg21.link/p0887r1) | VS 2019 16.1 <sup>[20](#note_20)</sup> |
| &nbsp;&nbsp;[P0020R6 atomic\<float>, atomic\<double>, atomic\<long double>](https://wg21.link/p0020r6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0463R1 endian](https://wg21.link/p0463r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0482R6 char8_t: Un type pour les caractères et les cordes UTF-8](https://wg21.link/P0482R6) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0600R1 \[ \[nodiscard\] \] Pour le TSL, Partie 1](https://wg21.link/p0600r1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0754R2 \<version>](https://wg21.link/p0754r2) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0771R1 noexcept pour le constructeur de déplacement de std::function](https://wg21.link/P0771R1) | VS 2019 16,2 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0487R1 Opérateur de résolution>>(basic_istream &,CharT*)](https://wg21.link/P0487R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0616R0 Utilisation de move() dans \<numeric>](https://wg21.link/p0616r0) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0898R3 Concepts de bibliothèque standard](https://wg21.link/P0898R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0919R3 Recherche hétérogène pour les conteneurs non ordonnés](https://wg21.link/P0919R3) | VS 2019 16,3 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1754R1 Renommer les concepts pour standard_case](https://wg21.link/P1754R1) | VS 2019 16,4 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0325R4 to_array de LFTS avec mises à jour](https://wg21.link/P0325R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0340R3 underlying_type compatible avec SFINAE](https://wg21.link/P0340R3) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0439R0 Classe enum memory_order](https://wg21.link/p0439r0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0553R4 \<bit> rotation et de comptage des fonctions](https://wg21.link/P0553R4) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0556R3 \<bit> ispow2(), ceil2(), floor2(), log2p1()](https://wg21.link/P0556R3) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0595R2 is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0631R8 \<numéros> Math Constants](https://wg21.link/P0631R8) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0738R2 Nettoyage de istream_iterator](https://wg21.link/P0738R2) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0767R1 Dépréciation de is_pod](https://wg21.link/P0767R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0966R1 string::reserve() ne doit pas être réduit](https://wg21.link/P0966R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1209R0 erase_if(), erase()](https://wg21.link/P1209R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1227R2 std::ssize() signé, span::size non signé](https://wg21.link/P1227R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1355R2 Contrat étroit pour ceil2()](https://wg21.link/P1355R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1357R1 is_bounded_array, is_unbounded_array](https://wg21.link/P1357R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1612R1 Relocalisation endian \<Pour mordre>](https://wg21.link/P1612R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1651R0 bind_front() ne doit pas déballer reference_wrapper](https://wg21.link/P1651R0) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1690R1 Refining Heterogeneous Lookup For Unordered Containers](https://wg21.link/P1690R1) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P1902R1 Macros de test de fonctionnalités manquants 2017-2019](https://wg21.link/P1902R1) | VS 2019 16,5 <sup> [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8) | Non |
| &nbsp;&nbsp;[P0053R7 \<syncstream>](https://wg21.link/p0053r7)<br/>&nbsp;&nbsp;[P0753R2 Manipulateurs osyncstream](https://wg21.link/p0753r2) | Non |
| &nbsp;&nbsp;[P0122R7 \<span>](https://wg21.link/p0122r7) | Non |
| &nbsp;&nbsp;[P0202R3 constexpr pour \<algorithm> et exchange()](https://wg21.link/p0202r3) | Non |
| &nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6) | Non |
| &nbsp;&nbsp;[P0355R7 Calendriers et fuseaux horaires \<chrono>](https://wg21.link/p0355r7) | Non |
| &nbsp;&nbsp;[P0357R3 Prise en charge de types incomplets dans reference_wrapper](https://wg21.link/P0357R3) | Non |
| &nbsp;&nbsp;[P0415R1 constexpr pour \<complex> (à nouveau)](https://wg21.link/p0415r1) | Non |
| &nbsp;&nbsp;[P0475R1 Élision de copie garantie pour la construction par morceaux](https://wg21.link/P0475R1) | Non |
| &nbsp;&nbsp;[P0476R2 \<bit> bit_cast](https://wg21.link/P0476R2) | Non |
| &nbsp;&nbsp;[P0528R3 Comparaison et échange atomique avec remplissage de Bits](https://wg21.link/P0528R3) | Non |
| &nbsp;&nbsp;[P0591R4 Fonctions utilitaires pour la construction de Uses-Allocator](https://wg21.link/P0591R4) | Non |
| &nbsp;&nbsp;[P0608R3 Amélioration du constructeur de conversion/opérateur d’assignation de variante](https://wg21.link/P0608R3) | Non |
| &nbsp;&nbsp;[P0619R4 Suppression des fonctionnalités déconseillées de C++17 dans C++20](https://wg21.link/P0619R4) | Non |
| &nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2) | Non |
| &nbsp;&nbsp;[P0655R1\<visite R>()](https://wg21.link/P0655R1) | Non |
| &nbsp;&nbsp;[P0674R1 make_shared() pour tableaux](https://wg21.link/p0674r1) | Non |
| &nbsp;&nbsp;[P0718R2 atomic\<shared_ptr\<T>>, atomic\<weak_ptr\<T>>](https://wg21.link/p0718r2) | Non |
| &nbsp;&nbsp;[P0768R1 Support de bibliothèque pour l’opérateur de comparaison de vaisseau spatial\<=>](https://wg21.link/p0768r1) | Non |
| &nbsp;&nbsp;[P0811R3 midpoint(), lerp()](https://wg21.link/P0811R3) | Non |
| &nbsp;&nbsp;[P0879R0 constexpr pour les fonctions de permutation](https://wg21.link/P0879R0) | Non |
| &nbsp;&nbsp;[P0896R4 \<Plages\>](https://wg21.link/P0896R4) | Non |
| &nbsp;&nbsp;[P0912R5 Prise en charge de la bibliothèque pour les coroutines](https://wg21.link/P0912R5) | Non |
| &nbsp;&nbsp;[P0920R2 Recherche de valeurs de hachage précalculées](https://wg21.link/P0920R2) | Non |
| &nbsp;&nbsp;[P0935R0 Éradication des constructeurs inutilement explicites par défaut](https://wg21.link/P0935R0) | Non |
| &nbsp;&nbsp;[P1001R2 execution::unseq](https://wg21.link/P1001R2) | Non |
| &nbsp;&nbsp;[P1006R1 constexpr pour pointer_traits<T*>::pointer_to()](https://wg21.link/P1006R1) | Non |
| &nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3) | Non |
| &nbsp;&nbsp;[P1020R1 Création de pointeur intelligent avec initialisation par défaut](https://wg21.link/P1020R1) | Non |
| &nbsp;&nbsp;[P1023R0 constexpr pour comparaisons std::array](https://wg21.link/P1023R0) | Non |
| &nbsp;&nbsp;[P1032R1 constexpr divers](https://wg21.link/P1032R1) | Non |
| &nbsp;&nbsp;[P1165R1 Propagation cohérente d’état allocateurs dans l’opérateur+() de basic_string](https://wg21.link/P1165R1) | Non |
| &nbsp;&nbsp;[P1285R0 Amélioration des exigences d’exhaustivité pour les caractéristiques de type](https://wg21.link/P1285R0) | Non |
| __Caractéristiques de la bibliothèque standard de la C-17__ | __Pris en charge__ |
| &nbsp;&nbsp;[LWG 2221 Opérateur de sortie formaté pour nullptr](https://cplusplus.github.io/LWG/issue2221) | VS 2019 16.1 |
| &nbsp;&nbsp;[N3911 void_t](https://wg21.link/n3911) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4089 Conversions sécurisées dans unique_ptr\<T[]>](https://wg21.link/n4089) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4169 invoke()](https://wg21.link/n4169) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4190 Suppression d’auto_ptr, random_shuffle() et du matériau \<functional> ancien](https://wg21.link/n4190) | VS 2015 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[N4258 Nettoyages noexcept](https://wg21.link/n4258) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4259 uncaught_exceptions()](https://wg21.link/n4259) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4277 reference_wrapper copiable de manière triviale](https://wg21.link/n4277) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() pour map/unordered_map](https://wg21.link/n4279) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4280 size(), empty(), data()](https://wg21.link/n4280) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4366 Affectation unique_ptr contrainte de façon précise](https://wg21.link/n4366) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4387 Amélioration de pair et tuple](https://wg21.link/n4387) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4389 bool_constant](https://wg21.link/n4389) | VS 2015 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4508 shared_mutex (sans contrainte de temps)](https://wg21.link/n4508) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4510 Prise en charge des types incomplets dans vector/list/forward_list](https://wg21.link/n4510) | VS 2013 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<algorithm> sample()](https://wg21.link/n4562#alg.random.sample) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<any>](https://wg21.link/n4562#any) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<memory_resource>](https://wg21.link/n4562#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 Suppression de l’affectation polymorphic_allocator](https://wg21.link/p0337r0) | VS 2017 15.6 |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<optional>](https://wg21.link/n4562#optional) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<string_view>](https://wg21.link/n4562#string.view) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : \<tuple> apply()](https://wg21.link/n4562#tuple) | VS 2017 15.0 |
| &nbsp;&nbsp;[N4562 Notions de base des bibliothèques : Boyer-Moore search()](https://wg21.link/n4562#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Résolution des types de retour de la fonction de recherche](https://wg21.link/p0253r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0003R5 Suppression des spécifications d’exceptions dynamiques](https://wg21.link/p0003r5) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0004R1 Suppression d’alias iostreams déconseillés](https://wg21.link/p0004r1) | VS 2015.2 <sup>[rem](#note_rem)</sup> |
| &nbsp;&nbsp;[P0005R4 not_fn()](https://wg21.link/p0005r4)<br/>&nbsp;&nbsp;[P0358R1 Correctifs pour not_fn()](https://wg21.link/p0358r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0006R0 Modèles de variable pour les caractéristiques de type (is_same_v, etc.).](https://wg21.link/p0006r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0007R1 as_const()](https://wg21.link/p0007r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0013R1 Caractéristiques de type des opérateurs logiques (association, etc.).](https://wg21.link/p0013r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0024R2 Algorithmes parallèles](https://wg21.link/p0024r2)<br/>&nbsp;&nbsp;[P0336R1 Renommage des stratégies d’exécution parallèle](https://wg21.link/p0336r1)<br/>&nbsp;&nbsp;[P0394R4 Les algorithmes parallèles doivent utiliser terminate() pour les exceptions](https://wg21.link/p0394r4)<br/>&nbsp;&nbsp;[P0452R1 Unifier \<les algorithmes numériques> parallèles](https://wg21.link/p0452r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0025R1 clamp()](https://wg21.link/p0025r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0030R1 hypot(x, y, z)](https://wg21.link/p0030r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0031R0 constexpr pour \<array> (de nouveau) et \<iterator>](https://wg21.link/p0031r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0032R3 Interface homogène pour variant/any/optional](https://wg21.link/p0032r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0033R1 Reformulation d’enable_shared_from_this](https://wg21.link/p0033r1) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0040R3 Extension des outils de gestion de mémoire](https://wg21.link/p0040r3) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0063R3 Bibliothèque standard C11](https://wg21.link/p0063r3) | VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup> |
| &nbsp;&nbsp;[P0067R5 Conversions de chaîne élémentaires](https://wg21.link/p0067r5) | VS 2019 16,4 <sup> [charconv](#note_charconv)</sup> |
| &nbsp;&nbsp;[P0074R0 owner_less\<>](https://wg21.link/p0074r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](https://wg21.link/p0077r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0083R3 Transfert de mappages et d’ensembles](https://wg21.link/p0083r3)<br/>&nbsp;&nbsp;[P0508R0 Clarification d’insert_return_type](https://wg21.link/p0508r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0084R2 Type de retour emplace](https://wg21.link/p0084r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0088R3 \<variant>](https://wg21.link/p0088r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](https://wg21.link/p0092r1) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](https://wg21.link/p0152r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size, etc.](https://wg21.link/p0154r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0156R0 lock_guard variadique](https://wg21.link/p0156r0) | VS 2015.2 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0156R2 Changement de nom de l’élément variadique lock\_guard en scoped\_lock](https://wg21.link/p0156r2) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](https://wg21.link/p0163r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0174R2 Dépréciation de composants de bibliothèque rudimentaires](https://wg21.link/p0174r2) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](https://wg21.link/p0185r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0209R2 make_from_tuple()](https://wg21.link/p0209r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0218R1 \<système de fichiers>](https://wg21.link/p0218r1)<br/>&nbsp;&nbsp;[P0219R1 Chemins relatifs du système de fichiers](https://wg21.link/p0219r1)<br/>&nbsp;&nbsp;[P0317R1 Mise en cache de l’entrée d’annuaire pour le système de fichiers](https://wg21.link/p0317r1)<br/>&nbsp;&nbsp;[P0392R0 Prise en charge de string_view dans les chemins du système de fichiers](https://wg21.link/p0392r0)<br/>&nbsp;&nbsp;[P0430R2 Soutien non-POSIX Systèmes de fichiers](https://wg21.link/p0430r2)<br/>&nbsp;&nbsp;[P0492R2 Résolution des commentaires NB pour le système de fichiers](https://wg21.link/p0492r2) | VS 2017 15.7 <sup>[E](#note_E)</sup> |
| &nbsp;&nbsp;[P0220R1 Spécification Library Fundamentals V1](https://wg21.link/p0220r1) | VS 2017 15.6 |
| &nbsp;&nbsp;[P0226R1 Fonctions mathématiques spéciales](https://wg21.link/p0226r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0254R2 Intégration de string_view et std::string](https://wg21.link/p0254r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0258R2 has_unique_object_representations](https://wg21.link/p0258r2) | VS 2017 15.3 <sup>[G](#note_G)</sup> |
| &nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](https://wg21.link/p0272r1) | VS 2015.3 |
| &nbsp;&nbsp;[P0295R0 gcd(), lcm()](https://wg21.link/p0295r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0298R3 std::byte](https://wg21.link/p0298r3) | VS 2017 15.3 <sup>[17](#note_17),&nbsp;[octets](#note_byte)</sup> |
| &nbsp;&nbsp;[P0302R1 Suppression de la prise en charge d’un allocateur dans std::function](https://wg21.link/p0302r1) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0307R2 Fonctionnalité optional>=](https://wg21.link/p0307r2) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0393R3 Variante supériorité/égalité](https://wg21.link/p0393r3) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0403R1 UDL pour \<string_view> ("meow"sv, etc.)](https://wg21.link/p0403r1) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](https://wg21.link/p0414r2)<br/>&nbsp;&nbsp;[P0497R0 Résolution de shared_ptr pour les tableaux](https://wg21.link/p0497r0) | VS 2017 15.5 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0418R2 Spécifications compare_exchange memory_order atomiques](https://wg21.link/p0418r2) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0426R1 constexpr pour char_traits](https://wg21.link/p0426r1) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0433R2 Intégration de la déduction de modèle pour les modèles de classe dans la bibliothèque standard](https://wg21.link/p0433r2)<br/>&nbsp;&nbsp;[P0739R0 Amélioration de l’intégration de la déduction d’argument de modèle de classe dans la bibliothèque standard](https://wg21.link/p0739r0) | VS 2017 15.7 |
| &nbsp;&nbsp;[P0435R1 Remaniant de common_type](https://wg21.link/p0435r1)<br/>&nbsp;&nbsp;[P0548R1 Tweaking\_type commun et durée](https://wg21.link/p0548r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0504R0 Retour sur in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](https://wg21.link/p0504r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0505R0 constexpr pour \<chrono> (de nouveau)](https://wg21.link/p0505r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0510R0 Rejet des variantes vides, de tableaux, de références et de types incomplets](https://wg21.link/p0510r0) | VS 2017 15.0 |
| &nbsp;&nbsp;[P0513R0 Empoisonnement du hachage](https://wg21.link/p0513r0)<br/>&nbsp;&nbsp;[P0599R1 noexcept hash](https://wg21.link/p0599r1) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0516R0 Marquage de la copie de shared_future comme noexcept](https://wg21.link/p0516r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0517R0 Construction de future_error à partir de future_errc](https://wg21.link/p0517r0) | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0521R0 Dépréciation de shared_ptr::unique()](https://wg21.link/p0521r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0558R1 Résolution des incohérences des classes de base nommées \<atomic](https://wg21.link/p0558r1)T> | VS 2017 15.3 <sup>[14](#note_14)</sup> |
| &nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2) | VS 2019 16,5 <sup> [20](#note_20)</sup> |
| &nbsp;&nbsp;[P0602R4 Propagation de la trivialité copie/déplacement dans variant/facultatif](https://wg21.link/P0602R4) | VS 2017 15.3<sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0604R0 Remplacement de is\_callable/result\_of par invoke\_result, is\_invocable, is\_nothrow\_invocable](https://wg21.link/p0604r0) | VS 2017 15.3 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0607R0 Variables inline pour la bibliothèque standard](https://wg21.link/p0607r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0618R0 Déprécier \<le codecvt>](https://wg21.link/p0618r0) | VS 2017 15.5 <sup>[17](#note_17)</sup> |
| &nbsp;&nbsp;[P0682R1 Réparation de conversions de chaînes élémentaires](https://wg21.link/P0682R1) | VS 2015 15.7 <sup>[17](#note_17)</sup> |
| __Caractéristiques de la bibliothèque standard de la C-14__ | __Pris en charge__ |
| &nbsp;&nbsp;[N3462 Utilisation de result_of compatible avec SFINAE](https://wg21.link/n3462) | VS 2015.2 |
| &nbsp;&nbsp;[N3302 constexpr pour \<complex>](https://wg21.link/n3302) | VS 2015 |
| &nbsp;&nbsp;[N3469 constexpr pour \<chrono>](https://wg21.link/n3469) | VS 2015 |
| &nbsp;&nbsp;[N3470 constexpr pour \<array>](https://wg21.link/n3470) | VS 2015 |
| &nbsp;&nbsp;[N3471 constexpr pour \<initializer_list>, \<tuple>, \<utility>](https://wg21.link/n3471) | VS 2015 |
| &nbsp;&nbsp;[N3545 integral_constant::operator()()](https://wg21.link/n3545) | VS 2015 |
| &nbsp;&nbsp;[N3642 UDL pour \<chrono>, \<string> (1729ms, "meow"s, etc.)](https://wg21.link/n3642) | VS 2015 |
| &nbsp;&nbsp;[N3644 Itérateurs « en avant » null](https://wg21.link/n3644) | VS 2015 |
| &nbsp;&nbsp;[N3654 quoted()](https://wg21.link/n3654) | VS 2015 |
| &nbsp;&nbsp;[N3657 Recherche associative hétérogène](https://wg21.link/n3657) | VS 2015 |
| &nbsp;&nbsp;[N3658 integer_sequence](https://wg21.link/n3658) | VS 2015 |
| &nbsp;&nbsp;[N3659 shared_mutex (avec contrainte de temps)](https://wg21.link/n3659) | VS 2015 |
| &nbsp;&nbsp;[N3668 exchange()](https://wg21.link/n3668) | VS 2015 |
| &nbsp;&nbsp;[N3669 Résolution des fonctions membres constexpr sans const](https://wg21.link/n3669) | VS 2015 |
| &nbsp;&nbsp;[N3670 get\<T>()](https://wg21.link/n3670) | VS 2015 |
| &nbsp;&nbsp;[N3671 equal(), is_permutation(), mismatch() à double plage](https://wg21.link/n3671) | VS 2015 |
| &nbsp;&nbsp;[Répartition de taille N3778](https://wg21.link/n3778) | VS 2015 |
| &nbsp;&nbsp;[N3779 UDL pour \<complex> (3.14i, etc.)](https://wg21.link/n3779) | VS 2015 |
| &nbsp;&nbsp;[N3789 constexpr pour \<functional>](https://wg21.link/n3789) | VS 2015 |
| &nbsp;&nbsp;[N3887 tuple_element_t](https://wg21.link/n3887) | VS 2015 |
| &nbsp;&nbsp;[N3891 Renommage de shared_mutex (avec contrainte de temps) en shared_timed_mutex](https://wg21.link/n3891) | VS 2015 |
| &nbsp;&nbsp;[N3346 Spécifications minimales d’éléments conteneurs](https://wg21.link/n3346) | VS 2013 |
| &nbsp;&nbsp;[N3421 Foncteurs d’opérateurs transparents (less\<>, etc.)](https://wg21.link/n3421) | VS 2013 |
| &nbsp;&nbsp;[N3655 Modèles d’alias pour \<type_traits> (decay_t, etc.)](https://wg21.link/n3655) | VS 2013 |
| &nbsp;&nbsp;[N3656 make_unique()](https://wg21.link/n3656) | VS 2013 |

Un groupe de documents énumérés ensemble indique une fonctionnalité Standard ainsi qu’une ou plusieurs améliorations ou agrandissements approuvés. Ces fonctionnalités sont implémentées ensemble.

### <a name="supported-values"></a>Valeurs prises en charge

__Aucun__ moyen n’est pas encore mis en œuvre.
__Partielle__ signifie que l’implémentation est incomplète. Pour plus d’informations, consultez la section Notes.
__VS 2010__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2010.
__VS 2013__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2013.
__VS 2015__ indique les fonctionnalités prises en charge dans Visual Studio 2015 (RTW).
__VS 2015.2__ et __VS 2015.3__ indiquent les fonctionnalités qui sont prises en charge dans Visual Studio 2015 Update 2 et Visual Studio 2015 Update 3, respectivement.
__VS 2017 15.0__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2017 version 15.0 (RTW).
__VS 2017 15.3__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2017 version 15.3.
__VS 2017 15.5__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2017 version 15.5.
__VS 2017 15.7__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2017 version 15.7.
__VS 2019 16.0__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2019 version 16.0 (RTW).
__VS 2019 16.1__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2019 version 16.1.
__VS 2019 16.2__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2019 version 16.2.
__VS 2019 16.3__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2019 version 16.3.
__VS 2019 16.4__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2019 version 16.4.
__VS 2019 16.5__ indique les fonctionnalités qui sont prises en charge dans Visual Studio 2019 version 16.5.

### <a name="notes"></a>Notes

<a name="note_A"></a> __A__ En mode [/std:c++14](../build/reference/std-specify-language-standard-version.md), les spécifications d’exceptions dynamiques restent non implémentées, et `throw()` est toujours traité comme un synonyme de `__declspec(nothrow)`. Dans C++17, la plupart des spécifications d’exceptions dynamiques ont été supprimées par P0003R5, laissant un vestige : `throw()` est déconseillé et doit se comporter comme synonyme de `noexcept`. En [mode /std:c-17,](../build/reference/std-specify-language-standard-version.md) MSVC se conforme désormais `throw()` à la `noexcept`norme en donnant le même comportement que, c’est-à-dire, l’application par résiliation.

L’option de compilateur [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) requiert l’ancien comportement de `__declspec(nothrow)`. Il est probable `throw()` que ce sera supprimé dans le C 20. Pour faciliter la migration de code en réponse à ces changements dans la norme et notre implémentation, de nouveaux avertissements du compilateur pour les problèmes de spécification d’exception ont été ajoutés sous [/std:c++17](../build/reference/std-specify-language-standard-version.md) et [/permissive-](../build/reference/permissive-standards-conformance.md).

<a name="note_B"></a> __B__ Pris en charge dans le mode [/permissive-](../build/reference/permissive-standards-conformance.md) dans Visual Studio 2017 15.7. Pour plus d’informations, voir [le support de recherche de noms en deux phases vient à MSVC](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/).

<a name="note_C"></a>__C__ Le support du compilateur pour les règles du préprocesseur C99 est incomplet dans Visual Studio 2017. Nous sommes en révision du préprocesseur, et a commencé à expédier ces changements dans Visual Studio 2017 version 15.8 avec le commutateur de compilateur [/expérimental:preprocessor.](../build/reference/experimental-preprocessor.md)

<a name="note_D"></a> __D__ Pris en charge sous [/std:c++14](../build/reference/std-specify-language-standard-version.md) avec un avertissement pouvant être supprimé, [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md).

<a name="note_E"></a>__E__ Il s’agit d’une `std::experimental` toute nouvelle implémentation, incompatible avec la version précédente, rendue nécessaire par le support symlink, les corrections de bogues, et les changements dans le comportement standard-requis. Actuellement, l’inclusion de \<filesystem> fournit le nouveau `std::filesystem` et le `std::experimental::filesystem` précédent, et l’inclusion de \<experimental/filesystem> fournit uniquement l’ancienne implémentation expérimentale. L’implémentation expérimentale sera supprimée de la prochaine version de rupture avec ABI des bibliothèques.

<a name="note_G"></a> __G__ Pris en charge par une fonction intrinsèque du compilateur.

<a name="note_14"></a> __14__ Ces fonctionnalités C++17/20 sont toujours activées, même quand [/std:c++14](../build/reference/std-specify-language-standard-version.md) (valeur par défaut) est spécifié. La raison en est soit parce que la fonctionnalité a été mise en œuvre avant l’introduction des options **/std,** ou parce que la mise en œuvre conditionnelle était indésirable complexe.

<a name="note_17"></a> __17__ Ces fonctionnalités sont activées par l’option du compilateur [/std:c++17](../build/reference/std-specify-language-standard-version.md) (ou [/std:c++latest](../build/reference/std-specify-language-standard-version.md)).

<a name="note_20"></a> __20__ Ces fonctionnalités sont activées par l’option du compilateur [/std:c++17](../build/reference/std-specify-language-standard-version.md). Quand l’implémentation C++20 est terminée, une nouvelle option de compilateur **/std:c++20** est ajoutée, sous laquelle ces fonctionnalités seront également disponibles.

<a name="note_byte"></a> __byte__ `std::byte` est activé par [/std:c++17](../build/reference/std-specify-language-standard-version.md) (ou [/std:c++latest](../build/reference/std-specify-language-standard-version.md)), mais étant donné qu’il peut entrer en conflit avec les en-têtes du SDK Windows dans certains cas, il comporte une macro d’annulation affinée. Il peut être désactivé en définissant `_HAS_STD_BYTE` sur `0`.

<a name="note_C11"></a> __C11__ Le CRT universel implémentait les parties de la bibliothèque standard C11 qui étaient requises par C++17, à l’exception des spécificateurs de conversion alternatifs C99 `strftime()` E/O, du mode exclusif C11 `fopen()` et de C11 `aligned_alloc()`. Ce dernier est peu susceptible d’être `aligned_alloc()` mis en œuvre, parce que `free()`C11 `free()` spécifié d’une manière qui est incompatible avec la mise en œuvre de Microsoft de: à savoir, qui doit être en mesure de gérer des allocations très alignées.

<a name="note_rem"></a> __rem__ Fonctionnalités supprimées lorsque l’option du compilateur [/std:c++17](../build/reference/std-specify-language-standard-version.md) (ou [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) est spécifiée. Ces fonctionnalités peuvent être réactivées pour faciliter la transition vers des modes de langage plus récents à l’aide des macros suivants : `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS`, et `_HAS_UNEXPECTED`.

<a name="note_charconv"></a> __charconv__ `from_chars()` et `to_chars()` sont disponibles pour les entiers. La chronologie correspondant aux virgules flottantes `from_chars()` et `to_chars()` se présente comme suit :

- VS 2017 15.7: `from_chars()` Integer et `to_chars()`.
- VS 2017 15,8: `from_chars()`Point flottant .
- VS 2017 15,9: `to_chars()` Surcharges de points flottants pour décimale la plus courte.
- VS 2019 16.0: `to_chars()` Surcharges de points flottants pour le hex le plus court et le hex de précision.
- VS 2019 16.2: `to_chars()` Surcharges de points flottants pour la précision fixe et de précision scientifique.
- VS 2019 16.4: La `to_chars()` surcharge de points flottants pour la précision générale.

<a name ="note_parallel"></a>__parallèle__ La bibliothèque d’algorithmes parallèles de C 17 est complète. Complet ne signifie pas que chaque algorithme est parallélisé dans tous les cas. Les algorithmes les plus importants ont été parallélisés, et des signatures de stratégie d’exécution sont fournies même lorsque les algorithmes ne sont pas parallélisés. L’en-tête interne central de notre implémentation, yvals_core.h, contient les « Notes d’algorithmes parallèles » suivantes : CMD permet à une implémentation d’implémenter des algorithmes parallèles comme appels aux algorithmes en série. Cette implémentation parallélise plusieurs appels d’algorithme courants, mais pas tous.

Les algorithmes suivants sont parallélisés :

- `adjacent_difference`, `adjacent_find`, `all_of`, `any_of`, `count`, `count_if`, `equal`, `exclusive_scan`, `find`, `find_end`, `find_first_of`, `find_if`, `find_if_not`, `for_each`, `for_each_n`, `inclusive_scan`, `is_heap`, `is_heap_until`, `is_partitioned`, `is_sorted`, `is_sorted_until`, `mismatch`, `none_of`, `partition`, `reduce`, `remove`, `remove_if`, `replace`, `replace_if`, `search`, `search_n`, `set_difference`, `set_intersection`, `sort`, `stable_sort`, `transform`, `transform_exclusive_scan`, `transform_inclusive_scan`, `transform_reduce`

Ce qui suit n’est pas actuellement en parallèle :

- Aucune amélioration notable des performances de parallélisme sur le matériel cible; tous les algorithmes qui ne font que copier ou permuter des éléments sans branches sont généralement limités en bande passante de mémoire :
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- Une certaine confusion existe concernant les exigences du parallélisme ; probablement dans la catégorie ci-dessus :
  - `generate`, `generate_n`
- Des soupçons existent quant à la possibilité d’établir un parallélisme efficace :
  - `partial_sort`, `partial_sort_copy`
- Pas encore évalué ; le parallélisme, qui peut être implémenté dans une version ultérieure, est censé être bénéfique :
  - `copy_if`, `includes`, `inplace_merge`, `lexicographical_compare`, `max_element`, `merge`, `min_element`, `minmax_element`, `nth_element`, `partition_copy`, `remove_copy`, `remove_copy_if`, `replace_copy`, `replace_copy_if`, `set_symmetric_difference`, `set_union`, `stable_partition`, `unique`, `unique_copy`

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)\
[Bibliothèque standard de CMD](../standard-library/cpp-standard-library-reference.md)\
[Améliorations de conformité de CMD dans Visual Studio](cpp-conformance-improvements.md)\
[Quoi de neuf pour Visual CMD dans Visual Studio](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visuel C 'changement histoire 2003 à 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Visuel CMD Quoi de neuf de 2003 à 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[Blog de l’équipe C++](https://devblogs.microsoft.com/cppblog/)
