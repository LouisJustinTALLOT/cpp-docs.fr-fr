---
description: 'En savoir plus sur : Erreurs du compilateur C3000 à C3099'
title: Erreurs du compilateur C3000 à C3099
ms.date: 04/21/2019
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
ms.openlocfilehash: ce4e088a1d69da20cae87fd9b824ddef4769c8da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238698"
---
# <a name="compiler-errors-c3000-through-c3099"></a>Erreurs du compilateur C3000 à C3099

Les Articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|Erreur du compilateur C3000|Obsolète.|
|[Erreur du compilateur C3001](compiler-error-c3001.md)|'*message*' : nom de directive OpenMP ATTENDU|
|[Erreur du compilateur C3002](compiler-error-c3002.md)|'*name1* *name2*' : plusieurs noms de directive OpenMP|
|[Erreur du compilateur C3003](compiler-error-c3003.md)|'*directive*' : nom de directive OpenMP non autorisé après des clauses de directive|
|[Erreur du compilateur C3004](compiler-error-c3004.md)|'*clause*' : clause non valide dans la directive'*directive*'OpenMP|
|[Erreur du compilateur C3005](compiler-error-c3005.md)|'*message*' : jeton inattendu rencontré dans la directive'*directive*'OpenMP|
|[Erreur du compilateur C3006](compiler-error-c3006.md)|'*clause*' : un argument attendu est manquant dans la clause de la directive'*directive*'OpenMP|
|[Erreur du compilateur C3007](compiler-error-c3007.md)|'*clause*' : la clause sur la directive'*directive*'OpenMP ne prend pas d’argument|
|[Erreur du compilateur C3008](compiler-error-c3008.md)|'*argument*' : une parenthèse fermante') 'est manquante dans l’argument de la directive'*directive*'OpenMP|
|[Erreur du compilateur C3009](compiler-error-c3009.md)|'*étiquette*' : saut dans le bloc structuré OpenMP non autorisé|
|[Erreur du compilateur C3010](compiler-error-c3010.md)|'*étiquette*' : saut hors du bloc structuré OpenMP non autorisé|
|[Erreur du compilateur C3011](compiler-error-c3011.md)|assembly inline non autorisé directement dans une région parallèle|
|[Erreur du compilateur C3012](compiler-error-c3012.md)|'*fonction*' : fonction intrinsèque non autorisée directement dans une région parallèle|
|[Erreur du compilateur C3013](compiler-error-c3013.md)|'*clause*' : la clause ne peut apparaître qu’une seule fois dans la directive'*directive*'OpenMP|
|[Erreur du compilateur C3014](compiler-error-c3014.md)|boucle for attendue à la suite de la directive'*directive*'OpenMP|
|[Erreur du compilateur C3015](compiler-error-c3015.md)|forme incorrecte de l'initialisation dans l'instruction 'for' OpenMP|
|[Erreur du compilateur C3016](compiler-error-c3016.md)|'*identificateur*' : la variable d’index de l’instruction’for’OpenMP doit avoir un type intégral signé|
|[Erreur du compilateur C3017](compiler-error-c3017.md)|forme incorrecte du test de fin dans l'instruction 'for' OpenMP|
|[Erreur du compilateur C3018](compiler-error-c3018.md)|'*identificateur*' : le test ou l’incrément de l’OpenMP doit utiliser la variable d’index'*variable*'|
|[Erreur du compilateur C3019](compiler-error-c3019.md)|forme incorrecte de l’incrément dans l’instruction’for’OpenMP|
|[Erreur du compilateur C3020](compiler-error-c3020.md)|'*variable*' : la variable d’index de la boucle’for’OpenMP ne peut pas être modifiée dans le corps de la boucle|
|[Erreur du compilateur C3021](compiler-error-c3021.md)|'*argument*' : argument vide dans la directive'*directive*'OpenMP|
|[Erreur du compilateur C3022](compiler-error-c3022.md)|'*directive*' : type de planification'*directive*'non valide dans la directive'*directive*'OpenMP|
|[Erreur du compilateur C3023](compiler-error-c3023.md)|'*argument*' : jeton inattendu rencontré dans l’argument de la clause'*directive*'OpenMP|
|[Erreur du compilateur C3024](compiler-error-c3024.md)|'Schedule (Runtime) ' : l’expression chunk_size n’est pas autorisée|
|[Erreur du compilateur C3025](compiler-error-c3025.md)|'*clause*' : expression intégrale attendue|
|[Erreur du compilateur C3026](compiler-error-c3026.md)|'*clause*' : l’expression constante doit être positive|
|[Erreur du compilateur C3027](compiler-error-c3027.md)|'*clause*' : expression arithmétique ou expression de pointeur attendue|
|[Erreur du compilateur C3028](compiler-error-c3028.md)|'*membre*' : seule une variable ou un membre de données statique peut être utilisé dans une clause de partage de données|
|[Erreur du compilateur C3029](compiler-error-c3029.md)|'*symbol*' : ne peut apparaître qu’une seule fois dans les clauses de partage de données d’une directive OpenMP|
|[Erreur du compilateur C3030](compiler-error-c3030.md)|'*identificateur*' : la variable de la clause/directive'*directive*'ne peut pas avoir un type référence|
|[Erreur du compilateur C3031](compiler-error-c3031.md)|'*identificateur*' : la variable de la clause’Reduction’doit avoir un type arithmétique scalaire|
|[Erreur du compilateur C3032](compiler-error-c3032.md)|'*identifier*' : la variable de la clause'*clause*'ne peut pas avoir un type'*type*'incomplet|
|[Erreur du compilateur C3033](compiler-error-c3033.md)|'*identifier*' : la variable de la clause'*clause*'ne peut pas avoir un type qualifié const|
|[Erreur du compilateur C3034](compiler-error-c3034.md)|La directive'*directive*'OpenMP ne peut pas être directement imbriquée dans la directive'*directive*'|
|[Erreur du compilateur C3035](compiler-error-c3035.md)|La directive 'ordered' OpenMP doit être liée directement à une directive 'for' ou 'parallel for' avec la clause 'ordered'|
|[Erreur du compilateur C3036](compiler-error-c3036.md)|'*clause*' : jeton d’opérateur non valide dans la clause’Reduction’OpenMP|
|[Erreur du compilateur C3037](compiler-error-c3037.md)|'*identifier*' : la variable de la clause'*clause*'doit être partagée dans un contexte englobant|
|[Erreur du compilateur C3038](compiler-error-c3038.md)|'*identificateur*' : la variable de la clause’Private’ne peut pas être une variable de réduction dans un contexte englobant|
|[Erreur du compilateur C3039](compiler-error-c3039.md)|'*identificateur*' : la variable d’index dans l’instruction’for’OpenMP ne peut pas être une variable de réduction|
|[Erreur du compilateur C3040](compiler-error-c3040.md)|'*identifier*' : le type de la variable dans la clause’Reduction’est incompatible avec l’opérateur de réduction'*Operator*'|
|[Erreur du compilateur C3041](compiler-error-c3041.md)|'*identificateur*' : la variable de la clause’copyprivate’doit être privée dans un contexte englobant|
|[Erreur du compilateur C3042](compiler-error-c3042.md)|les clauses’copyprivate’et’NOWAIT’ne peuvent pas apparaître en même temps dans la directive'*directive*'OpenMP|
|[Erreur du compilateur C3043](compiler-error-c3043.md)|la directive 'critical' OpenMP ne peut pas être imbriquée dans une directive 'critical' du même nom|
|[Erreur du compilateur C3044](compiler-error-c3044.md)|'section' : uniquement autorisé directement imbriqué dans une directive’sections’OpenMP|
|[Erreur du compilateur C3045](compiler-error-c3045.md)|Instruction composée attendue à la suite de la directive 'sections' OpenMP. Accolade '{' manquante|
|[Erreur du compilateur C3046](compiler-error-c3046.md)|Bloc structuré manquant dans une région '#pragma omp sections' OpenMP|
|[Erreur du compilateur C3047](compiler-error-c3047.md)|Le bloc structuré d'une région 'sections' OpenMP doit être précédé de '#pragma omp section'|
|[Erreur du compilateur C3048](compiler-error-c3048.md)|Forme incorrecte de l'expression placée à la suite de '#pragma omp atomic'|
|[Erreur du compilateur C3049](compiler-error-c3049.md)|'*argument*' : argument non valide dans la clause’default’OpenMP|
|[Erreur du compilateur C3050](compiler-error-c3050.md)|'*classe*' : une classe ref ne peut pas hériter de'*identifier*'|
|Erreur du compilateur C3051|Obsolète.|
|[Erreur du compilateur C3052](compiler-error-c3052.md)|'*identificateur*' : la variable n’apparaît pas dans une clause de partage de données sous une clause default (None)|
|[Erreur du compilateur C3053](compiler-error-c3053.md)|'*identifier*' : 'threadprivate’n’est valide que pour les éléments de données globaux ou statiques|
|[Erreur du compilateur C3054](compiler-error-c3054.md)|'#pragma omp parallel' n'est pas pris en charge actuellement dans une classe ou fonction générique|
|[Erreur du compilateur C3055](compiler-error-c3055.md)|'*identificateur*' : impossible de référencer le symbole avant qu’il ne soit utilisé dans la directive’threadprivate'|
|[Erreur du compilateur C3056](compiler-error-c3056.md)|'*identificateur*' : le symbole n’est pas dans la même portée avec la directive’threadprivate'|
|[Erreur du compilateur C3057](compiler-error-c3057.md)|'*identificateur*' : l’initialisation dynamique des symboles’threadprivate’n’est pas prise en charge actuellement|
|[Erreur du compilateur C3058](compiler-error-c3058.md)|'*identificateur*' : symbole non déclaré comme’threadprivate’avant qu’il ne soit utilisé dans la clause’copyy'|
|[Erreur du compilateur C3059](compiler-error-c3059.md)|'*identifier*' : le symbole’threadprivate’ne peut pas être utilisé dans la clause'*clause*'|
|[Erreur du compilateur C3060](compiler-error-c3060.md)|'*identificateur*' : une fonction friend ne peut pas être définie à l’intérieur d’une classe à l’aide d’un nom qualifié (elle peut uniquement être déclarée)|
|Erreur du compilateur C3061|opérateur'*Operator*' : non autorisé sur l’énumération'*type*'avec le type sous-jacent'*type*'|
|[Erreur du compilateur C3062](compiler-error-c3062.md)|'*identificateur*' : l’énumérateur requiert une valeur, car le type sous-jacent est'*type*'|
|[Erreur du compilateur C3063](compiler-error-c3063.md)|opérateur'*opérateur*' : tous les opérandes doivent avoir le même type d’énumération|
|Erreur du compilateur C3064|'*identificateur*' : doit être un type simple ou correspondre à un|
|[Erreur du compilateur C3065](compiler-error-c3065.md)|la déclaration de propriété au niveau d'une portée sans classe n'est pas autorisée|
|[Erreur du compilateur C3066](compiler-error-c3066.md)|Il existe plusieurs façons d’appeler un objet de ce type avec ces arguments|
|Erreur du compilateur C3067|une liste d’initialiseurs ne peut pas être utilisée avec l’opérateur intégré []|
|[Erreur du compilateur C3068](compiler-error-c3068.md)|'*identificateur*' : une fonction’Naked’ne peut pas contenir d’objets qui requièrent un déroulement si une exception C++ s’est produite|
|[Erreur du compilateur C3069](compiler-error-c3069.md)|opérateur'*opérateur*' : non autorisé pour un type énumération|
|[Erreur du compilateur C3070](compiler-error-c3070.md)|'*identificateur*' : la propriété n’a pas de méthode’Set'|
|[Erreur du compilateur C3071](compiler-error-c3071.md)|l’opérateur'*opérateur*'ne peut être appliqué qu’à une instance d’une classe ref ou d’un type valeur|
|[Erreur du compilateur C3072](compiler-error-c3072.md)|l’opérateur'*Operator*'ne peut pas être appliqué à une instance d’une classe ref utilisez l’opérateur'% 'unaire pour convertir une instance d’une classe ref en type handle|
|[Erreur du compilateur C3073](compiler-error-c3073.md)|'*identifier*' : la classe ref n’a pas de constructeur de copie défini par l’utilisateur|
|Erreur du compilateur C3074|un tableau ne peut pas être initialisé avec un initialiseur entre parenthèses|
|[Erreur du compilateur C3075](compiler-error-c3075.md)|'*identificateur*' : vous ne pouvez pas incorporer une instance d’un type référence, '*type*', dans un type valeur|
|[Erreur du compilateur C3076](compiler-error-c3076.md)|'*identificateur*' : vous ne pouvez pas incorporer une instance d’un type référence, '*type*', dans un type natif|
|[Erreur du compilateur C3077](compiler-error-c3077.md)|'*identificateur*' : un finaliseur ne peut être qu’un membre d’un type référence|
|Erreur du compilateur C3078|la taille du tableau doit être spécifiée dans les nouvelles expressions|
|Erreur du compilateur C3079|une liste d’initialiseurs ne peut pas être utilisée comme opérande droit de cet opérateur d’assignation|
|[Erreur du compilateur C3080](compiler-error-c3080.md)|'*Finalizer*' : un finaliseur ne peut pas avoir de spécificateur de classe de stockage|
|Erreur du compilateur C3081|Obsolète.|
|Erreur du compilateur C3082|Obsolète.|
|[Erreur du compilateur C3083](compiler-error-c3083.md)|'*identificateur*' : le symbole situé à gauche de' :: 'doit être un type|
|[Erreur du compilateur C3084](compiler-error-c3084.md)|'*identificateur*' : un destructeur/finaliseur ne peut pas être'*Keyword*'|
|[Erreur du compilateur C3085](compiler-error-c3085.md)|'*identificateur*' : un constructeur ne peut pas être'*Keyword*'|
|Erreur du compilateur C3086|Impossible de trouver’std :: initializer_list' : vous devez #include \<initializer_list>|
|[Erreur du compilateur C3087](compiler-error-c3087.md)|'*identifier*' : l’appel de'*DECLARATION*'Initialise déjà ce membre|
|Erreur du compilateur C3088|'*classe*' : le constructeur d’attribut doit avoir des arguments formels nommés|
|Erreur du compilateur C3089|'*identificateur*' : le nom du paramètre ne correspond à aucun nom de membre de données|
|Erreur du compilateur C3090|'*classe*' : la classe d’attributs ne peut pas être un modèle|
|Erreur du compilateur C3091|'*classe*' : la classe d’attributs ne peut pas avoir de classes de base|
|Erreur du compilateur C3092|'*classe*' : un membre de classe d’attributs ne peut pas être un champ de bits, 'static’ou’const'|
|Erreur du compilateur C3093|'*type*' : type non autorisé pour le membre de classe d’attributs'*member*'|
|[Erreur du compilateur C3094](compiler-error-c3094.md)|'*attribute*' : utilisation anonyme non autorisée|
|[Erreur du compilateur C3095](compiler-error-c3095.md)|'*attribute*' : impossible de répéter l’attribut|
|[Erreur du compilateur C3096](compiler-error-c3096.md)|'*attribute*' : l’attribut est autorisé sur les données membres des classes d’attributs uniquement|
|[Erreur du compilateur C3097](compiler-error-c3097.md)|'*attribute*' : l’attribut doit être étendu avec’assembly : 'ou’module : '|
|Erreur du compilateur C3098|'*identifier*' : l’attribut n’a pas de constructeurs définis par l’utilisateur|
|[Erreur du compilateur C3099](compiler-error-c3099.md)|'*Keyword*' : utilisez [System :: AttributeUsageAttribute]/[Windows :: Foundation :: Metadata :: AttributeUsageAttribute] pour les attributs managés/WinRT|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
