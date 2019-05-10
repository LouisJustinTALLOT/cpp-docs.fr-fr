---
title: Erreurs du compilateur C2500 à C2599
ms.date: 04/21/2019
f1_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
helpviewer_keywords:
- C2501
- C2508
- C2515
- C2519
- C2520
- C2522
- C2525
- C2527
- C2536
- C2538
- C2539
- C2546
- C2547
- C2559
- C2560
- C2564
- C2565
- C2576
- C2578
- C2580
- C2590
- C2591
- C2595
- C2596
ms.assetid: a869aaed-e9f6-49e3-b273-00ea7f45bed7
ms.openlocfilehash: 87728c2d7055715b7e7d986d5ab8792ceba5c450
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857080"
---
# <a name="compiler-errors-c2500-through-c2599"></a>Erreurs du compilateur C2500 à C2599

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur qui sont générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C2500](compiler-error-C2500.md)|«*identificateur1*' : '*identificateur2*' est déjà une classe de base directe|
|Erreur du compilateur C2501|'*identificateur*' : ' __declspec (*spécificateur*)' peut uniquement être appliqué pour les structures, unions, classes ou membres de champ de bits non signé|
|[Erreur du compilateur C2502](compiler-error-C2502.md)|«*identificateur*' : trop de modificateurs d’accès sur la classe de base|
|[Erreur du compilateur C2503](compiler-error-C2503.md)|«*classe*' : les classes de base ne peut pas contenir de tableaux de taille zéro|
|[Erreur du compilateur C2504](compiler-error-C2504.md)|«*classe*' : non défini de classe de base|
|[Erreur du compilateur C2505](compiler-error-C2505.md)|«*symbole*' : ' __declspec (*spécificateur*)' peut uniquement être appliqué aux déclarations ou définitions d’objets globaux ou de données membres static|
|[Erreur du compilateur C2506](compiler-error-C2506.md)|«*membre*' : ' __declspec (*spécificateur*)' ne peut pas être appliqué à ce symbole|
|[Erreur du compilateur C2507](compiler-error-C2507.md)|«*identificateur*' : modificateurs virtuels sur la classe de base trop nombreux|
|Erreur du compilateur C2508|«*identificateur*' : ' __declspec (*spécificateur1*)' ne peut pas être combiné avec ' __declspec (*spécificateur2*) »|
|[Erreur du compilateur C2509](compiler-error-C2509.md)|«*identificateur*' : fonction membre non déclarée dans '*classe*»|
|[Erreur du compilateur C2510](compiler-error-C2510.md)|«*identificateur*' : gauche de ' ::' doit être class/struct/union|
|[Erreur du compilateur C2511](compiler-error-C2511.md)|«*identificateur*' : introuvable dans la fonction membre surchargée '*classe*»|
|[Erreur du compilateur C2512](compiler-error-C2512.md)|«*identificateur*' : aucun constructeur par défaut approprié disponible|
|[Erreur du compilateur C2513](compiler-error-C2513.md)|'*type': no variable declared before '='|
|[Erreur du compilateur C2514](compiler-error-C2514.md)|«*classe*' : classe n’a aucun constructeur|
|Erreur du compilateur C2515|«*identificateur*' : 'vtguard' peut uniquement être appliqué aux définitions ou déclarations de classe|
|[Erreur du compilateur C2516](compiler-error-C2516.md)|«*classe*' : n’est pas une classe de base juridique|
|[Erreur du compilateur C2517](compiler-error-C2517.md)|«*identificateur*' : droite de ' ::' n’est pas défini|
|[Erreur du compilateur C2518](compiler-error-C2518.md)|keyword '*keyword*' illegal in base class list; ignored|
|Erreur du compilateur C2519|«*identificateur*» : Les attributs WinRT peuvent contenir uniquement des champs publics|
|Erreur du compilateur C2520|«*classe*' : aucun constructeur non explicite disponible pour la conversion implicite|
|[Erreur du compilateur C2521](compiler-error-C2521.md)|un destructeur/finaliseur n’accepte pas d’arguments|
|Erreur du compilateur C2522|«*identificateur*» : Identificateur de surcharge ne peut pas être utilisé sur '*identificateur1*'car il est déjà spécifié sur'*identificateur2*'|
|[Erreur du compilateur C2523](compiler-error-C2523.md)|«*classe*:: ~*identificateur*' : incompatibilité de balise de destructeur/finaliseur|
|[Erreur du compilateur C2524](compiler-error-C2524.md)|«*identificateur*' : un destructeur/finaliseur doit avoir une liste de paramètres 'void'|
|Erreur du compilateur C2525|«*identificateur*» : Le paramètre '*identificateur1*'nommé'*identificateur2*» sur la base de fonction et doit être mise en correspondance dans une implémentation publiée|
|[Erreur du compilateur C2526](compiler-error-C2526.md)|«*identificateur1*» : Fonction de liaison C ne peut pas retourner C++ classe*identificateur2*'|
|Erreur du compilateur C2527|«*identificateur*» : Impossible de spécifier defaultoverload pour à la fois sur «*function1*'et'*function2*». Supprimez une spécification ou renommez la fonction lors de l’implémentation|
|[Erreur du compilateur C2528](compiler-error-C2528.md)|«*identificateur*' : pointeur vers la référence n’est pas conforme|
|[Erreur du compilateur C2529](compiler-error-C2529.md)|«*identificateur*' : référence à une référence n’est pas conforme|
|[Erreur du compilateur C2530](compiler-error-C2530.md)|«*identificateur*' : les références doivent être initialisées|
|[Erreur du compilateur C2531](compiler-error-C2531.md)|«*identificateur*' : référence à un peu non conforme de champ|
|[Erreur du compilateur C2532](compiler-error-C2532.md)|«*identificateur*' : modificateur non conforme pour la référence|
|[Erreur du compilateur C2533](compiler-error-C2533.md)|«*identificateur*' : un type de retour non autorisés de constructeurs|
|[Erreur du compilateur C2534](compiler-error-C2534.md)|«*identificateur*' : constructeur ne peut pas retourner une valeur|
|[Erreur du compilateur C2535](compiler-error-C2535.md)|«*identificateur*' : fonction membre déjà définie ou déclarée|
|Erreur du compilateur C2536|Obsolète.|
|[Erreur du compilateur C2537](compiler-error-C2537.md)|«*spécificateur*' : spécification de liaison non conforme|
|Erreur du compilateur C2538|Obsolète.|
|Erreur du compilateur C2539|Obsolète.|
|[Erreur du compilateur C2540](compiler-error-C2540.md)|expression non constante comme limite de tableau|
|[Erreur du compilateur C2541](compiler-error-C2541.md)|«*identificateur*' : Impossible de supprimer les objets qui ne sont pas des pointeurs|
|[Erreur du compilateur C2542](compiler-error-C2542.md)|«*identificateur*' : objet de classe n’a aucun constructeur pour l’initialisation|
|[Erreur du compilateur C2543](compiler-error-C2543.md)|attendu ']' pour l’opérateur « [] »|
|[Erreur du compilateur C2544](compiler-error-C2544.md)|attendu ')' pour l’opérateur « () »|
|[Erreur du compilateur C2545](compiler-error-C2545.md)|«*opérateur*' : Impossible de trouver l’opérateur surchargé|
|Erreur du compilateur C2546|«*identificateur*' : quand un type est défini dans un assembly PIA et un assembly non-PIA l’assembly PIA doit être référencé tout d’abord|
|Erreur du compilateur C2547|«*identificateur*» : Tous les paramètres d’une méthode publiée doivent être nommés explicitement sur la déclaration|
|[Erreur du compilateur C2548](compiler-error-C2548.md)|«*fonction*' : paramètre par défaut pour le paramètre manquant *paramètre*|
|[Erreur du compilateur C2549](compiler-error-C2549.md)|conversion définie par l’utilisateur ne peut pas spécifier un type de retour|
|[Erreur du compilateur C2550](compiler-error-C2550.md)|«*identificateur*' : listes d’initialiseurs de constructeur sont autorisés uniquement sur la définition d’un constructeur|
|[Erreur du compilateur C2551](compiler-error-C2551.md)|le type 'void *' nécessite un cast explicite|
|[Erreur du compilateur C2552](compiler-error-C2552.md)|«*identificateur*' : pas des agrégats ne peuvent pas être initialisés avec une liste d’initialiseurs|
|[Erreur du compilateur C2553](compiler-error-C2553.md)|«*type* *derived_class*::*fonction*' : type de retour de fonction virtuelle de substitution diffère de '*type* *base_ classe*::*fonction*'|
|[Erreur du compilateur C2555](compiler-error-C2555.md)|«*derived_class*::*fonction*' : fonction virtuelle de substitution type de retour est différent et n’est pas covariant '*base_class*::*fonction*'|
|[Erreur du compilateur C2556](compiler-error-C2556.md)|«*type1* *classe*::*fonction*' : fonction surchargée ne diffère uniquement par le type de retour de '*type2* *classe*::*fonction*'|
|[Erreur du compilateur C2557](compiler-error-C2557.md)|«*identificateur*' : Impossible d’initialiser des membres privés et protégés sans un constructeur|
|[Erreur du compilateur C2558](compiler-error-C2558.md)|la classe*classe*' : aucun constructeur de copie disponible ou le constructeur de copie n’est déclaré 'explicit'|
|Erreur du compilateur C2559|«*identificateur*' : Impossible de surcharger une fonction membre sans qualificateur ref avec une fonction membre avec un qualificateur ref|
|Erreur du compilateur C2560|«*identificateur*' : Impossible de surcharger une fonction membre avec un qualificateur ref avec une fonction membre sans qualificateur ref|
|[Erreur du compilateur C2561](compiler-error-C2561.md)|«*fonction*' : fonction doit retourner une valeur|
|[Erreur du compilateur C2562](compiler-error-C2562.md)|«*fonction*' : fonction 'void' retournant une valeur|
|[Erreur du compilateur C2563](compiler-error-C2563.md)|incompatibilité dans la liste de paramètres formels|
|Erreur du compilateur C2564|Obsolète.|
|Erreur du compilateur C2565|«*identificateur*' : qualificateur ref est illégal pour les constructeurs/destructeurs|
|[Erreur du compilateur C2566](compiler-error-C2566.md)|fonction surchargée dans une expression conditionnelle|
|[Erreur du compilateur C2567](compiler-error-C2567.md)|Impossible d’ouvrir les métadonnées dans '*filename*», *possible_reason*|
|[Erreur du compilateur C2568](compiler-error-C2568.md)|«*identificateur*' : Impossible de résoudre la surcharge de fonction|
|[Erreur du compilateur C2569](compiler-error-C2569.md)|«*identificateur*' : enum/union ne peut pas être utilisée comme classe de base|
|[Erreur du compilateur C2570](compiler-error-C2570.md)|«*identificateur*' : union ne peut pas avoir de classes de base|
|[Erreur du compilateur C2571](compiler-error-C2571.md)|«*identificateur*' : fonction virtuelle ne peut pas figurer dans l’union '*union*»|
|[Erreur du compilateur C2572](compiler-error-C2572.md)|«*fonction*' : redéfinition de l’argument par défaut : paramètre *nombre*|
|[Erreur du compilateur C2573](compiler-error-C2573.md)|«*classe*' : ne peut pas supprimer les pointeurs vers les objets de ce type ; la classe n’a aucune surcharge de non-positionnement pour 'operator delete'. Utilisez :: delete ou ajoutez 'opérateur delete(void*)' à la classe|
|[Erreur du compilateur C2574](compiler-error-C2574.md)|«*destructeur*' : ne peut pas être déclaré static|
|[Erreur du compilateur C2575](compiler-error-C2575.md)|«*identificateur*' : seules les fonctions membres et les bases peuvent être virtuelles|
|Erreur du compilateur C2576|«*identificateur*' : ne peut pas introduire une nouvelle méthode virtuelle 'public'. Envisagez de faire de la méthode non virtuelle ou modifier l’accessibilité en 'internal' ou 'protected private'|
|[Erreur du compilateur C2577](compiler-error-C2577.md)|«*identificateur*' : un destructeur/finaliseur ne peut pas avoir un type de retour|
|Erreur du compilateur C2578|«*classe*' : type ne peut pas avoir un 'protected' ou le constructeur 'protected public'|
|[Erreur du compilateur C2579](compiler-error-C2579.md)|Impossible de résoudre le type *type* (*décalage*). Il est prévu dans *nom de fichier*|
|Erreur du compilateur C2580|«*identificateur*' : plusieurs versions d’une fonction membre spéciale par défaut ne sont pas autorisées.|
|[Erreur du compilateur C2581](compiler-error-C2581.md)|«*type*' : statique ' opérateur = « fonction n’est pas conforme|
|[Erreur du compilateur C2582](compiler-error-C2582.md)|' opérateur *opérateur*« (fonction) n’est pas disponible dans »*type*'|
|[Erreur du compilateur C2583](compiler-error-C2583.md)|«*identificateur*' : ' const/volatile' pointeur 'this' est non conforme pour les constructeurs/destructeurs|
|[Erreur du compilateur C2584](compiler-error-C2584.md)|«*classe*' : base directe '*base_class2*' n’est pas accessible ; déjà une base de '*base_class1*»|
|[Erreur du compilateur C2585](compiler-error-C2585.md)|la conversion explicite vers '*type*' est ambigu|
|[Erreur du compilateur C2586](compiler-error-C2586.md)|syntaxe de conversion définie par l’utilisateur incorrecte : indirections non conformes|
|[Erreur du compilateur C2587](compiler-error-C2587.md)|«*identificateur*' : utilisation non conforme d’une variable locale comme paramètre par défaut|
|[Erreur du compilateur C2588](compiler-error-C2588.md)|' :: ~*identificateur*' : non conforme de global destructeur/finaliseur|
|[Erreur du compilateur C2589](compiler-error-C2589.md)|«*identificateur*' : jeton non conforme à droite de ' :: »|
|Erreur du compilateur C2590|«*identificateur*' : seul un constructeur peut avoir une liste d’initialiseurs de base/membre|
|Erreur du compilateur C2591|ExclusiveTo ne peut pas utiliser '*type*» en tant qu’argument. Uniquement un 'ref class' est un argument valide|
|[Erreur du compilateur C2592](compiler-error-C2592.md)|«*classe*' : '*base_class2*'héritée'*base_class1*' et ne peut pas être spécifié de nouveau|
|[Erreur du compilateur C2593](compiler-error-C2593.md)|' opérateur *identificateur*' est ambigu|
|[Erreur du compilateur C2594](compiler-error-C2594.md)|«*opérateur*' : conversions ambiguës de '*type1*'en'*type2*»|
|Erreur du compilateur C2595|«*identificateur*' WinRT d’un type d’attribut doit être sealed|
|Erreur du compilateur C2596|«*identificateur*' WinRT d’un champ d’attribut peut uniquement être un 'public enum class', 'int', 'unsigned int', 'bool', 'Platform::Type', 'Platform::String' ou 'Windows : Foundation :: HResult'|
|[Erreur du compilateur C2597](compiler-error-C2597.md)|référence non conforme à un membre non statique '*identificateur*'|
|[Erreur du compilateur C2598](compiler-error-C2598.md)|spécification de liaison doit être portée globale|
|[Erreur du compilateur C2599](compiler-error-C2599.md)|«*identificateur*' : la déclaration anticipée d’un enum WinRT/géré n’est pas autorisée.|

## <a name="see-also"></a>Voir aussi

[C /C++ compilateur et build erreurs et avertissements des outils](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
