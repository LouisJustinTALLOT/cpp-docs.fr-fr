---
title: Erreurs du compilateur C2900 à C2999
ms.date: 11/17/2017
f1_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
helpviewer_keywords:
- C2900
- C2901
- C2905
- C2907
- C2915
- C2916
- C2922
- C2924
- C2925
- C2926
- C2938
- C2949
- C2950
- C2954
- C2956
- C2960
- C2961
- C2963
- C2964
- C2965
- C2966
- C2967
- C2968
- C2972
- C2980
- C2981
- C2982
- C2983
- C2984
- C2985
- C2986
- C2987
- C2997
- C2999
ms.assetid: e3440738-e11b-4878-9ae3-6bc6c53ba461
ms.openlocfilehash: 4d430d1d446147c662f7f6405185aee75d95bc0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466895"
---
# <a name="compiler-errors-c2900-through-c2999"></a>Erreurs du compilateur C2900 à C2999

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur qui sont générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|C2900 d’erreur du compilateur|«*déclarateur*' : les modèles de fonction membre dans les classes WinRT doivent être 'private', 'internal' ou 'protected private'|
|C2901 d’erreur du compilateur|«*identificateur*' : une interface générique ou un délégué ne peut pas être public|
|[Erreur du compilateur C2902](compiler-error-c2902.md)|«*jeton*' : inattendu jeton suivant 'modèle/générique', identificateur attendu|
|[Erreur du compilateur C2903](compiler-error-c2903.md)|«*identificateur*' : symbole n’est ni un modèle/générique de classe ni un fonction modèle/générique|
|[Erreur du compilateur C2904](compiler-error-c2904.md)|«*identificateur*' : nom déjà utilisé pour un modèle dans la portée actuelle|
|C2905 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C2906](compiler-error-c2906.md)|«*modèle*' : une spécialisation explicite requiert 'modèle <>'|
|C2907 d’erreur du compilateur|l’argument du Registre '*nombre*' ne spécifie pas le numéro du Registre valide|
|[Erreur du compilateur C2908](compiler-error-c2908.md)|spécialisation explicite ; «*modèle*' a déjà été instancié|
|[Erreur du compilateur C2909](compiler-error-c2909.md)|«*identificateur*' : instanciation explicite du modèle de fonction exige un type de retour|
|[Erreur du compilateur C2910](compiler-error-c2910.md)|«*fonction*' : ne peut pas être explicitement spécialisé|
|[Erreur du compilateur C2911](compiler-error-c2911.md)|«*membre*' : ne peut pas être déclaré ou défini dans la portée actuelle|
|[Erreur du compilateur C2912](compiler-error-c2912.md)|spécialisation explicite '*déclaration*' n’est pas une spécialisation d’un modèle de fonction|
|[Erreur du compilateur C2913](compiler-error-c2913.md)|spécialisation explicite ; «*déclaration*' n’est pas une spécialisation de modèle de classe|
|[Erreur du compilateur C2914](compiler-error-c2914.md)|«*identificateur*' : Impossible de déduire l’argument de modèle/générique comme argument de fonction est ambigu|
|C2915 d’erreur du compilateur|«*identificateur*' : '*type*' ne peut pas être utilisé directement sur la surface publiée d’un type WinRT. Utilisez ' Platform::Object ^' à la place pour passer ce type|
|C2916 d’erreur du compilateur|«*identificateur*' : [FlagsAttribute] doit être spécifié (uniquement) sur un enum public avec un 'unsigned int' type sous-jacent|
|[Erreur du compilateur C2917](compiler-error-c2917.md)|«*identificateur*' : paramètre de modèle non valide|
|[Erreur du compilateur C2918](compiler-error-c2918.md)|«*identificateur*' : les propriétés indexées ne peut pas être utilisées sur la surface publiée d’un type WinRT|
|[Erreur du compilateur C2919](compiler-error-c2919.md)|«*type*' : ne peut pas utiliser les opérateurs sur la surface publiée d’un type WinRT|
|[Erreur du compilateur C2920](compiler-error-c2920.md)|redéfinition : '*type*' : classe modèle/générique a déjà été déclaré comme*déclaration*'|
|[Erreur du compilateur C2921](compiler-error-c2921.md)|redéfinition : '*type*' : classe modèle/générique en cours de redéclaration comme*déclaration*'|
|C2922 d’erreur du compilateur|«*interface*' : WinRT d’une interface ne peut pas contenir de membres statiques|
|[Erreur du compilateur C2923](compiler-error-c2923.md)|«*type*' : '*identificateur*'n’est pas un argument de type modèle/générique valide pour le paramètre'*paramètre*»|
|C2924 d’erreur du compilateur|argument de routine __declspec (Interrupt) absent dans R2|
|C2925 d’erreur du compilateur|routine de __declspec (Interrupt) ne peut pas utiliser de virgule flottante|
|Erreur du compilateur C2926|«*identificateur*' : un initialiseur de membre par défaut n’est pas autorisé pour un membre d’un struct anonyme au sein d’une union|
|[Erreur du compilateur C2927](compiler-error-c2927.md)|«*identificateur*' : un modèle de fonction doit être appelé avec au moins un argument|
|[Erreur du compilateur C2928](compiler-error-c2928.md)|instanciation explicite ; «*identificateur*'n’est pas une fonction ou un membre de données statiques de classe de modèle'*classe*»|
|[Erreur du compilateur C2929](compiler-error-c2929.md)|«*déclarateur*' : instanciation explicite ; ne peut pas forcer ou de supprimer explicitement l’instanciation d’un membre de classe de modèle|
|[Erreur du compilateur C2930](compiler-error-c2930.md)|«*classe*' : modèle-id/générique-id redéfini comme énumérateur de ' enum *identificateur*»|
|[Erreur du compilateur C2931](compiler-error-c2931.md)|«*class1*' : modèle-id/générique-id redéfini comme fonction membre de '*classe2*»|
|[Erreur du compilateur C2932](compiler-error-c2932.md)|«*type*' : modèle-id/générique-id redéfini comme donnée membre de '*identificateur*»|
|[Erreur du compilateur C2933](compiler-error-c2933.md)|«*type*' : modèle-id/générique-id redéfini comme typedef de membre '*identificateur*»|
|[Erreur du compilateur C2934](compiler-error-c2934.md)|«*type*' : modèle-id/générique-id redéfini comme imbriquée '*élément*'of'*identificateur*»|
|[Erreur du compilateur C2935](compiler-error-c2935.md)|«*type*' : modèle-id/générique-id redéfini comme fonction globale|
|[Erreur du compilateur C2936](compiler-error-c2936.md)|«*type*' : modèle-id/générique-id redéfini comme variable globale de données|
|[Erreur du compilateur C2937](compiler-error-c2937.md)|«*type*' : modèle-id/générique-id redéfini comme typedef global|
|C2938 d’erreur du compilateur|«*identificateur*' : Impossible de spécialiser le modèle d’alias|
|[Erreur du compilateur C2939](compiler-error-c2939.md)|«*type*' : modèle-id/générique-id redéfini comme variable locale de données|
|[Erreur du compilateur C2940](compiler-error-c2940.md)|«*type*' : modèle-id/générique-id redéfini comme typedef local|
|[Erreur du compilateur C2941](compiler-error-c2941.md)|«*type*' : modèle-id/générique-id redéfini comme une variable locale '*élément*»|
|[Erreur du compilateur C2942](compiler-error-c2942.md)|«*type*' : modèle-id/générique-id redéfini comme argument formel d’une fonction|
|[Erreur du compilateur C2943](compiler-error-c2943.md)|«*type*' : modèle-id/générique-id redéfini comme argument de type d’un modèle|
|[Erreur du compilateur C2944](compiler-error-c2944.md)|«*type*' : modèle-id/générique-id redéfini comme argument de valeur d’un modèle|
|[Erreur du compilateur C2945](compiler-error-c2945.md)|l'instanciation explicite ne fait pas référence à une spécialisation de classe de modèle|
|[Erreur du compilateur C2946](compiler-error-c2946.md)|instanciation explicite ; «*type*' n’est pas une spécialisation de classe de modèle|
|[Erreur du compilateur C2947](compiler-error-c2947.md)|attendu ' >' pour terminer les arguments template, trouvé '*jeton*'|
|[Erreur du compilateur C2948](compiler-error-c2948.md)|instanciation explicite ; spécificateur de classe de stockage '*spécificateur*' non autorisé sur une spécialisation|
|C2949 d’erreur du compilateur|thread_local n’est pas pris en charge avec /kernel|
|Erreur du compilateur C2950|Obsolète.|
|[Erreur du compilateur C2951](compiler-error-c2951.md)|déclarations de modèle/générique sont autorisées uniquement à l’espace de noms global, ou portée de classe|
|[Erreur du compilateur C2952](compiler-error-c2952.md)|«*déclaration*' : déclaration de modèle/générique manquant de liste de paramètres de modèle/générique|
|[Erreur du compilateur C2953](compiler-error-c2953.md)|«*type*' : modèle de classe a déjà été défini|
|Erreur du compilateur C2954|argument word de l’instruction pas dans la plage|
|[Erreur du compilateur C2955](compiler-error-c2955.md)|«*type*' : utilisation de la classe modèle/générique nécessite la liste d’arguments de modèle/générique|
|C2956 d’erreur du compilateur|désallocation dimensionnée fonction 'operator delete (void *, size_t)' est choisie comme fonction de désallocation de positionnement.|
|[Erreur du compilateur C2957](compiler-error-c2957.md)|«*jeton*' : délimiteur gauche non valide : attendu ' < »|
|[Erreur du compilateur C2958](compiler-error-c2958.md)|gauche *délimiteur* , consultez «*fichier*(*line_number*) » n’a pas été équilibré correctement|
|[Erreur du compilateur C2959](compiler-error-c2959.md)|une classe ou fonction générique ne peut pas être un membre d’un modèle|
|C2960 d’erreur du compilateur|Obsolète.|
|C2961 d’erreur du compilateur|«*fonction*' : instanciations explicites incohérentes, une instanciation explicite précédente ne spécifiait pas '*argument*»|
|[Erreur du compilateur C2962](compiler-error-c2962.md)|Erreur de syntaxe : '*jeton*' : prévu de définition de fonction membre de classe de modèle se terminer par '}'|
|Erreur du compilateur C2963|Obsolète.|
|Erreur du compilateur C2964|Obsolète.|
|C2965 d’erreur du compilateur|__declspec (*spécificateur*) n’est pas pris en charge avec /kernel|
|C2966 d’erreur du compilateur|«*identificateur1*' : doit avoir le même __declspec(code_seg(...)) comme sa classe de base*identificateur2*»|
|C2967 d’erreur du compilateur|«*identificateur*' : une fonction virtuelle de substitution doit avoir le même __declspec(code_seg(...)) qu’une fonction virtuelle substituée|
|C2968 d’erreur du compilateur|«*identificateur*' : déclaration d’alias récurrente|
|[Erreur du compilateur C2969](compiler-error-c2969.md)|Erreur de syntaxe : '*jeton*' : définition de fonction de membre doit se terminer par '}'|
|[Erreur du compilateur C2970](compiler-error-c2970.md)|«*type*' : paramètre de modèle '*paramètre*' : '*argument*' : une expression impliquant des objets avec une liaison interne ne peut pas être utilisée comme argument sans type|
|[Erreur du compilateur C2971](compiler-error-c2971.md)|«*type*' : paramètre de modèle '*paramètre*' : '*argument*' : une variable avec une durée de stockage non statique ne peut pas être utilisée comme argument sans type|
|C2972 d’erreur du compilateur|«*type*' : paramètre de modèle '*paramètre*' : le type d’argument sans type n’est pas valide|
|[Erreur du compilateur C2973](compiler-error-c2973.md)|«*modèle*' : argument template non valide '*nombre*»|
|[Erreur du compilateur C2974](compiler-error-c2974.md)|«*type*' : argument de modèle/générique non valide pour '*paramètre*', type attendu|
|[Erreur du compilateur C2975](compiler-error-c2975.md)|«*type*' : argument template non valide pour '*paramètre*', expression de constante de compilation attendue|
|[Erreur du compilateur C2976](compiler-error-c2976.md)|«*type*' : trop peu d’arguments de modèle/générique|
|[Erreur du compilateur C2977](compiler-error-c2977.md)|«*type*' : trop d’arguments de modèle/générique|
|[Erreur du compilateur C2978](compiler-error-c2978.md)|Erreur de syntaxe : attendu '*MotClé1*'ou'*MotClé2*'; type trouvé'*type*' ; type de non paramètres ne sont pas pris en charge dans les génériques|
|[Erreur du compilateur C2979](compiler-error-c2979.md)|les spécialisations explicites ne sont pas prises en charge dans les génériques|
|C2980 d’erreur du compilateur|Gestion des exceptions C++ ne sont pas pris en charge avec /kernel|
|C2981 d’erreur du compilateur|la forme dynamique de '*mot clé*' n’est pas pris en charge avec /kernel|
|C2982 d’erreur du compilateur|'*déclaration*' : __declspec(code_seg(...)) différents utilisés : était '*identificateur1*« maintenant »*identificateur2*'|
|C2983 d’erreur du compilateur|«*déclaration*' : toutes les déclarations doivent avoir un __declspec(code_seg(...)) identiques|
|C2984 d’erreur du compilateur|Obsolète.|
|C2985 d’erreur du compilateur|«*argument*' : l’argument de __declspec(code_seg(...)) doit être une section de texte|
|C2986 d’erreur du compilateur|«*identificateur*' : __declspec(code_seg(...)) peut uniquement être appliqué à une classe ou une fonction|
|C2987 d’erreur du compilateur|une déclaration ne peut pas comporter simultanément __declspec (code_seg ('*identificateur*')) et __declspec (code_seg ('*valeur*'))|
|[Erreur du compilateur C2988](compiler-error-c2988.md)|définition/déclaration de modèle non reconnaissable|
|[Erreur du compilateur C2989](compiler-error-c2989.md)|«*classe*' : classe modèle/générique a déjà été déclaré en tant que modèle/générique sans classe|
|[Erreur du compilateur C2990](compiler-error-c2990.md)|«*classe*' : classe modèle/générique a déjà été déclarée comme un modèle/générique de classe|
|[Erreur du compilateur C2991](compiler-error-c2991.md)|redéfinition du paramètre de modèle/générique '*paramètre*'|
|[Erreur du compilateur C2992](compiler-error-c2992.md)|«*classe*' : liste de paramètres de modèle/générique non valide ou manquant|
|[Erreur du compilateur C2993](compiler-error-c2993.md)|«*type*' : type non conforme pour le paramètre de modèle sans type '*identificateur*»|
|[Erreur du compilateur C2994](compiler-error-c2994.md)|classe sans nom dans une liste de paramètres de modèle|
|[Erreur du compilateur C2995](compiler-error-c2995.md)|«*déclaration*' : modèle de fonction a déjà été défini|
|[Erreur du compilateur C2996](compiler-error-c2996.md)|«*fonction*' : définition de modèle de fonction récurrente|
|C2997 d’erreur du compilateur|«*fonction*' : limite de tableau ne peut pas être déduit à partir d’un initialiseur de membre par défaut|
|[Erreur du compilateur C2998](compiler-error-c2998.md)|«*déclarateur*' : ne peut pas être une définition de modèle|
|Erreur du compilateur C2999|Erreur inconnue choisissez la commande Support technique dans le menu aide de Visual C++ ou ouvrez le fichier d’aide de Support technique pour plus d’informations|
