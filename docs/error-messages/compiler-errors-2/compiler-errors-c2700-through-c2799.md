---
title: Erreurs du compilateur C2700 à C2799
ms.date: 04/21/2019
f1_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
helpviewer_keywords:
- C2716
- C2717
- C2727
- C2729
- C2737
- C2740
- C2741
- C2742
- C2744
- C2746
- C2747
- C2759
- C2763
- C2769
- C2772
- C2789
- C2796
- C2799
ms.assetid: 6ee257bb-94bc-42b9-af2c-3c73926afba4
ms.openlocfilehash: 174f6a9c8ec9e44deadfca090ba492cb32d53e9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197512"
---
# <a name="compiler-errors-c2700-through-c2799"></a>Erreurs du compilateur C2700 à C2799

Les Articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C2700](compiler-error-c2700.md)|'*type*' : ne peut pas être levé (utilisez/W4 pour plus d’informations)|
|[Erreur du compilateur C2701](compiler-error-c2701.md)|'*fonction*' : un modèle de fonction/générique ne peut pas être friend d’une classe locale|
|[Erreur du compilateur C2702](compiler-error-c2702.md)| __except peut ne pas apparaître dans le bloc de fin|
|[Erreur du compilateur C2703](compiler-error-c2703.md)|instruction __leave non conforme|
|[Erreur du compilateur C2704](compiler-error-c2704.md)|'*fonction*' : __va_start intrinsèque autorisé uniquement dans les varargs|
|[Erreur du compilateur C2705](compiler-error-c2705.md)|'*étiquette*' : saut dans la portée'*exception_block*'non conforme|
|[Erreur du compilateur C2706](compiler-error-c2706.md)|__except non conforme sans __try de correspondance ('} 'manquant dans __try bloc ?)|
|[Erreur du compilateur C2707](compiler-error-c2707.md)|'*identificateur*' : contexte incorrect pour une fonction intrinsèque|
|[Erreur du compilateur C2708](compiler-error-c2708.md)|'*identificateur*' : la longueur des paramètres réels en octets diffère de l’appel ou de la référence précédent|
|[Erreur du compilateur C2709](compiler-error-c2709.md)|'*identificateur*' : la longueur en octets des paramètres formels diffère de celle de la déclaration précédente|
|[Erreur du compilateur C2710](compiler-error-c2710.md)|'*identificateur*' : ' __declspec (*modificateur*) 'ne peut s’appliquer qu’à une fonction qui retourne un pointeur|
|[Erreur du compilateur C2711](compiler-error-c2711.md)|'*fonction*' : cette fonction ne peut pas être compilée comme managée, envisagez d’utiliser #pragma non managé|
|[Erreur du compilateur C2712](compiler-error-c2712.md)|Impossible d’utiliser __try dans les fonctions qui requièrent le déroulement de l’objet|
|[Erreur du compilateur C2713](compiler-error-c2713.md)|Une seule forme de gestion des exceptions permise par fonction|
|[Erreur du compilateur C2714](compiler-error-c2714.md)| `alignof(void)`n’est pas autorisé|
|[Erreur du compilateur C2715](compiler-error-c2715.md)|'*type*' : impossible de lever ou d’intercepter ce type|
|Erreur du compilateur C2716|Obsolète.|
|Erreur du compilateur C2717|Obsolète.|
|[Erreur du compilateur C2718](compiler-error-c2718.md)|'*type*' : le paramètre réel avec l’alignement demandé du *nombre* ne sera pas aligné|
|[Erreur du compilateur C2719](compiler-error-c2719.md)|'*paramètre*' : le paramètre formel avec l’alignement demandé du *nombre* ne sera pas aligné|
|[Erreur du compilateur C2720](compiler-error-c2720.md)|'*identificateur*' : spécificateur de classe de stockage'*specifier*'non conforme sur les membres|
|[Erreur du compilateur C2721](compiler-error-c2721.md)|'*specifier*' : spécificateur de classe de stockage non conforme entre le type et le mot clé Operator|
|[Erreur du compilateur C2722](compiler-error-c2722.md)|' ::*Operator*' : la commande d’opérateur suivante n’est pas conforme ; Utilisez’operator *opérateur*'|
|[Erreur du compilateur C2723](compiler-error-c2723.md)|'*fonction*' : spécificateur'*specifier*'non conforme sur la définition d’une fonction|
|[Erreur du compilateur C2724](compiler-error-c2724.md)|'*fonction*' : 'static’ne doit pas être utilisé sur les fonctions membres définies au niveau de la portée du fichier|
|[Erreur du compilateur C2725](compiler-error-c2725.md)|'*type*' : impossible de lever ou d’intercepter un objet managé/WinRT par valeur ou référence|
|[Erreur du compilateur C2726](compiler-error-c2726.md)|'gcnew’peut uniquement être utilisé pour créer un objet avec un type managé/WinRT|
|Erreur du compilateur C2727|Obsolète.|
|[Erreur du compilateur C2728](compiler-error-c2728.md)|'*type*' : un tableau natif ne peut pas contenir ce type|
|Erreur du compilateur C2729|Obsolète.|
|[Erreur du compilateur C2730](compiler-error-c2730.md)|'*Class*' : ne peut pas être une classe de base d’elle-même|
|[Erreur du compilateur C2731](compiler-error-c2731.md)|'*fonction*' : la fonction ne peut pas être surchargée|
|[Erreur du compilateur C2732](compiler-error-c2732.md)|la spécification de la liaison contredit les spécifications antérieures pour'*Function*'|
|[Erreur du compilateur C2733](compiler-error-c2733.md)|'*fonction*' : seconde liaison C d’une fonction surchargée non autorisée|
|[Erreur du compilateur C2734](compiler-error-c2734.md)|'*identificateur*' : l’objet’const’doit être initialisé s’il n’est pas’extern'|
|[Erreur du compilateur C2735](compiler-error-c2735.md)|le mot clé'*Keyword*'n’est pas autorisé dans le spécificateur de type de paramètre formel|
|[Erreur du compilateur C2736](compiler-error-c2736.md)|le mot clé'*Keyword*'n’est pas autorisé dans un cast|
|Erreur du compilateur C2737|'*identificateur*' : l’objet’constexpr’doit être initialisé|
|[Erreur du compilateur C2738](compiler-error-c2738.md)|'operator *type*' : est ambigu ou n’est pas un membre de'*Class*'|
|[Erreur du compilateur C2739](compiler-error-c2739.md)|'*nombre*' : les dimensions de tableau managé/WinRT explicites doivent être comprises entre 1 et 32|
|Erreur du compilateur C2740|la valeur de l’opérande'*Number*'est hors limites'*lower_bound*  -  *upper_bound*'|
|Erreur du compilateur C2741|taille du frame trop grande|
|Erreur du compilateur C2742|Obsolète.|
|[Erreur du compilateur C2743](compiler-error-c2743.md)|'*type*' : impossible d’intercepter un type natif avec __clrcall destructeur ou un constructeur de copie|
|Erreur du compilateur C2744|'*Operator*'n’est pas un opérateur CLR/WinRT valide|
|[Erreur du compilateur C2745](compiler-error-c2745.md)|'*Token*' : ce jeton ne peut pas être converti en identificateur|
|Erreur du compilateur C2746|Obsolète.|
|Erreur du compilateur C2747|Obsolète.|
|[Erreur du compilateur C2748](compiler-error-c2748.md)|la création d’un tableau managé/WinRT doit avoir une taille de tableau ou un initialiseur de tableau|
|[Erreur du compilateur C2749](compiler-error-c2749.md)|'*type*' : peut uniquement lever ou intercepter un handle d’une classe managée avec/clr : safe|
|[Erreur du compilateur C2750](compiler-error-c2750.md)|'*type*' : impossible d’utiliser’New’sur le type référence ; Utilisez’gcnew’à la place|
|[Erreur du compilateur C2751](compiler-error-c2751.md)|'*paramètre*' : le nom d’un paramètre de fonction ne peut pas être qualifié|
|[Erreur du compilateur C2752](compiler-error-c2752.md)|'*template*' : plusieurs spécialisations partielles correspondent à la liste d’arguments template|
|[Erreur du compilateur C2753](compiler-error-c2753.md)|'*template*' : une spécialisation partielle ne peut pas correspondre à la liste d’arguments pour le modèle principal|
|[Erreur du compilateur C2754](compiler-error-c2754.md)|'*template*' : une spécialisation partielle ne peut pas avoir un paramètre de modèle sans type dépendant|
|[Erreur du compilateur C2755](compiler-error-c2755.md)|'*paramètre*' : un paramètre sans type d’une spécialisation partielle doit être un identificateur simple|
|[Erreur du compilateur C2756](compiler-error-c2756.md)|'*template*' : les arguments template par défaut ne sont pas autorisés sur une spécialisation partielle|
|[Erreur du compilateur C2757](compiler-error-c2757.md)|'*identificateur*' : un symbole portant ce nom existe déjà et, par conséquent, ce nom ne peut pas être utilisé comme nom d’espace de noms|
|[Erreur du compilateur C2758](compiler-error-c2758.md)|'*membre*' : un membre de type référence doit être initialisé|
|Erreur du compilateur C2759|rapports assembleur en ligne : *ERROR_MESSAGE*|
|[Erreur du compilateur C2760](compiler-error-c2760.md)|erreur de syntaxe : '*TOKEN1*'attendu non'*Token2*'|
|[Erreur du compilateur C2761](compiler-error-c2761.md)|'*fonction*' : la redéclaration de la fonction membre n’est pas autorisée|
|[Erreur du compilateur C2762](compiler-error-c2762.md)|'*template*' : expression non valide comme argument template pour'*Parameter*'|
|Erreur du compilateur C2763|'*template*' : utilisation non valide d’un littéral de chaîne comme argument template pour'*Parameter*'|
|[Erreur du compilateur C2764](compiler-error-c2764.md)|'*paramètre*' : paramètre de modèle non utilisé ou pouvant être déduit dans la spécialisation partielle'*spécialisation*'|
|[Erreur du compilateur C2765](compiler-error-c2765.md)|'*fonction*' : une spécialisation explicite d’un modèle de fonction ne peut pas avoir d’arguments par défaut|
|[Erreur du compilateur C2766](compiler-error-c2766.md)|spécialisation explicite ; '*spécialisation*'a déjà été défini|
|[Erreur du compilateur C2767](compiler-error-c2767.md)|incompatibilité de dimension de tableau managé/WinRT : argument (s) de *nombre* attendu (s)- *nombre* fourni|
|[Erreur du compilateur C2768](compiler-error-c2768.md)|'*fonction*' : utilisation non conforme d’arguments template explicites|
|Erreur du compilateur C2769|vous ne pouvez pas initialiser l’initialisation d’un tableau managé/WinRT dans une liste d’initialiseurs de base/membre|
|[Erreur du compilateur C2770](compiler-error-c2770.md)|argument (s) template/générique explicite (s) non valide (s) pour'*template*'|
|[Erreur du compilateur C2771](compiler-error-c2771.md)|#import seulement autorisé au niveau global ou de la portée espace de noms|
|Erreur du compilateur C2772|Obsolète.|
|[Erreur du compilateur C2773](compiler-error-c2773.md)|#import et #using disponibles uniquement dans le compilateur C++|
|[Erreur du compilateur C2774](compiler-error-c2774.md)|'*identificateur*' : aucune méthode’put’associée à cette propriété|
|[Erreur du compilateur C2775](compiler-error-c2775.md)|'*identificateur*' : aucune méthode’obtient’n’est associée à cette propriété|
|[Erreur du compilateur C2776](compiler-error-c2776.md)|une seule méthode' « obtient » peut être spécifiée par propriété|
|[Erreur du compilateur C2777](compiler-error-c2777.md)|une seule méthode’put’peut être spécifiée par propriété|
|[Erreur du compilateur C2778](compiler-error-c2778.md)|GUID incorrectement formé dans __declspec (UUID ())|
|[Erreur du compilateur C2779](compiler-error-c2779.md)|'*déclaration*' : les méthodes de propriété ne peuvent être associées qu’à des données membres non statiques|
|[Erreur du compilateur C2780](compiler-error-c2780.md)|'*déclaration*' *: nombre d’arguments attendu* - *nombre* fourni|
|[Erreur du compilateur C2781](compiler-error-c2781.md)|'*DECLARATION*' : attend au *moins le nombre d'* *arguments spécifié*|
|[Erreur du compilateur C2782](compiler-error-c2782.md)|'*déclaration*' : le paramètre de modèle/générique'*paramètre*'est ambigu|
|[Erreur du compilateur C2783](compiler-error-c2783.md)|'*déclaration*' : impossible de déduire l’argument template/générique pour'*identifier*'|
|[Erreur du compilateur C2784](compiler-error-c2784.md)|'*déclaration*' : impossible de déduire un argument template/générique pour'*type1*'à partir de'*type2*'|
|[Erreur du compilateur C2785](compiler-error-c2785.md)|'*déclaration1*'et'*déclaration2*'ont des types de retour différents|
|[Erreur du compilateur C2786](compiler-error-c2786.md)|'*type*' : opérande non valide pour __uuidof|
|[Erreur du compilateur C2787](compiler-error-c2787.md)|'*identificateur*' : aucun GUID associé à cet objet|
|[Erreur du compilateur C2788](compiler-error-c2788.md)|'*identificateur*' : plus d’un GUID associé à cet objet|
|Erreur du compilateur C2789|'*identificateur*' : un objet de type qualifié const doit être initialisé|
|[Erreur du compilateur C2790](compiler-error-c2790.md)|'Super' : ce mot clé ne peut être utilisé que dans le corps d’une fonction membre de classe|
|[Erreur du compilateur C2791](compiler-error-c2791.md)|utilisation non conforme de’Super' : '*classe*'n’a aucune classe de base|
|[Erreur du compilateur C2792](compiler-error-c2792.md)|'Super' : ce mot clé doit être suivi de' :: '|
|[Erreur du compilateur C2793](compiler-error-c2793.md)|'*Token*' : jeton inattendu après' :: ', identificateur ou mot clé’operator’attendu|
|[Erreur du compilateur C2794](compiler-error-c2794.md)|'*identificateur*' : n’est membre d’aucune classe de base directe ou indirecte de'*classe*'|
|[Erreur du compilateur C2795](compiler-error-c2795.md)|'Super ::*identifier*'n’est pas une fonction membre|
|Erreur du compilateur C2796|'Ref New’peut uniquement être utilisé pour créer une instance d’un type WinRT|
|[Erreur du compilateur C2797](compiler-error-c2797.md)|Périmé '*identificateur*' : l’initialisation de liste dans une liste d’initialiseurs de membre ou un initialiseur de membre de données non statique n’est pas implémenté|
|[Erreur du compilateur C2798](compiler-error-c2798.md)|'Super ::*identifier*'est ambigu|
|Erreur du compilateur C2799|'*identificateur*' : un objet de type de classe qualifié const sans constructeur par défaut fourni par l’utilisateur doit être initialisé|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
