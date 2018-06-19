---
title: Erreurs du compilateur C2600 à C2699 | Documents Microsoft
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
helpviewer_keywords:
- C2604
- C2606
- C2607
- C2608
- C2609
- C2610
- C2615
- C2618
- C2620
- C2621
- C2622
- C2623
- C2625
- C2629
- C2631
- C2639
- C2641
- C2642
- C2643
- C2644
- C2684
- C2685
- C2686
- C2697
dev_langs:
- C++
ms.assetid: 73c6319f-cbea-4a2f-913b-90dc1af61f64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0637ff146ca71c1ee14c534792cf70c44c0616b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283352"
---
# <a name="compiler-errors-c2600-through-c2699"></a>Erreurs du compilateur de C2600 à C2699

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C2600](compiler-error-c2600.md)|'*fonction*' : Impossible de définir une fonction membre spéciale générée par le compilateur (doit être déclarée d’abord dans la classe)|
|[Erreur du compilateur C2601](compiler-error-c2601.md)|'*fonction*' : les définitions de fonction locale ne sont pas autorisées|
|[Erreur du compilateur C2602](compiler-error-c2602.md)|'*classe*::*identificateur*'n’est pas un membre de classe de base de'*classe*'|
|[Erreur du compilateur C2603](compiler-error-c2603.md)|'*fonction*' : trop d’objets static de portée de bloc avec constructeur/destructeurs dans la fonction|
|C2604 d’erreur du compilateur|'*identificateur*' : ne peut pas implémenter plus d’une méthode d’interface|
|[Erreur du compilateur C2605](compiler-error-c2605.md)|'*identificateur*' : cette méthode est réservée dans une classe gérée/WinRT|
|C2606 d’erreur du compilateur|'*class1*' : Impossible de réimplémenter '*membre*', car il est hérité du runtime de base'*classe2*'|
|C2607 d’erreur du compilateur|échoué de l’assertion statique|
|C2608 d’erreur du compilateur|Obsolète.|
|C2609 d’erreur du compilateur|Obsolète.|
|C2610 d’erreur du compilateur|'*classe*::*membre*' : n’est pas une fonction membre spéciale qui peut être définie par défaut|
|[Erreur du compilateur C2611](compiler-error-c2611.md)|'*jeton*' : non conforme après ' ~' (identificateur attendu)|
|[Erreur du compilateur C2612](compiler-error-c2612.md)|de fin '*caractère*' non conforme dans une liste d’initialiseurs de base/membre|
|[Erreur du compilateur C2613](compiler-error-c2613.md)|de fin '*caractère*' non conforme dans une liste de classes de base|
|[Erreur du compilateur C2614](compiler-error-c2614.md)|'*classe*' : l’initialisation de membre non conforme : '*identificateur*' n’est pas une base ni un membre|
|C2615 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2616](compiler-error-c2616.md)|'*conversion*' : Impossible de convertir implicitement une non-lvalue '*type1*' à un '*type2*' qui n’est pas const|
|[Erreur du compilateur C2617](compiler-error-c2617.md)|'*fonction*' : instruction return incohérente|
|C2618 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2619](compiler-error-c2619.md)|'*identificateur*' : une donnée membre static n’est pas autorisée dans une struct/union anonyme|
|Erreur du compilateur C2620|Obsolète.|
|Erreur du compilateur C2621|Obsolète.|
|Erreur du compilateur C2622|Obsolète.|
|Erreur du compilateur C2623|Obsolète.|
|[Erreur du compilateur C2624](compiler-error-c2624.md)|'*étendue*::*type*' : les classes locales ne peut pas être utilisés pour déclarer des variables 'extern'|
|C2625 d’erreur du compilateur|'*identificateur*' : membre d’union illégal ; le type '*type*' est de type référence|
|[Erreur du compilateur C2626](compiler-error-c2626.md)|'*identificateur*' : un membre de données privé/protégées n’est pas autorisé dans une struct/union anonyme|
|[Erreur du compilateur C2627](compiler-error-c2627.md)|'*fonction*' : fonction membre non autorisée dans une union anonyme|
|[Erreur du compilateur C2628](compiler-error-c2628.md)|'*type1*'suivi de'*type2*' n’est pas conforme (n’auriez-vous pas oublié un ';' ?)|
|C2629 d’erreur du compilateur|'*identificateur*' : une struct/union anonyme ne peut pas déclarer un type imbriqué|
|[Erreur du compilateur C2630](compiler-error-c2630.md)|'*symbole*' trouvé à la place d’une liste séparée par des virgules|
|C2631 d’erreur du compilateur|'*identificateur*' : une classe ou une enum ne peut pas être définie dans un modèle d’alias|
|[Erreur du compilateur C2632](compiler-error-c2632.md)|'*type1*'suivi de'*type2*' n’est pas autorisé|
|[Erreur du compilateur C2633](compiler-error-c2633.md)|'*identificateur*' : 'inline' est la classe de stockage autorisée uniquement pour les constructeurs|
|[Erreur du compilateur C2634](compiler-error-c2634.md)|'*classe*::*membre*' : pointeur vers membre de référence non conforme|
|[Erreur du compilateur C2635](compiler-error-c2635.md)|Impossible de convertir un '*type1*\*' à un '*type2*\*' ; conversion à partir de la classe de base virtuelle implicite|
|[Erreur du compilateur C2636](compiler-error-c2636.md)|'*identificateur*' : pointeur vers membre de référence non conforme|
|[Erreur du compilateur C2637](compiler-error-c2637.md)|'*identificateur*' : ne peut pas modifier les pointeurs sur données membres|
|[Erreur du compilateur C2638](compiler-error-c2638.md)|'*identificateur*' : modificateur __based non conforme sur pointeur vers membre|
|C2639 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2640](compiler-error-c2640.md)|'*identificateur*' : modificateur __based non conforme sur une référence|
|C2641 d’erreur du compilateur|Obsolète.|
|C2642 d’erreur du compilateur|Obsolète.|
|C2643 d’erreur du compilateur|Obsolète.|
|C2644 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2645](compiler-error-c2645.md)|Aucun nom qualifié pour un pointeur vers membre (trouvé ' :: *')|
|[Erreur du compilateur C2646](compiler-error-c2646.md)|un struct/union anonyme au niveau global ou la portée espace de noms doit être déclarée statique|
|[Erreur du compilateur C2647](compiler-error-c2647.md)|'*opérateur*' : Impossible de déréférencer un '*type1*' sur un '*type2*'|
|[Erreur du compilateur C2648](compiler-error-c2648.md)|'*identificateur*' : utilisation d’un membre comme paramètre par défaut nécessite un membre statique|
|[Erreur du compilateur C2649](compiler-error-c2649.md)|'*identificateur*' : n’est pas un 'class/struct/union'|
|[Erreur du compilateur C2650](compiler-error-c2650.md)|'*opérateur*' : ne peut pas être une fonction virtuelle|
|[Erreur du compilateur C2651](compiler-error-c2651.md)|'*type*' : gauche de ' ::' doit être une classe, struct ou une union|
|[Erreur du compilateur C2652](compiler-error-c2652.md)|'*identificateur*' : constructeur de copie non conforme : premier paramètre ne doit pas être un '*type*'|
|[Erreur du compilateur C2653](compiler-error-c2653.md)|'*identificateur*' : n’est pas un nom de classe ou espace de noms|
|[Erreur du compilateur C2654](compiler-error-c2654.md)|'*identificateur*' : tentative d’accéder à un membre en dehors d’une fonction membre|
|[Erreur du compilateur C2655](compiler-error-c2655.md)|'*identificateur*' : définition ou redéclaration non conforme dans la portée actuelle|
|[Erreur du compilateur C2656](compiler-error-c2656.md)|'*fonction*' : fonction non autorisée comme champ de bits|
|[Erreur du compilateur C2657](compiler-error-c2657.md)|'*classe*:: *' trouvé au début d’une instruction (vous avez oublié de spécifier un type ?)|
|[Erreur du compilateur C2658](compiler-error-c2658.md)|'*identificateur*' : redéfinition dans un struct/union anonyme|
|[Erreur du compilateur C2659](compiler-error-c2659.md)|'*opérateur*' : fonction comme opérande gauche|
|[Erreur du compilateur C2660](compiler-error-c2660.md)|'*fonction*' : fonction n’accepte pas *nombre* arguments|
|[Erreur du compilateur C2661](compiler-error-c2661.md)|'*fonction*' : aucune fonction surchargée ne nécessite *nombre* arguments|
|[Erreur du compilateur C2662](compiler-error-c2662.md)|'*fonction*' : Impossible de convertir un pointeur 'this' de '*type1*'à'*type2*'|
|[Erreur du compilateur C2663](compiler-error-c2663.md)|'*fonction*' : *nombre* surcharges n’ont pas de conversion autorisée pour le pointeur 'this'|
|[Erreur du compilateur C2664](compiler-error-c2664.md)|'*fonction*' : Impossible de convertir l’argument *nombre* à partir de '*type1*'à'*type2*'|
|[Erreur du compilateur C2665](compiler-error-c2665.md)|'*fonction*' : aucune de la *nombre* surcharges a pu convertir tous les types d’argument|
|[Erreur du compilateur C2666](compiler-error-c2666.md)|'*fonction*' : *nombre* surcharges ont des conversions similaires|
|[Erreur du compilateur C2667](compiler-error-c2667.md)|'*fonction*' : aucun des *nombre* surcharges ont une meilleure conversion|
|[Erreur du compilateur C2668](compiler-error-c2668.md)|'*fonction*' : appel ambigu à une fonction surchargée|
|[Erreur du compilateur C2669](compiler-error-c2669.md)|fonction membre non autorisée dans une union anonyme|
|[Erreur du compilateur C2670](compiler-error-c2670.md)|'*fonction*' : le modèle de fonction ne peut pas convertir le paramètre *nombre* à partir du type '*type*'|
|[Erreur du compilateur C2671](compiler-error-c2671.md)|'*fonction*' : les fonctions membres statiques n’ont pas de pointeurs 'this'|
|[C2672 d’erreur du compilateur](compiler-error-c2672.md)|'*fonction*' : aucune correspondance de trouver la fonction ne surchargée|
|[Erreur du compilateur C2673](compiler-error-c2673.md)|'*fonction*' : les fonctions globales n’ont pas de pointeurs 'this'|
|[Erreur du compilateur C2674](compiler-error-c2674.md)|une déclaration générique n’est pas autorisée dans ce contexte|
|[Erreur du compilateur C2675](compiler-error-c2675.md)|unaire '*opérateur*' : '*type*' ne définit pas cet opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini|
|[Erreur du compilateur C2676](compiler-error-c2676.md)|binaire '*opérateur*' : '*type*' ne définit pas cet opérateur ou une conversion vers un type acceptable pour l’opérateur prédéfini|
|[Erreur du compilateur C2677](compiler-error-c2677.md)|binaire '*opérateur*' : aucun opérateur global trouvé qui accepte le type '*type*' (ou il n’existe aucune conversion acceptable)|
|[Erreur du compilateur C2678](compiler-error-c2678.md)|binaire '*opérateur*' : aucun opérateur ne trouvé qui accepte un opérande de partie gauche de type '*type*' (ou il n’existe aucune conversion acceptable)|
|[Erreur du compilateur C2679](compiler-error-c2679.md)|binaire '*opérateur*' : aucun opérateur trouvé qui accepte un opérande de droit de type '*type*' (ou il n’existe aucune conversion acceptable)|
|[Erreur du compilateur C2680](compiler-error-c2680.md)|'*type*' : type de cible non valide pour *cast*|
|[Erreur du compilateur C2681](compiler-error-c2681.md)|'*type*' : type d’expression non valide pour *cast*|
|[Erreur du compilateur C2682](compiler-error-c2682.md)|Impossible d’utiliser '*cast*' pour convertir'*type1*'à'*type2*'|
|[Erreur du compilateur C2683](compiler-error-c2683.md)|'*cast*' : '*type*' n’est pas un type polymorphe|
|C2684 d’erreur du compilateur|'*déclarateur*' : les fonctions supprimées et définies par défaut ne sont pas pris en charge dans les classes managées/WinRT|
|C2685 d’erreur du compilateur|'*déclarateur*' : les fonctions supprimées et définies par défaut ne sont pas pris en charge avec les spécificateurs de restriction explicites|
|C2686 d’erreur du compilateur|Impossible de surcharger des fonctions membres statiques et non statiques avec les mêmes types de paramètre|
|[Erreur du compilateur C2687](compiler-error-c2687.md)|'*type*' : déclaration d’exception ne peut pas être 'void' ou désigner un type incomplet ou pointeur ou une référence à un type incomplet|
|[Erreur du compilateur C2688](compiler-error-c2688.md)|'*type*::*membre*' : retours covariants avec plusieurs ou l’héritage virtuel non pris en charge pour les fonctions varargs|
|[Erreur du compilateur C2689](compiler-error-c2689.md)|'*fonction*' : une fonction friend ne peut pas être définie dans une classe locale|
|[Erreur du compilateur C2690](compiler-error-c2690.md)|'*opérateur*' : ne peut pas effectuer une opération arithmétique de pointeur sur un tableau managé/WinRT|
|[Erreur du compilateur C2691](compiler-error-c2691.md)|'*type*' : un tableau managé/WinRT ne peut pas avoir ce type d’élément|
|[Erreur du compilateur C2692](compiler-error-c2692.md)|'*fonction*' : fonctions entièrement prototypées requises dans le compilateur C avec le ' / clr' option|
|[Erreur du compilateur C2693](compiler-error-c2693.md)|'*opérateur*' : comparaison non conforme entre des références et un tableau managé/WinRT|
|[Erreur du compilateur C2694](compiler-error-c2694.md)|'*fonction_substitution*' : fonction virtuelle de substitution a des spécifications d’exception moins restrictive que la fonction membre virtuelle de classe de base '*fonction_base*'|
|[Erreur du compilateur C2695](compiler-error-c2695.md)|'*fonction_substitution*' : fonction virtuelle de substitution diffère de '*fonction_base*' que par la convention d’appel|
|[Erreur du compilateur C2696](compiler-error-c2696.md)|Impossible de créer un objet temporaire de type géré/WinRT '*type*'|
|Erreur du compilateur C2697|Obsolète.|
|[Erreur du compilateur C2698](compiler-error-c2698.md)|la déclaration using pour '*déclaration1*'ne peuvent pas coexister avec la déclaration using existante pour'*déclaration2*'|
