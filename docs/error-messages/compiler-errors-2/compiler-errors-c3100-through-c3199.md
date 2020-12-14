---
description: 'En savoir plus sur : Erreurs du compilateur C3100 à C3199'
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
ms.openlocfilehash: d2398fa8ae783a34662efc361730a5054a982458
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238711"
---
# <a name="compiler-errors-c3100-through-c3199"></a>Erreurs du compilateur C3100 à C3199

Les Articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C3100](compiler-error-c3100.md)|'*identificateur*' : qualificateur d’attribut inconnu|
|[Erreur du compilateur C3101](compiler-error-c3101.md)|expression non conforme pour l’argument d’attribut nommé'*identifier*'|
|Erreur du compilateur C3102|Obsolète.|
|[Erreur du compilateur C3103](compiler-error-c3103.md)|'*identificateur*' : argument nommé répété|
|[Erreur du compilateur C3104](compiler-error-c3104.md)|argument d’attribut non conforme|
|Erreur du compilateur C3105|'*symbol*' : ne peut pas être utilisé en tant qu’attribut|
|[Erreur du compilateur C3106](compiler-error-c3106.md)|'*attribute*' : les arguments sans nom doivent précéder les arguments nommés|
|Erreur du compilateur C3107|'*attribute*' : impossible de définir les fonctions membres des attributs natifs|
|Erreur du compilateur C3108|Impossible de déduire un type, car une liste d’initialiseurs n’est pas une expression|
|Erreur du compilateur C3109|'*identificateur*' : les méthodes d’interface doivent utiliser la Convention d’appel' __stdcall’ou' __cdecl'|
|[Erreur du compilateur C3110](compiler-error-c3110.md)|'*fonction*' : impossible de surcharger une méthode d’interface com|
|Erreur du compilateur C3111|Une liste d’initialiseurs ne peut pas être utilisée en tant qu’argument par défaut pour un paramètre de modèle|
|Erreur du compilateur C3112|'*interface*' : une interface peut être déclarée uniquement au niveau de la portée globale ou de l’espace de noms|
|[Erreur du compilateur C3113](compiler-error-c3113.md)|un’interface/enum’ne peut pas être un modèle/générique|
|[Erreur du compilateur C3114](compiler-error-c3114.md)|'*identificateur*' : argument d’attribut nommé non valide|
|[Erreur du compilateur C3115](compiler-error-c3115.md)|'*attribute*' : cet attribut n’est pas autorisé sur'*Construct*'|
|[Erreur du compilateur C3116](compiler-error-c3116.md)|'*specifier*' : classe de stockage non valide pour la méthode d’interface|
|[Erreur du compilateur C3117](compiler-error-c3117.md)|'*interface*' : une interface ne peut avoir qu’une seule classe de base|
|[Erreur du compilateur C3118](compiler-error-c3118.md)|'*interface*' : les interfaces ne prennent pas en charge l’héritage virtuel|
|Erreur du compilateur C3119|alignas (void) n’est pas autorisé|
|[Erreur du compilateur C3120](compiler-error-c3120.md)|'*identificateur*' : les méthodes d’interface ne peuvent pas accepter une liste d’arguments variable|
|[Erreur du compilateur C3121](compiler-error-c3121.md)|Impossible de changer le GUID pour la classe'*Class*'|
|Erreur du compilateur C3122|'*interface*' : une interface générique WinRT ne peut pas avoir de GUID|
|Erreur du compilateur C3123|L’interface générique WinRT ne peut pas avoir de contraintes|
|Erreur du compilateur C3124|'signed Char’n’est pas un type de données WinRT valide. Utilisez « unsigned char », « wchar_t » ou « signed Short » à la place.|
|Erreur du compilateur C3125|'*type*' : le type ne peut pas dériver directement ni indirectement de’Platform :: exception'|
|[Erreur du compilateur C3126](compiler-error-c3126.md)|Impossible de définir une Union'*Union*'à l’intérieur du type managé/WinRT'*type*'|
|Erreur du compilateur C3127|'*type*' : le trait'*trait*'ne peut être utilisé que sur une classe ref WinRT|
|Erreur du compilateur C3128|'*type*'n’a pas de vtable introduit par'*type*'|
|Erreur du compilateur C3129|'*type*' : __default_vptr_for_base ne peut être utilisé que sur des bases et des types polymorphes définis localement|
|[Erreur du compilateur C3130](compiler-error-c3130.md)|Erreur interne du compilateur : échec de l’écriture du bloc de code injecté dans PDB|
|[Erreur du compilateur C3131](compiler-error-c3131.md)|le projet doit avoir un attribut’module’avec une propriété’name'|
|[Erreur du compilateur C3132](compiler-error-c3132.md)|'*paramètre*' : les tableaux de paramètres ne peuvent être appliqués qu’à un argument formel de type’Single-unidimensionnel Managed/WinRT array'|
|[Erreur du compilateur C3133](compiler-error-c3133.md)|Les attributs ne peuvent pas être appliqués aux varargs C++|
|[Erreur du compilateur C3134](compiler-error-c3134.md)|'*valeur*' : la valeur de l’argument d’attribut'*argument*'n’a pas un type valide'*type*'|
|[Erreur du compilateur C3135](compiler-error-c3135.md)|'*identificateur*' : une propriété ne peut pas avoir un type’const’ou’volatile'|
|[Erreur du compilateur C3136](compiler-error-c3136.md)|'*interface*' : une interface com ne peut hériter que d’une autre interface com, '*interface*'n’est pas une interface com|
|[Erreur du compilateur C3137](compiler-error-c3137.md)|'*identificateur*' : une propriété ne peut pas être initialisée|
|[Erreur du compilateur C3138](compiler-error-c3138.md)|'*identificateur*' : une interface'*attribute*'doit hériter de IDispatch ou d’une interface qui hérite de IDispatch|
|[Erreur du compilateur C3139](compiler-error-c3139.md)|'*type*' : impossible d’exporter un UDT sans membres|
|[Erreur du compilateur C3140](compiler-error-c3140.md)|Impossible d’avoir plusieurs attributs’module’dans la même unité de compilation|
|[Erreur du compilateur C3141](compiler-error-c3141.md)|'*interface*' : les interfaces ne prennent en charge que l’héritage public|
|[Erreur du compilateur C3142](compiler-error-c3142.md)|'*Property*' : vous ne pouvez pas prendre l’adresse d’une propriété|
|Erreur du compilateur C3143|'*argument*' : l’argument d’attribut ne peut pas avoir plusieurs valeurs|
|Erreur du compilateur C3144|'*attribute*' : l’attribut requiert des arguments explicites, '*argument*'est sans nom|
|[Erreur du compilateur C3145](compiler-error-c3145.md)|'*identificateur*' : une variable globale ou statique ne peut pas avoir un type managé/WinRT'*type*'|
|Erreur du compilateur C3146|Obsolète.|
|Erreur du compilateur C3147|Obsolète.|
|Erreur du compilateur C3148|Obsolète.|
|[Erreur du compilateur C3149](compiler-error-c3149.md)|'*type*' : impossible d’utiliser ce type ici sans un'*Token*'de niveau supérieur|
|[Erreur du compilateur C3150](compiler-error-c3150.md)|'*Construct*' : '*attribute*'ne peut s’appliquer qu’à une classe, un struct, une interface, un tableau ou un pointeur|
|Erreur du compilateur C3151|Obsolète.|
|[Erreur du compilateur C3152](compiler-error-c3152.md)|'*Function*' : '*Keyword*'ne peut s’appliquer qu’à une classe, une structure ou une fonction membre virtuelle|
|[Erreur du compilateur C3153](compiler-error-c3153.md)|'*interface*' : vous ne pouvez pas créer une instance d’une interface|
|[Erreur du compilateur C3154](compiler-error-c3154.md)|', 'Attendu avant les points de suspension. Points de suspension séparés par des virgules non pris en charge dans les fonctions de tableau de paramètres.|
|[Erreur du compilateur C3155](compiler-error-c3155.md)|les attributs ne sont pas autorisés dans un indexeur de propriété|
|[Erreur du compilateur C3156](compiler-error-c3156.md)|'*classe*' : vous ne pouvez pas avoir de définition locale d’un type managé/WinRT|
|[Erreur du compilateur C3157](compiler-error-c3157.md)|L’attribut ParamArray ne peut être appliqué qu’au dernier paramètre|
|Erreur du compilateur C3158|'*fonction*' : '*Keyword*'ne peut s’appliquer qu’à une fonction membre virtuelle|
|[Erreur du compilateur C3159](compiler-error-c3159.md)|'*identificateur*' : le tableau de pointeurs vers le type valeur ne peut pas être déclaré|
|[Erreur du compilateur C3160](compiler-error-c3160.md)|'*type*' : les données membres d’une classe managée/WinRT ne peuvent pas avoir ce type|
|[Erreur du compilateur C3161](compiler-error-c3161.md)|'*interface*' : l’imbrication d’une classe, d’une structure ou d’une interface dans une interface n’est pas conforme ; l’imbrication d’une interface dans une classe ou un struct n’est pas conforme|
|[Erreur du compilateur C3162](compiler-error-c3162.md)|'*type*' : un type référence qui a un destructeur ne peut pas être utilisé comme type de données membres static'*member*'|
|[Erreur du compilateur C3163](compiler-error-c3163.md)|'*classe*' : attributs non cohérents avec la déclaration précédente|
|Erreur du compilateur C3164|Obsolète.|
|Erreur du compilateur C3165|'*valeur*' : impossible de convertir en valeur intégrale ou à virgule flottante|
|[Erreur du compilateur C3166](compiler-error-c3166.md)|Obsolète. '*type*' : un membre de données d’une classe managée/WinRT ne peut pas avoir le type'*pointer_type* à l’intérieur du *managed_pointer_type*'|
|[Erreur du compilateur C3167](compiler-error-c3167.md)|Impossible d’initialiser .NET Framework : Assurez-vous qu’il est installé|
|[Erreur du compilateur C3168](compiler-error-c3168.md)|'*type*' : type sous-jacent non conforme pour enum|
|Erreur du compilateur C3169|'*type*' : impossible de déduire le type de’auto’à partir de'*type*'|
|[Erreur du compilateur C3170](compiler-error-c3170.md)|Impossible d’avoir des identificateurs de module différents dans un projet|
|[Erreur du compilateur C3171](compiler-error-c3171.md)|'*module*' : impossible de spécifier des attributs de module différents dans un projet|
|[Erreur du compilateur C3172](compiler-error-c3172.md)|'*identificateur*' : impossible de spécifier des attributs de idl_module différents dans un projet|
|[Erreur du compilateur C3173](compiler-error-c3173.md)|incompatibilité de version dans la fusion IDL|
|[Erreur du compilateur C3174](compiler-error-c3174.md)|l’attribut module n’a pas été spécifié|
|[Erreur du compilateur C3175](compiler-error-c3175.md)|'*fonction*' : impossible d’appeler une méthode d’un type managé à partir d’une fonction non managée'*fonction*'|
|[Erreur du compilateur C3176](compiler-error-c3176.md)|'*type*' : impossible de déclarer un type valeur local|
|Erreur du compilateur C3177|vous ne pouvez pas avoir une fonction de conversion en un type contenant'*type*'|
|Erreur du compilateur C3178|'*type*' : impossible d’utiliser ParamArray dans une fonction avec des arguments par défaut|
|[Erreur du compilateur C3179](compiler-error-c3179.md)|un type managé/WinRT sans nom n’est pas autorisé|
|[Erreur du compilateur C3180](compiler-error-c3180.md)|'*type*' : le nom dépasse la limite de métadonnées de'*Number*'caractères|
|[Erreur du compilateur C3181](compiler-error-c3181.md)|'*type*' : opérande non valide pour l' *opérateur*|
|[Erreur du compilateur C3182](compiler-error-c3182.md)|'*type*' : une déclaration using de membre ou une déclaration d’accès est non conforme dans un type managé/WinRT|
|[Erreur du compilateur C3183](compiler-error-c3183.md)|Impossible de définir une classe, un struct ou une Union sans nom à l’intérieur du type managé/WinRT'*classe*'|
|Erreur du compilateur C3184|Obsolète.|
|[Erreur du compilateur C3185](compiler-error-c3185.md)|'typeid' : utilisé sur le type managé/WinRT'*type*', utilisez'*Operator*'à la place|
|Erreur du compilateur C3186|Obsolète.|
|[Erreur du compilateur C3187](compiler-error-c3187.md)|'*identificateur*' : est uniquement disponible dans le corps d’une fonction|
|Erreur du compilateur C3188|Obsolète.|
|[Erreur du compilateur C3189](compiler-error-c3189.md)|'typeid<*déclarateur*> ' : cette syntaxe n’est plus prise en charge, utilisez :: typeid à la place|
|[Erreur du compilateur C3190](compiler-error-c3190.md)|'*declarator*'avec les arguments template fournis n’est pas l’instanciation explicite d’une fonction membre de'*type*'|
|Erreur du compilateur C3191|Obsolète.|
|[Erreur du compilateur C3192](compiler-error-c3192.md)|erreur de syntaxe : ' ^ 'n’est pas un opérateur de préfixe (vouliez-vous dire' * ' ?)|
|Erreur du compilateur C3193|'*Construct*' : requiert l’option de ligne de commande'/CLR’ou'/ZW'|
|[Erreur du compilateur C3194](compiler-error-c3194.md)|'*type*' : un type valeur ne peut pas avoir d’opérateur d’assignation|
|[Erreur du compilateur C3195](compiler-error-c3195.md)|'*Keyword*' : est réservé et ne peut pas être utilisé en tant que membre d’une classe ref ou d’un type valeur. Les opérateurs CLR/WinRT doivent être définis à l’aide du mot clé’operator'|
|[Erreur du compilateur C3196](compiler-error-c3196.md)|'*identificateur*' : utilisé plusieurs fois|
|[Erreur du compilateur C3197](compiler-error-c3197.md)|'*Keyword*' : ne peut être utilisé que dans les définitions|
|[Erreur du compilateur C3198](compiler-error-c3198.md)|utilisation non valide des pragmas à virgule flottante : fenv_access pragma ne fonctionne qu’en mode precise|
|[Erreur du compilateur C3199](compiler-error-c3199.md)|utilisation non valide des pragmas à virgule flottante : les exceptions ne sont pas prises en charge en mode non précis|

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements du compilateur C/C++ et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Erreurs du compilateur C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
