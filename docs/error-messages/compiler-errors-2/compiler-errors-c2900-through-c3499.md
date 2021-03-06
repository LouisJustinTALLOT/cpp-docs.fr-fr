---
description: 'En savoir plus sur : Erreurs du compilateur C2900 à C2999'
title: Erreurs du compilateur C2900 à C2999
ms.date: 04/21/2019
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
ms.openlocfilehash: 73770588a27bb0f5150f3334f33e0a1c33aa2296
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238763"
---
# <a name="compiler-errors-c2900-through-c2999"></a>Erreurs du compilateur C2900 à C2999

Les Articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|Erreur du compilateur C2900|'*déclarateur*' : les modèles de fonction membre des classes WinRT doivent être’Private', 'Internal’ou’protected Private'|
|Erreur du compilateur C2901|'*identificateur*' : une interface ou un délégué générique ne peut pas être public|
|[Erreur du compilateur C2902](compiler-error-c2902.md)|'*jeton*' : jeton inattendu après’modèle/générique', identificateur attendu|
|[Erreur du compilateur C2903](compiler-error-c2903.md)|'*identificateur*' : le symbole n’est ni un modèle de classe/générique, ni un modèle de fonction/générique|
|[Erreur du compilateur C2904](compiler-error-c2904.md)|'*identificateur*' : nom déjà utilisé pour un modèle dans la portée actuelle|
|Erreur du compilateur C2905|Obsolète.|
|[Erreur du compilateur C2906](compiler-error-c2906.md)|'*template*' : une spécialisation explicite requiert’template <> '|
|Erreur du compilateur C2907|l’argument Register'*Number*'ne spécifie pas un numéro de Registre valide|
|[Erreur du compilateur C2908](compiler-error-c2908.md)|spécialisation explicite ; '*template*'a déjà été instancié|
|[Erreur du compilateur C2909](compiler-error-c2909.md)|'*identifier*' : l’instanciation explicite d’un modèle de fonction exige un type de retour|
|[Erreur du compilateur C2910](compiler-error-c2910.md)|'*fonction*' : ne peut pas être explicitement spécialisé|
|[Erreur du compilateur C2911](compiler-error-c2911.md)|'*membre*' : ne peut pas être déclaré ou défini dans la portée actuelle|
|[Erreur du compilateur C2912](compiler-error-c2912.md)|la spécialisation explicite'*déclaration*'n’est pas une spécialisation d’un modèle de fonction|
|[Erreur du compilateur C2913](compiler-error-c2913.md)|spécialisation explicite ; '*déclaration*'n’est pas une spécialisation d’un modèle de classe|
|[Erreur du compilateur C2914](compiler-error-c2914.md)|'*identifier*' : impossible de déduire un argument de modèle/générique, car l’argument de fonction est ambigu|
|Erreur du compilateur C2915|'*identificateur*' : '*type*'ne peut pas être utilisé directement sur la surface publiée d’un type WinRT. Utilisez « Platform :: Object ^ » à la place pour passer ce type|
|Erreur du compilateur C2916|'*identifier*' : [FlagsAttribute] doit (uniquement) être spécifié sur un enum public avec un type sous-jacent’unsigned int'|
|[Erreur du compilateur C2917](compiler-error-c2917.md)|'*identificateur*' : paramètre de modèle non valide|
|[Erreur du compilateur C2918](compiler-error-c2918.md)|'*identificateur*' : les propriétés indexées ne peuvent pas être utilisées sur la surface publiée d’un type WinRT|
|[Erreur du compilateur C2919](compiler-error-c2919.md)|'*type*' : les opérateurs ne peuvent pas être utilisés sur la surface publiée d’un type WinRT|
|[Erreur du compilateur C2920](compiler-error-c2920.md)|redéfinition : '*type*' : le modèle de classe/générique a déjà été déclaré en tant que'*DECLARATION*'|
|[Erreur du compilateur C2921](compiler-error-c2921.md)|redéfinition : '*type*' : modèle de classe/générique en cours de *redéclaration comme’declaration*'|
|Erreur du compilateur C2922|'*interface*' : une interface WinRT ne peut pas contenir de membres statiques|
|[Erreur du compilateur C2923](compiler-error-c2923.md)|'*type*' : '*identifier*'n’est pas un argument de type modèle/générique valide pour le paramètre'*paramètre*'|
|Erreur du compilateur C2924|argument de routine __declspec (interruption) non dans R2|
|Erreur du compilateur C2925|la routine de __declspec (interruption) ne peut pas utiliser de virgule flottante|
|Erreur du compilateur C2926|'*identificateur*' : un initialiseur de membre par défaut n’est pas autorisé pour un membre d’un struct anonyme au sein d’une Union|
|[Erreur du compilateur C2927](compiler-error-c2927.md)|'*identificateur*' : un modèle de fonction doit être appelé avec au moins un argument|
|[Erreur du compilateur C2928](compiler-error-c2928.md)|instanciation explicite ; '*identifier*'n’est pas une fonction ni une donnée membre static de la classe de modèle'*Class*'|
|[Erreur du compilateur C2929](compiler-error-c2929.md)|'*declarator*' : instanciation explicite ; Impossible d’imposer et de supprimer explicitement l’instanciation d’un membre de classe de modèle|
|[Erreur du compilateur C2930](compiler-error-c2930.md)|'*classe*' : ID-modèle/générique-id redéfini comme énumérateur de' *identificateur* d’énumération'|
|[Erreur du compilateur C2931](compiler-error-c2931.md)|'*classe1*' : ID de modèle/générique-id redéfini comme fonction membre de'*Class2*'|
|[Erreur du compilateur C2932](compiler-error-c2932.md)|'*type*' : template-ID/Generic-id redéfini comme donnée membre de'*identifier*'|
|[Erreur du compilateur C2933](compiler-error-c2933.md)|'*type*' : template-ID/Generic-id redéfini comme membre typedef de'*identifier*'|
|[Erreur du compilateur C2934](compiler-error-c2934.md)|'*type*' : template-ID/Generic-id redéfini comme'*Item*'imbriqué de'*identifier*'|
|[Erreur du compilateur C2935](compiler-error-c2935.md)|'*type*' : template-ID/Generic-id redéfini comme fonction globale|
|[Erreur du compilateur C2936](compiler-error-c2936.md)|'*type*' : template-ID/Generic-id redéfini comme variable globale de données|
|[Erreur du compilateur C2937](compiler-error-c2937.md)|'*type*' : ID de modèle/générique-id redéfini comme typedef global|
|Erreur du compilateur C2938|'*identificateur*' : échec de spécialisation du modèle d’alias|
|[Erreur du compilateur C2939](compiler-error-c2939.md)|'*type*' : ID de modèle/générique-id redéfini comme variable de données locale|
|[Erreur du compilateur C2940](compiler-error-c2940.md)|'*type*' : ID de modèle/générique-id redéfini comme typedef local|
|[Erreur du compilateur C2941](compiler-error-c2941.md)|'*type*' : template-ID/Generic-id redéfini comme'*Item*'local|
|[Erreur du compilateur C2942](compiler-error-c2942.md)|'*type*' : template-ID/Generic-id redéfini comme argument formel d’une fonction|
|[Erreur du compilateur C2943](compiler-error-c2943.md)|'*type*' : template-ID/Generic-id redéfini comme argument de type d’un modèle|
|[Erreur du compilateur C2944](compiler-error-c2944.md)|'*type*' : template-ID/Generic-id redéfini comme argument de valeur d’un modèle|
|[Erreur du compilateur C2945](compiler-error-c2945.md)|l'instanciation explicite ne fait pas référence à une spécialisation de classe de modèle|
|[Erreur du compilateur C2946](compiler-error-c2946.md)|instanciation explicite ; '*type*'n’est pas une spécialisation de classe de modèle|
|[Erreur du compilateur C2947](compiler-error-c2947.md)|' > 'attendu pour terminer les arguments template, '*Token*'trouvé|
|[Erreur du compilateur C2948](compiler-error-c2948.md)|instanciation explicite ; spécificateur de classe de stockage'*specifier*'non autorisé sur une spécialisation|
|Erreur du compilateur C2949|thread_local n’est pas pris en charge avec/kernel|
|Erreur du compilateur C2950|Obsolète.|
|[Erreur du compilateur C2951](compiler-error-c2951.md)|les déclarations modèle/générique sont autorisées uniquement au niveau de l’espace de noms global, de l’espace de noms ou de la classe|
|[Erreur du compilateur C2952](compiler-error-c2952.md)|'*déclaration*' : la liste de paramètres génériques/template n’est pas une déclaration de modèle/générique|
|[Erreur du compilateur C2953](compiler-error-c2953.md)|'*type*' : un modèle de classe a déjà été défini|
|Erreur du compilateur C2954|argument de mot d’instruction non compris dans la plage|
|[Erreur du compilateur C2955](compiler-error-c2955.md)|'*type*' : l’utilisation d’un modèle de classe/générique nécessite une liste d’arguments modèle/générique|
|Erreur du compilateur C2956|la fonction de désallocation dimensionnée’operator delete (void *, size_t) 'est choisie comme fonction de désallocation de positionnement.|
|[Erreur du compilateur C2957](compiler-error-c2957.md)|'*Token*' : délimiteur gauche non valide : ' < 'attendu|
|[Erreur du compilateur C2958](compiler-error-c2958.md)|le *délimiteur* gauche trouvé dans'*file*(*line_number*) 'n’a pas été correctement mis en correspondance|
|[Erreur du compilateur C2959](compiler-error-c2959.md)|une classe ou une fonction générique ne peut pas être membre d’un modèle|
|Erreur du compilateur C2960|Obsolète.|
|Erreur du compilateur C2961|'*fonction*' : instanciations explicites incohérentes, une instanciation explicite précédente ne spécifiait pas'*argument*'|
|[Erreur du compilateur C2962](compiler-error-c2962.md)|erreur de syntaxe : '*Token*' : une définition de fonction membre de classe de modèle attendue se termine par'} '|
|Erreur du compilateur C2963|Obsolète.|
|Erreur du compilateur C2964|Obsolète.|
|Erreur du compilateur C2965|__declspec (*specifier*) n’est pas pris en charge avec/kernel|
|Erreur du compilateur C2966|'*identificateur1*' : doit avoir le même __declspec (code_seg (...)) que sa classe de base'*identificateur2*'|
|Erreur du compilateur C2967|'*identificateur*' : une fonction virtuelle de substitution doit avoir le même __declspec (code_seg (...)) qu’une fonction virtuelle substituée|
|Erreur du compilateur C2968|'*identificateur*' : déclaration d’alias récurrente|
|[Erreur du compilateur C2969](compiler-error-c2969.md)|erreur de syntaxe : '*Token*' : la définition d’une fonction membre doit se terminer par'} '|
|[Erreur du compilateur C2970](compiler-error-c2970.md)|'*type*' : paramètre de modèle'*paramètre*' : '*argument*' : une expression impliquant des objets avec une liaison interne ne peut pas être utilisée comme argument sans type|
|[Erreur du compilateur C2971](compiler-error-c2971.md)|'*type*' : paramètre de modèle'*paramètre*' : '*argument*' : une variable avec une durée de stockage non statique ne peut pas être utilisée comme argument sans type|
|Erreur du compilateur C2972|'*type*' : paramètre de modèle'*paramètre*' : le type d’argument sans type n’est pas valide|
|[Erreur du compilateur C2973](compiler-error-c2973.md)|'*modèle*' : argument template non valide'*numéro*'|
|[Erreur du compilateur C2974](compiler-error-c2974.md)|'*type*' : argument générique/template non valide pour'*Parameter*', type attendu|
|[Erreur du compilateur C2975](compiler-error-c2975.md)|'*type*' : argument template non valide pour'*Parameter*', expression constante au moment de la compilation attendue|
|[Erreur du compilateur C2976](compiler-error-c2976.md)|'*type*' : nombre d’arguments template/générique insuffisant|
|[Erreur du compilateur C2977](compiler-error-c2977.md)|'*type*' : arguments modèle/générique trop nombreux|
|[Erreur du compilateur C2978](compiler-error-c2978.md)|erreur de syntaxe : '*keyword1*'ou'*keyword2*'attendu ; type'*type*'trouvé ; les paramètres sans type ne sont pas pris en charge dans les génériques|
|[Erreur du compilateur C2979](compiler-error-c2979.md)|les spécialisations explicites ne sont pas prises en charge dans les génériques|
|Erreur du compilateur C2980|La gestion des exceptions C++ n’est pas prise en charge avec/kernel|
|Erreur du compilateur C2981|la forme dynamique de'*Keyword*'n’est pas prise en charge avec/kernel|
|Erreur du compilateur C2982|'*déclaration*' : différentes __declspec (code_seg (...)) utilisées : '*identificateur1*'maintenant'*identificateur2*'|
|Erreur du compilateur C2983|'*déclaration*' : toutes les déclarations doivent avoir un __declspec identique (code_seg (...))|
|Erreur du compilateur C2984|Obsolète.|
|Erreur du compilateur C2985|'*argument*' : l’argument de __declspec (code_seg (...)) doit être une section de texte|
|Erreur du compilateur C2986|'*identificateur*' : __declspec (code_seg (...)) ne peut s’appliquer qu’à une classe ou une fonction|
|Erreur du compilateur C2987|une déclaration ne peut pas avoir les deux __declspec (code_seg ('*identifier*')) et __declspec (code_seg ('*value*'))|
|[Erreur du compilateur C2988](compiler-error-c2988.md)|Déclaration/définition de modèle non reconnaissable|
|[Erreur du compilateur C2989](compiler-error-c2989.md)|'*classe*' : le modèle de classe/générique a déjà été déclaré en tant que modèle/générique non-classe|
|[Erreur du compilateur C2990](compiler-error-c2990.md)|'*classe*' : modèle/générique sans classe a déjà été déclaré en tant que modèle de classe/générique|
|[Erreur du compilateur C2991](compiler-error-c2991.md)|redéfinition du paramètre de modèle/générique'*paramètre*'|
|[Erreur du compilateur C2992](compiler-error-c2992.md)|'*classe*' : liste de paramètres de modèle/générique non valide ou manquante|
|[Erreur du compilateur C2993](compiler-error-c2993.md)|'*type*' : type non conforme pour le paramètre de modèle sans type'*identifier*'|
|[Erreur du compilateur C2994](compiler-error-c2994.md)|classe sans nom dans une liste de paramètres de modèle|
|[Erreur du compilateur C2995](compiler-error-c2995.md)|'*déclaration*' : le modèle de fonction a déjà été défini|
|[Erreur du compilateur C2996](compiler-error-c2996.md)|'*fonction*' : définition de modèle de fonction récursive|
|Erreur du compilateur C2997|'*fonction*' : la liaison de tableau ne peut pas être déduite d’un initialiseur de membre par défaut|
|[Erreur du compilateur C2998](compiler-error-c2998.md)|'*déclarateur*' : ne peut pas être une définition de modèle|
|Erreur du compilateur C2999|ERREUR inconnue Veuillez choisir la commande support technique dans le menu ? (aide) du Visual C++ ou ouvrez le fichier d’aide du support technique pour plus d’informations|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
