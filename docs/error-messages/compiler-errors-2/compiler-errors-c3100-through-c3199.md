---
title: Erreurs du compilateur C3100 à C3199
ms.date: 04/21/2019
f1_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
helpviewer_keywords:
- C3102
- C3105
- C3107
- C3108
- C3109
- C3111
- C3112
- C3119
- C3122
- C3123
- C3124
- C3125
- C3127
- C3128
- C3129
- C3143
- C3144
- C3146
- C3147
- C3148
- C3151
- C3158
- C3164
- C3165
- C3169
- C3177
- C3178
- C3184
- C3188
- C3191
- C3193
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
ms.openlocfilehash: efa3207a9fdfb81a52bf319a1cbc2da84084b6cd
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856821"
---
# <a name="compiler-errors-c3100-through-c3199"></a>Erreurs du compilateur C3100 à C3199

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur qui sont générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C3100](compiler-error-c3100.md)|«*identificateur*' : qualificateur d’attribut inconnu|
|[Erreur du compilateur C3101](compiler-error-c3101.md)|expression non conforme pour l’argument d’attribut nommé '*identificateur*'|
|Erreur du compilateur C3102|Obsolète.|
|[Erreur du compilateur C3103](compiler-error-c3103.md)|«*identificateur*' : argument nommé répété|
|[Erreur du compilateur C3104](compiler-error-c3104.md)|argument d’attribut non conforme|
|Erreur du compilateur C3105|«*symbole*' : ne peut pas être utilisé en tant qu’attribut|
|[Erreur du compilateur C3106](compiler-error-c3106.md)|«*attribut*' : arguments sans nom doivent précéder les arguments nommés|
|Erreur du compilateur C3107|«*attribut*' : Impossible de définir les fonctions membres des attributs natifs|
|Erreur du compilateur C3108|Impossible de déduire un type comme une liste d’initialiseurs n’est pas une expression|
|Erreur du compilateur C3109|«*identificateur*' : les méthodes d’interface doivent utiliser le '__stdcall' ou '__cdecl' convention d’appel|
|[Erreur du compilateur C3110](compiler-error-c3110.md)|«*fonction*' : vous ne pouvez pas surcharger une méthode d’interface COM|
|Erreur du compilateur C3111|Une liste d’initialiseurs ne peut pas être utilisée comme argument par défaut pour un paramètre de modèle|
|Erreur du compilateur C3112|«*interface*' : une interface ne peut être déclarée au niveau global ou de la portée de l’espace de noms|
|[Erreur du compilateur C3113](compiler-error-c3113.md)|un 'interface/enum' ne peut pas être un modèle/générique|
|[Erreur du compilateur C3114](compiler-error-c3114.md)|«*identificateur*' : argument d’attribut nommé non valide|
|[Erreur du compilateur C3115](compiler-error-c3115.md)|«*attribut*' : cet attribut n’est pas autorisé sur '*construire*»|
|[Erreur du compilateur C3116](compiler-error-c3116.md)|«*spécificateur*' : classe de stockage non valide pour la méthode d’interface|
|[Erreur du compilateur C3117](compiler-error-c3117.md)|«*interface*' : une interface peut avoir uniquement une classe de base|
|[Erreur du compilateur C3118](compiler-error-c3118.md)|«*interface*' : les interfaces ne prennent pas en charge l’héritage virtuel|
|Erreur du compilateur C3119|alignas (void) n’est pas autorisée.|
|[Erreur du compilateur C3120](compiler-error-c3120.md)|«*identificateur*' : les méthodes d’interface ne peut pas prendre une liste d’arguments variable|
|[Erreur du compilateur C3121](compiler-error-c3121.md)|Impossible de changer GUID pour la classe*classe*'|
|Erreur du compilateur C3122|«*interface*' : une interface générique WinRT ne peut pas avoir de GUID|
|Erreur du compilateur C3123|Interface générique WinRT ne peut pas avoir de contraintes|
|Erreur du compilateur C3124|'signed char' n’est pas un type de données WinRT valid. Utilisez plutôt 'unsigned char', 'wchar_t' ou 'signed short'.|
|Erreur du compilateur C3125|«*type*' : type ne peut pas dériver directement ou indirectement de 'Platform::Exception'|
|[Erreur du compilateur C3126](compiler-error-c3126.md)|Impossible de définir une union '*union*'à l’intérieur gérés/WinRT type'*type*'|
|Erreur du compilateur C3127|«*type*' : '*caractéristique*' caractéristique est utilisable uniquement sur une classe de référence WinRT|
|Erreur du compilateur C3128|«*type*'n’a pas de vtable a été introduite par'*type*»|
|Erreur du compilateur C3129|«*type*' : __default_vptr_for_base n’utilisable uniquement sur des bases et des types polymorphes définis localement|
|[Erreur du compilateur C3130](compiler-error-c3130.md)|Erreur interne du compilateur : échec d’écriture de bloc de code injecté dans PDB|
|[Erreur du compilateur C3131](compiler-error-c3131.md)|projet doit avoir un attribut 'module' avec une propriété 'name'|
|[Erreur du compilateur C3132](compiler-error-c3132.md)|«*paramètre*' : les tableaux de paramètres peuvent uniquement être appliqués à un argument formel de type 'single-dimensional gérés/WinRT array'|
|[Erreur du compilateur C3133](compiler-error-c3133.md)|Les attributs ne peuvent pas être appliqués aux varargs C++|
|[Erreur du compilateur C3134](compiler-error-c3134.md)|«*valeur*' : valeur de l’argument d’attribut '*argument*'n’a pas de type valide'*type*»|
|[Erreur du compilateur C3135](compiler-error-c3135.md)|«*identificateur*' : une propriété ne peut pas avoir une 'const' ou 'volatile' de type|
|[Erreur du compilateur C3136](compiler-error-c3136.md)|«*interface*' : une interface COM ne peut hériter que d’une autre interface COM, '*interface*' n’est pas une interface COM|
|[Erreur du compilateur C3137](compiler-error-c3137.md)|«*identificateur*' : une propriété ne peut pas être initialisée.|
|[Erreur du compilateur C3138](compiler-error-c3138.md)|«*identificateur*' : une «*attribut*' interface doit hériter de IDispatch ou d’une interface qui hérite de IDispatch|
|[Erreur du compilateur C3139](compiler-error-c3139.md)|«*type*' : Impossible d’exporter un UDT sans membres|
|[Erreur du compilateur C3140](compiler-error-c3140.md)|ne peut pas avoir plusieurs attributs 'module' dans la même unité de compilation|
|[Erreur du compilateur C3141](compiler-error-c3141.md)|«*interface*' : les interfaces ne prennent en charge que les héritages publics|
|[Erreur du compilateur C3142](compiler-error-c3142.md)|«*propriété*' : vous ne pouvez pas prendre l’adresse d’une propriété|
|Erreur du compilateur C3143|«*argument*' : argument d’attribut ne peut pas avoir plusieurs valeurs|
|Erreur du compilateur C3144|«*attribut*' : attribut requiert des arguments explicites, «*argument*» est sans nom|
|[Erreur du compilateur C3145](compiler-error-c3145.md)|«*identificateur*' : variable globale ou statique n’est peut-être pas gérés/WinRT type '*type*»|
|Erreur du compilateur C3146|Obsolète.|
|Erreur du compilateur C3147|Obsolète.|
|Erreur du compilateur C3148|Obsolète.|
|[Erreur du compilateur C3149](compiler-error-c3149.md)|«*type*' : Impossible d’utiliser ce type ici sans un niveau supérieur '*jeton*»|
|[Erreur du compilateur C3150](compiler-error-c3150.md)|«*construire*' : '*attribut*' peut uniquement être appliqué à la classe, struct, interface, tableau ou pointeur|
|Erreur du compilateur C3151|Obsolète.|
|[Erreur du compilateur C3152](compiler-error-c3152.md)|«*fonction*' : '*mot clé*' peut uniquement être appliqué à une classe, un struct ou une fonction membre virtuelle|
|[Erreur du compilateur C3153](compiler-error-c3153.md)|«*interface*' : Impossible de créer une instance d’une interface|
|[Erreur du compilateur C3154](compiler-error-c3154.md)|Attendu ',' avant les points de suspension. Non-virgule séparées par des points de suspension non pris en charge sur les fonctions de tableau de paramètre.|
|[Erreur du compilateur C3155](compiler-error-c3155.md)|les attributs ne sont pas autorisés dans un indexeur de propriété|
|[Erreur du compilateur C3156](compiler-error-c3156.md)|«*classe*' : vous ne peut pas avoir de définition locale d’un type géré/WinRT|
|[Erreur du compilateur C3157](compiler-error-c3157.md)|ParamArray attribut peut uniquement être appliqué au dernier paramètre|
|Erreur du compilateur C3158|«*fonction*' : '*mot clé*' peut uniquement être appliqué à une fonction membre virtuelle|
|[Erreur du compilateur C3159](compiler-error-c3159.md)|«*identificateur*' : Impossible de déclarer un tableau de pointeurs vers type valeur|
|[Erreur du compilateur C3160](compiler-error-c3160.md)|«*type*' : une donnée membre d’une classe gérée/WinRT ne peut pas avoir ce type|
|[Erreur du compilateur C3161](compiler-error-c3161.md)|«*interface*' : imbrication classe, structure ou interface dans une interface n’est pas conforme ; l’imbrication d’une interface dans une classe ou un struct n’est pas conforme|
|[Erreur du compilateur C3162](compiler-error-c3162.md)|«*type*' : un type référence qui a un destructeur ne peut pas être utilisé comme type de données membres static '*membre*»|
|[Erreur du compilateur C3163](compiler-error-c3163.md)|«*classe*' : attributs non cohérents avec la déclaration précédente|
|Erreur du compilateur C3164|Obsolète.|
|Erreur du compilateur C3165|«*valeur*' : Impossible de convertir en une valeur intégrale ou à virgule flottante|
|[Erreur du compilateur C3166](compiler-error-c3166.md)|Obsolète. «*type*' : une donnée membre d’une classe gérée/WinRT ne peut pas avoir de type '*type_pointeur* à intérieurs *managed_pointer_type*»|
|[Erreur du compilateur C3167](compiler-error-c3167.md)|Impossible d’initialiser le .NET Framework : Vérifiez qu’il est installé|
|[Erreur du compilateur C3168](compiler-error-c3168.md)|«*type*' : type d’enum sous-jacent non conforme|
|Erreur du compilateur C3169|«*type*' : Impossible de déduire le type de 'auto' à partir de '*type*»|
|[Erreur du compilateur C3170](compiler-error-c3170.md)|ne peut pas avoir des identificateurs de module différents dans un projet|
|[Erreur du compilateur C3171](compiler-error-c3171.md)|«*module*' : Impossible de spécifier des attributs de module différents dans un projet|
|[Erreur du compilateur C3172](compiler-error-c3172.md)|«*identificateur*' : Impossible de spécifier des attributs idl_module différents dans un projet|
|[Erreur du compilateur C3173](compiler-error-c3173.md)|incompatibilité de version dans la fusion idl|
|[Erreur du compilateur C3174](compiler-error-c3174.md)|attribut de module n’a pas été spécifié.|
|[Erreur du compilateur C3175](compiler-error-c3175.md)|'*fonction*' : Impossible d’appeler une méthode d’un type managé à partir de la fonction non managée '*fonction*'|
|[Erreur du compilateur C3176](compiler-error-c3176.md)|«*type*' : Impossible de déclarer un type valeur local|
|Erreur du compilateur C3177|Vous ne pouvez avoir une fonction de conversion en un type qui contienne «*type*'|
|Erreur du compilateur C3178|«*type*' : Impossible d’utiliser ParamArray dans une fonction avec des arguments par défaut|
|[Erreur du compilateur C3179](compiler-error-c3179.md)|un type géré/WinRT sans nom n’est pas autorisé.|
|[Erreur du compilateur C3180](compiler-error-c3180.md)|«*type*' : nom dépasse la limite métadonnées de '*nombre*' caractères|
|[Erreur du compilateur C3181](compiler-error-c3181.md)|«*type*' : opérande non valide pour *opérateur*|
|[Erreur du compilateur C3182](compiler-error-c3182.md)|«*type*' : une déclaration de déclaration using ou d’accès de membre n’est pas conforme au sein d’un type géré/WinRT|
|[Erreur du compilateur C3183](compiler-error-c3183.md)|Impossible de définir une classe sans nom, struct ou union à l’intérieur du type de gérés/WinRT '*classe*'|
|Erreur du compilateur C3184|Obsolète.|
|[Erreur du compilateur C3185](compiler-error-c3185.md)|'typeid' : utilisé sur un type géré/WinRT '*type*», utilisez '*opérateur*' à la place|
|Erreur du compilateur C3186|Obsolète.|
|[Erreur du compilateur C3187](compiler-error-c3187.md)|«*identificateur*' : est uniquement disponible dans le corps d’une fonction|
|Erreur du compilateur C3188|Obsolète.|
|[Erreur du compilateur C3189](compiler-error-c3189.md)|' typeid <*déclarateur*>': cette syntaxe n’est plus pris en charge, utilisez :: typeid à la place|
|[Erreur du compilateur C3190](compiler-error-c3190.md)|«*déclarateur*'avec les arguments template fournis n’est pas l’instanciation explicite d’une fonction membre de'*type*»|
|Erreur du compilateur C3191|Obsolète.|
|[Erreur du compilateur C3192](compiler-error-c3192.md)|Erreur de syntaxe : ' ^' n’est pas un opérateur préfixé (voulez-vous utiliser ' *'?)|
|Erreur du compilateur C3193|«*construire*' : requiert ' / clr' ou ' / ZW' option de ligne de commande|
|[Erreur du compilateur C3194](compiler-error-c3194.md)|«*type*' : un type valeur ne peut pas avoir un opérateur d’assignation|
|[Erreur du compilateur C3195](compiler-error-c3195.md)|«*mot clé*' : est réservé et ne peut pas être utilisé en tant que membre d’un type de classe ou une valeur ref. Opérateurs CLR/WinRT doivent être définis à l’aide du mot clé 'operator'|
|[Erreur du compilateur C3196](compiler-error-c3196.md)|«*identificateur*' : utilisé plusieurs fois|
|[Erreur du compilateur C3197](compiler-error-c3197.md)|«*mot clé*' : peut uniquement être utilisé dans les définitions|
|[Erreur du compilateur C3198](compiler-error-c3198.md)|utilisation non valide des pragmas à virgule flottante : le pragma fenv_access ne fonctionne qu’en mode précision|
|[Erreur du compilateur C3199](compiler-error-c3199.md)|utilisation non valide des pragmas à virgule flottante : les exceptions ne sont pas pris en charge en mode sans précision|

## <a name="see-also"></a>Voir aussi

[C /C++ compilateur et build erreurs et avertissements des outils](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
