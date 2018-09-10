---
title: Erreurs du compilateur C3000 à C3099 | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
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
dev_langs:
- C++
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7565a2656bcb5c9ad10c83179b563423d42be7b5
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44319043"
---
# <a name="compiler-errors-c3000-through-c3099"></a>Erreurs du compilateur C3000 à C3099

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur qui sont générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|C3000 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C3001](compiler-error-c3001.md)|«*message*' : nom de directive OpenMP attendu|
|[Erreur du compilateur C3002](compiler-error-c3002.md)|«*name1* *name2*' : plusieurs noms de directive OpenMP|
|[Erreur du compilateur C3003](compiler-error-c3003.md)|«*directive*' : nom de directive OpenMP non autorisé après des clauses de directive|
|[Erreur du compilateur C3004](compiler-error-c3004.md)|«*clause*' : clause non valide sur OpenMP '*directive*» (directive)|
|[Erreur du compilateur C3005](compiler-error-c3005.md)|«*message*' : jeton inattendu rencontré dans OpenMP '*directive*» (directive)|
|[Erreur du compilateur C3006](compiler-error-c3006.md)|«*clause*' : clause sur OpenMP '*directive*' un argument attendu est manquant dans la directive|
|[Erreur du compilateur C3007](compiler-error-c3007.md)|«*clause*' : clause sur OpenMP '*directive*' ne prend un argument|
|[Erreur du compilateur C3008](compiler-error-c3008.md)|*argument*' : argument fermant manquant ')' sur OpenMP '*directive*' directive|
|[Erreur du compilateur C3009](compiler-error-c3009.md)|«*étiquette*' : saut dans le bloc structuré OpenMP non autorisé|
|[Erreur du compilateur C3010](compiler-error-c3010.md)|«*étiquette*' : saut hors du bloc structuré OpenMP non autorisé|
|[Erreur du compilateur C3011](compiler-error-c3011.md)|assembly inline non autorisé directement dans une région parallèle|
|[Erreur du compilateur C3012](compiler-error-c3012.md)|«*fonction*' : fonction intrinsèque non autorisée directement dans une région parallèle|
|[Erreur du compilateur C3013](compiler-error-c3013.md)|'*clause*' : clause peut uniquement apparaître une fois sur OpenMP '*directive*» (directive)|
|[Erreur du compilateur C3014](compiler-error-c3014.md)|attendu une boucle suivant OpenMP '*directive*» (directive)|
|[Erreur du compilateur C3015](compiler-error-c3015.md)|forme incorrecte de l'initialisation dans l'instruction 'for' OpenMP|
|[Erreur du compilateur C3016](compiler-error-c3016.md)|«*identificateur*' : variable d’index 'instruction for' OpenMP doit disposer d’un type intégral signé|
|[Erreur du compilateur C3017](compiler-error-c3017.md)|forme incorrecte du test de fin dans l'instruction 'for' OpenMP|
|[Erreur du compilateur C3018](compiler-error-c3018.md)|«*identificateur*' : OpenMP 'for' test ou l’incrément doive utiliser la variable d’index '*variable*»|
|[Erreur du compilateur C3019](compiler-error-c3019.md)|incrément 'd’instruction for' OpenMP a forme incorrecte|
|[Erreur du compilateur C3020](compiler-error-c3020.md)|«*variable*' : variable d’index OpenMP 'boucle for' ne peut pas être modifié dans le corps de la boucle|
|[Erreur du compilateur C3021](compiler-error-c3021.md)|«*argument*' : argument est vide sur OpenMP '*directive*» (directive)|
|[Erreur du compilateur C3022](compiler-error-c3022.md)|'*directive*' : type de planification non valide de '*directive*'on OpenMP'*directive*» (directive)|
|[Erreur du compilateur C3023](compiler-error-c3023.md)|«*argument*' : jeton inattendu rencontré dans l’argument avec OpenMP '*directive*« clause|
|[Erreur du compilateur C3024](compiler-error-c3024.md)|'Schedule (Runtime)' : l’expression chunk_size n’est pas autorisée.|
|[Erreur du compilateur C3025](compiler-error-c3025.md)|«*clause*' : expression intégrale attendue|
|[Erreur du compilateur C3026](compiler-error-c3026.md)|«*clause*' : expression constante doit être positive|
|[Erreur du compilateur C3027](compiler-error-c3027.md)|«*clause*' : expression arithmétique ou pointeur attendue|
|[Erreur du compilateur C3028](compiler-error-c3028.md)|«*membre*' : seul un membre de données de variable ou static peut être utilisé dans une clause de partage de données|
|[Erreur du compilateur C3029](compiler-error-c3029.md)|«*symbole*' : ne peut apparaître qu’une seule fois dans le partage de données clauses dans une directive OpenMP|
|[Erreur du compilateur C3030](compiler-error-c3030.md)|«*identificateur*' : variable '*directive*' clause/directive ne peut pas avoir un type référence|
|[Erreur du compilateur C3031](compiler-error-c3031.md)|«*identificateur*' : variable de clause 'reduction' doit avoir un type arithmétique scalaire|
|[Erreur du compilateur C3032](compiler-error-c3032.md)|«*identificateur*' : variable '*clause*'clause ne peut pas avoir de type incomplet'*type*»|
|[Erreur du compilateur C3033](compiler-error-c3033.md)|«*identificateur*' : variable '*clause*« clause ne peut pas avoir un type qualifié const|
|[Erreur du compilateur C3034](compiler-error-c3034.md)|OpenMP '*directive*'directive ne peut pas être directement imbriquée dans'*directive*» (directive)|
|[Erreur du compilateur C3035](compiler-error-c3035.md)|La directive 'ordered' OpenMP doit être liée directement à une directive 'for' ou 'parallel for' avec la clause 'ordered'|
|[Erreur du compilateur C3036](compiler-error-c3036.md)|«*clause*' : jeton d’opérateur non valide dans la clause 'Reduction' OpenMP|
|[Erreur du compilateur C3037](compiler-error-c3037.md)|«*identificateur*' : variable '*clause*« clause doit être partagée dans un contexte englobant|
|[Erreur du compilateur C3038](compiler-error-c3038.md)|«*identificateur*' : variable de la clause 'private' ne peut pas être une variable de réduction dans un contexte englobant|
|[Erreur du compilateur C3039](compiler-error-c3039.md)|«*identificateur*' : variable d’index 'instruction for' OpenMP ne peut pas être une variable de réduction|
|[Erreur du compilateur C3040](compiler-error-c3040.md)|«*identificateur*' : type de variable dans la clause 'reduction' est incompatible avec l’opérateur de réduction '*opérateur*»|
|[Erreur du compilateur C3041](compiler-error-c3041.md)|«*identificateur*' : variable de la clause 'copyprivate' doit être privée dans un contexte englobant|
|[Erreur du compilateur C3042](compiler-error-c3042.md)|les clauses 'copyprivate' et 'nowait' ne peut pas apparaître ensemble sur OpenMP '*directive*» (directive)|
|[Erreur du compilateur C3043](compiler-error-c3043.md)|la directive 'critical' OpenMP ne peut pas être imbriquée dans une directive 'critical' du même nom|
|[Erreur du compilateur C3044](compiler-error-c3044.md)|'section' : uniquement autorisé une imbrication directe sous une directive 'sections' OpenMP|
|[Erreur du compilateur C3045](compiler-error-c3045.md)|Instruction composée attendue à la suite de la directive 'sections' OpenMP. Accolade '{' manquante|
|[Erreur du compilateur C3046](compiler-error-c3046.md)|Bloc structuré manquant dans une région '#pragma omp sections' OpenMP|
|[Erreur du compilateur C3047](compiler-error-c3047.md)|Le bloc structuré d'une région 'sections' OpenMP doit être précédé de '#pragma omp section'|
|[Erreur du compilateur C3048](compiler-error-c3048.md)|Forme incorrecte de l'expression placée à la suite de '#pragma omp atomic'|
|[Erreur du compilateur C3049](compiler-error-c3049.md)|«*argument*' : argument non valide dans la clause 'default' OpenMP|
|[Erreur du compilateur C3050](compiler-error-c3050.md)|«*classe*' : une classe ref ne peut pas hériter de '*identificateur*»|
|C3051 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C3052](compiler-error-c3052.md)|«*identificateur*' : variable n’apparaît pas dans une clause de partage de données sous une clause default (None)|
|[Erreur du compilateur C3053](compiler-error-c3053.md)|«*identificateur*' : 'threadprivate' n’est valide pour les éléments de données global ou static|
|[Erreur du compilateur C3054](compiler-error-c3054.md)|'#pragma omp parallel' n'est pas pris en charge actuellement dans une classe ou fonction générique|
|[Erreur du compilateur C3055](compiler-error-c3055.md)|«*identificateur*' : Impossible de référencer le symbole avant qu’il soit utilisé dans la directive 'threadprivate'|
|[Erreur du compilateur C3056](compiler-error-c3056.md)|«*identificateur*' : symbole n’est pas dans la même portée avec la directive 'threadprivate'|
|[Erreur du compilateur C3057](compiler-error-c3057.md)|«*identificateur*' : l’initialisation dynamique des symboles 'threadprivate' n’est pas pris en charge|
|[Erreur du compilateur C3058](compiler-error-c3058.md)|«*identificateur*' : symbole non déclaré comme 'threadprivate' avant d’être utilisée dans la clause 'copyin'|
|[Erreur du compilateur C3059](compiler-error-c3059.md)|«*identificateur*' : symbole 'threadprivate' ne peut pas être utilisé dans le '*clause*« clause|
|[Erreur du compilateur C3060](compiler-error-c3060.md)|«*identificateur*' : une fonction friend ne peut pas être définie à l’intérieur d’une classe à l’aide d’un nom qualifié (elle peut uniquement être déclarée)|
|C3061 d’erreur du compilateur|opérateur '*opérateur*' : non autorisé sur une énumération '*type*« avec le type sous-jacent'*type*'|
|[Erreur du compilateur C3062](compiler-error-c3062.md)|«*identificateur*' : énumérateur requiert une valeur dans la mesure où le type sous-jacent est '*type*»|
|[Erreur du compilateur C3063](compiler-error-c3063.md)|opérateur '*opérateur*' : tous les opérandes doivent avoir le même type d’énumération|
|C3064 d’erreur du compilateur|«*identificateur*' : doit être un type simple ou correspondre à ce dernier|
|[Erreur du compilateur C3065](compiler-error-c3065.md)|la déclaration de propriété au niveau d'une portée sans classe n'est pas autorisée|
|[Erreur du compilateur C3066](compiler-error-c3066.md)|Il existe plusieurs façons qu’un objet de ce type peut être appelé avec ces arguments|
|C3067 d’erreur du compilateur|une liste d’initialiseurs ne peut pas être utilisée avec l’opérateur intégrés]|
|[Erreur du compilateur C3068](compiler-error-c3068.md)|«*identificateur*' : une fonction 'naked' ne peut pas contenir des objets qui requièrent un déroulement si une exception C++ s’est produite|
|[Erreur du compilateur C3069](compiler-error-c3069.md)|opérateur '*opérateur*' : non autorisé pour le type d’énumération|
|[Erreur du compilateur C3070](compiler-error-c3070.md)|«*identificateur*' : propriété n’a pas une méthode 'set'|
|[Erreur du compilateur C3071](compiler-error-c3071.md)|opérateur '*opérateur*' peut uniquement être appliqué à une instance d’une classe ref ou un type valeur|
|[Erreur du compilateur C3072](compiler-error-c3072.md)|opérateur '*opérateur*' ne peut pas être appliqué à une instance d’une classe de l’opérateur unaire '%' pour convertir une instance d’une référence à un type de handle, utilisez classe ref|
|[Erreur du compilateur C3073](compiler-error-c3073.md)|«*identificateur*' : classe ref n’a pas d’un constructeur de copie défini par l’utilisateur|
|C3074 d’erreur du compilateur|un tableau ne peut pas être initialisé avec un initialiseur entre parenthèses|
|[Erreur du compilateur C3075](compiler-error-c3075.md)|«*identificateur*' : vous ne pouvez pas incorporer une instance d’un type référence, '*type*», dans un type valeur|
|[Erreur du compilateur C3076](compiler-error-c3076.md)|«*identificateur*' : vous ne pouvez pas incorporer une instance d’un type référence, '*type*», dans un type natif|
|[Erreur du compilateur C3077](compiler-error-c3077.md)|«*identificateur*' : un finaliseur ne peut être un membre d’un type référence|
|C3078 d’erreur du compilateur|taille du tableau doit être spécifiée dans les nouvelles expressions|
|C3079 d’erreur du compilateur|une liste d’initialiseurs ne peut pas être utilisée comme opérande de droite de cet opérateur d’assignation|
|[Erreur du compilateur C3080](compiler-error-c3080.md)|«*finaliseur*' : un finaliseur ne peut pas avoir de spécificateur de classe de stockage|
|C3081 d’erreur du compilateur|Obsolète.|
|Erreur du compilateur C3082|Obsolète.|
|[Erreur du compilateur C3083](compiler-error-c3083.md)|«*identificateur*' : le symbole à gauche d’un ' ::' doit être un type|
|[Erreur du compilateur C3084](compiler-error-c3084.md)|«*identificateur*' : un destructeur/finaliseur ne peut pas être '*mot clé*»|
|[Erreur du compilateur C3085](compiler-error-c3085.md)|«*identificateur*' : un constructeur ne peut pas être '*mot clé*»|
|C3086 d’erreur du compilateur|Impossible de trouver 'std::initializer_list' : vous devez #include \<initializer_list >|
|[Erreur du compilateur C3087](compiler-error-c3087.md)|«*identificateur*' : appel de '*déclaration*' Initialise déjà ce membre|
|C3088 d’erreur du compilateur|«*classe*' : le constructeur d’attribut doit avoir des arguments formels nommés|
|C3089 d’erreur du compilateur|«*identificateur*' : nom du paramètre ne correspond pas de nom de n’importe quel membre données|
|C3090 d’erreur du compilateur|«*classe*' : classe d’attributs ne peut pas être un modèle|
|C3091 d’erreur du compilateur|«*classe*' : classe d’attributs ne peut pas avoir de classes de base|
|C3092 d’erreur du compilateur|«*classe*' : membre de classe d’attribut ne peut pas être un peu champ, 'static' ou 'const'|
|C3093 d’erreur du compilateur|«*type*' : type non autorisé pour le membre de classe d’attribut '*membre*»|
|[Erreur du compilateur C3094](compiler-error-c3094.md)|«*attribut*' : utilisation anonyme non autorisée|
|[Erreur du compilateur C3095](compiler-error-c3095.md)|«*attribut*' : attribut ne peut pas être répété.|
|[Erreur du compilateur C3096](compiler-error-c3096.md)|«*attribut*' : attribut est autorisé sur les données membres des classes d’attributs uniquement|
|[Erreur du compilateur C3097](compiler-error-c3097.md)|'*attribut*' : attribut portée doit être définie avec ' assembly :' ou ' module :'|
|C3098 d’erreur du compilateur|«*identificateur*' : attribut n’a aucun constructeur défini par l’utilisateur|
|[Erreur du compilateur C3099](compiler-error-c3099.md)|«*mot clé*' : utilisez [System::AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] pour les attributs de gérés/WinRT|
