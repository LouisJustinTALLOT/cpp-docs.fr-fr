---
title: C3100 d’erreurs du compilateur via C3199 | Documents Microsoft
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
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
dev_langs:
- C++
ms.assetid: 7bc40c2f-6a8d-488a-b665-f39375afee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 062ab968a51c38e9418a96b0df07eec3ae399ac3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283892"
---
# <a name="compiler-errors-c3100-through-c3199"></a>C3100 d’erreurs du compilateur via C3199

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’erreur générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Messages d’erreur

|Error|Message|
|-----------|-------------|
|[Erreur du compilateur C3100](compiler-error-c3100.md)|'*identificateur*' : qualificateur d’attribut inconnu|
|[Erreur du compilateur C3101](compiler-error-c3101.md)|expression non conforme pour l’argument d’attribut nommé '*identificateur*'|
|C3102 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C3103](compiler-error-c3103.md)|'*identificateur*' : argument nommé répété|
|[Erreur du compilateur C3104](compiler-error-c3104.md)|argument d’attribut non conforme|
|C3105 d’erreur du compilateur|'*symbole*' : ne peut pas être utilisé en tant qu’attribut|
|[Erreur du compilateur C3106](compiler-error-c3106.md)|'*attribut*' : les arguments sans nom doivent précéder les arguments nommés|
|C3107 d’erreur du compilateur|'*attribut*' : Impossible de définir les fonctions membres des attributs natifs|
|C3108 d’erreur du compilateur|Impossible de déduire un type comme une liste d’initialiseurs n’est pas une expression|
|C3109 d’erreur du compilateur|'*identificateur*' : les méthodes d’interface doivent utiliser le '__stdcall' ou '__cdecl' convention d’appel|
|[Erreur du compilateur C3110](compiler-error-c3110.md)|'*fonction*' : vous ne pouvez pas surcharger une méthode d’interface COM.|
|C3111 d’erreur du compilateur|Une liste d’initialiseurs ne peut pas être utilisée comme argument pour un paramètre de modèle par défaut|
|C3112 d’erreur du compilateur|'*interface*' : une interface peut uniquement être déclarée au niveau global ou de la portée espace de noms|
|[Erreur du compilateur C3113](compiler-error-c3113.md)|un 'interface/enum' ne peut pas être un modèle/générique|
|[Erreur du compilateur C3114](compiler-error-c3114.md)|'*identificateur*' : argument d’attribut nommé non valide|
|[Erreur du compilateur C3115](compiler-error-c3115.md)|'*attribut*' : cet attribut n’est pas autorisé sur '*construire*'|
|[Erreur du compilateur C3116](compiler-error-c3116.md)|'*spécificateur*' : classe de stockage non valide pour la méthode d’interface|
|[Erreur du compilateur C3117](compiler-error-c3117.md)|'*interface*' : une interface peut avoir uniquement une classe de base|
|[Erreur du compilateur C3118](compiler-error-c3118.md)|'*interface*' : les interfaces ne prennent pas en charge l’héritage virtuel|
|C3119 d’erreur du compilateur|alignas(void) n’est pas autorisée.|
|[Erreur du compilateur C3120](compiler-error-c3120.md)|'*identificateur*' : les méthodes d’interface ne peut pas prendre une liste d’arguments variables|
|[Erreur du compilateur C3121](compiler-error-c3121.md)|Impossible de changer GUID pour la classe*classe*'|
|C3122 d’erreur du compilateur|'*interface*' : une interface générique WinRT ne peut pas avoir de GUID|
|C3123 d’erreur du compilateur|Interface générique WinRT ne peut pas avoir de contraintes|
|C3124 d’erreur du compilateur|'signed char' n’est pas un type de données WinRT valid. Utilisez plutôt 'unsigned char', 'wchar_t' ou 'signed short'.|
|C3125 d’erreur du compilateur|'*type*' : type ne peut pas dériver directement ou indirectement de 'Platform::Exception'|
|[Erreur du compilateur C3126](compiler-error-c3126.md)|Impossible de définir une union '*union*'à l’intérieur de type de managed/WinRT'*type*'|
|C3127 d’erreur du compilateur|'*type*' : '*caractéristique*' caractéristique est utilisable uniquement sur une classe ref WinRT|
|C3128 d’erreur du compilateur|'*type*'n’a pas de vtable a été introduite par'*type*'|
|C3129 d’erreur du compilateur|'*type*' : __default_vptr_for_base est utilisable uniquement sur des types polymorphes définis localement et les bases|
|[Erreur du compilateur C3130](compiler-error-c3130.md)|L’erreur interne du compilateur : échec d’écriture de bloc de code injecté dans PDB|
|[Erreur du compilateur C3131](compiler-error-c3131.md)|projet doit avoir un attribut 'module' avec une propriété 'name'|
|[Erreur du compilateur C3132](compiler-error-c3132.md)|'*paramètre*' : paramètre tableaux ne peuvent être appliqués à un argument formel de type 'single-dimensional managed/WinRT array'|
|[Erreur du compilateur C3133](compiler-error-c3133.md)|Les attributs ne peuvent pas être appliqués aux varargs C++|
|[Erreur du compilateur C3134](compiler-error-c3134.md)|'*valeur*' : la valeur de l’argument d’attribut '*argument*'n’a pas de type valide'*type*'|
|[Erreur du compilateur C3135](compiler-error-c3135.md)|'*identificateur*' : une propriété ne peut pas avoir 'const' ou 'volatile' de type|
|[Erreur du compilateur C3136](compiler-error-c3136.md)|'*interface*' : une interface COM ne peut hériter que d’une autre interface COM, '*interface*' n’est pas une interface COM|
|[Erreur du compilateur C3137](compiler-error-c3137.md)|'*identificateur*' : une propriété ne peut pas être initialisée.|
|[Erreur du compilateur C3138](compiler-error-c3138.md)|'*identificateur*' : une «*attribut*' interface doit hériter de IDispatch ou d’une interface qui hérite de IDispatch|
|[Erreur du compilateur C3139](compiler-error-c3139.md)|'*type*' : Impossible d’exporter un UDT sans membres|
|[Erreur du compilateur C3140](compiler-error-c3140.md)|ne peut pas avoir plusieurs attributs 'module' dans la même unité de compilation|
|[Erreur du compilateur C3141](compiler-error-c3141.md)|'*interface*' : les interfaces ne prennent en charge que l’héritage public|
|[Erreur du compilateur C3142](compiler-error-c3142.md)|'*propriété*' : vous ne pouvez pas prendre l’adresse d’une propriété|
|C3143 d’erreur du compilateur|'*argument*' : argument d’attribut ne peut pas avoir plusieurs valeurs|
|C3144 d’erreur du compilateur|'*attribut*' : l’attribut requiert des arguments explicites, '*argument*» est sans nom|
|[Erreur du compilateur C3145](compiler-error-c3145.md)|'*identificateur*' : variable globale ou statique n’est peut-être pas type géré/WinRT '*type*'|
|Erreur du compilateur C3146|Obsolète.|
|Erreur du compilateur C3147|Obsolète.|
|Erreur du compilateur C3148|Obsolète.|
|[Erreur du compilateur C3149](compiler-error-c3149.md)|'*type*' : Impossible d’utiliser ce type ici sans un niveau supérieur '*jeton*'|
|[Erreur du compilateur C3150](compiler-error-c3150.md)|'*construire*' : '*attribut*' peut uniquement être appliqué à la classe, struct, interface, tableau ou pointeur|
|Erreur du compilateur C3151|Obsolète.|
|[Erreur du compilateur C3152](compiler-error-c3152.md)|'*fonction*' : '*mot clé*' peut uniquement être appliqué à une classe, une structure ou une fonction membre virtuelle|
|[Erreur du compilateur C3153](compiler-error-c3153.md)|'*interface*' : Impossible de créer une instance d’une interface|
|[Erreur du compilateur C3154](compiler-error-c3154.md)|Attendu ',' avant les points de suspension. Non-virgule séparées par des points de suspension non pris en charge sur les fonctions de tableau de paramètres.|
|[Erreur du compilateur C3155](compiler-error-c3155.md)|les attributs ne sont pas autorisés dans une propriété d’indexeur|
|[Erreur du compilateur C3156](compiler-error-c3156.md)|'*classe*' : vous ne peut pas avoir de définition locale d’un type managé/WinRT|
|[Erreur du compilateur C3157](compiler-error-c3157.md)|L’attribut ParamArray peut uniquement être appliqué au dernier paramètre|
|C3158 d’erreur du compilateur|'*fonction*' : '*mot clé*' peut uniquement être appliqué à une fonction membre virtuelle|
|[Erreur du compilateur C3159](compiler-error-c3159.md)|'*identificateur*' : Impossible de déclarer un tableau de pointeurs vers le type de valeur|
|[Erreur du compilateur C3160](compiler-error-c3160.md)|'*type*' : un membre de données d’une classe gérée/WinRT ne peut pas avoir ce type|
|[Erreur du compilateur C3161](compiler-error-c3161.md)|'*interface*' : classe, struct ou interface dans une interface d’imbrication non conforme ; l’imbrication d’une interface dans une classe ou un struct est non conforme|
|[Erreur du compilateur C3162](compiler-error-c3162.md)|'*type*' : un type référence qui a un destructeur ne peut pas être utilisé comme type de données membres static '*membre*'|
|[Erreur du compilateur C3163](compiler-error-c3163.md)|'*classe*' : attributs non cohérents avec la déclaration précédente|
|Erreur du compilateur C3164|Obsolète.|
|C3165 d’erreur du compilateur|'*valeur*' : Impossible de convertir une valeur intégrale ou à virgule flottante|
|[Erreur du compilateur C3166](compiler-error-c3166.md)|Obsolète. '*type*' : un membre de données d’une classe gérée/WinRT ne peut pas avoir de type '*type_pointeur* à intérieurs *managed_pointer_type*'|
|[Erreur du compilateur C3167](compiler-error-c3167.md)|Impossible d’initialiser le .NET Framework : Vérifiez qu’il est installé|
|[Erreur du compilateur C3168](compiler-error-c3168.md)|'*type*' : type d’enum sous-jacent non conforme|
|C3169 d’erreur du compilateur|'*type*' : Impossible de déduire le type de 'auto' à partir de '*type*'|
|[Erreur du compilateur C3170](compiler-error-c3170.md)|ne peut pas avoir des identificateurs de module différents dans un projet|
|[Erreur du compilateur C3171](compiler-error-c3171.md)|'*module*' : Impossible de spécifier des attributs de module différents dans un projet|
|[Erreur du compilateur C3172](compiler-error-c3172.md)|'*identificateur*' : Impossible de spécifier des attributs idl_module différents dans un projet|
|[Erreur du compilateur C3173](compiler-error-c3173.md)|incompatibilité de version dans la fusion idl|
|[Erreur du compilateur C3174](compiler-error-c3174.md)|attribut de module n’a pas été spécifié.|
|[Erreur du compilateur C3175](compiler-error-c3175.md)|'*fonction*' : Impossible d’appeler une méthode d’un type managé à partir de la fonction non managée '*fonction*'|
|[Erreur du compilateur C3176](compiler-error-c3176.md)|'*type*' : Impossible de déclarer un type valeur local|
|C3177 d’erreur du compilateur|Vous ne pouvez avoir une fonction de conversion en un type qui contienne «*type*'|
|C3178 d’erreur du compilateur|'*type*' : Impossible d’utiliser ParamArray dans une fonction avec des arguments par défaut|
|[Erreur du compilateur C3179](compiler-error-c3179.md)|un type managé/WinRT sans nom n’est pas autorisé.|
|[Erreur du compilateur C3180](compiler-error-c3180.md)|'*type*' : nom dépasse la limite métadonnées de '*nombre*' caractères|
|[Erreur du compilateur C3181](compiler-error-c3181.md)|'*type*' : opérande non valide pour *(opérateur)*|
|[Erreur du compilateur C3182](compiler-error-c3182.md)|'*type*' : une déclaration d’accès ou de la déclaration à l’aide de membre est non conforme au sein d’un type managé/WinRT|
|[Erreur du compilateur C3183](compiler-error-c3183.md)|Impossible de définir une classe sans nom, struct ou union à l’intérieur du type géré/WinRT '*classe*'|
|C3184 d’erreur du compilateur|Obsolète.|
|[Erreur du compilateur C3185](compiler-error-c3185.md)|'typeid' : utilisé avec le type géré/WinRT '*type*', utilisez '*opérateur*' à la place|
|Erreur du compilateur C3186|Obsolète.|
|[Erreur du compilateur C3187](compiler-error-c3187.md)|'*identificateur*' : est uniquement disponible dans le corps d’une fonction|
|Erreur du compilateur C3188|Obsolète.|
|[Erreur du compilateur C3189](compiler-error-c3189.md)|' typeid <*déclarateur*>': cette syntaxe n’est plus pris en charge, utilisez :: typeid à la place|
|[Erreur du compilateur C3190](compiler-error-c3190.md)|'*déclarateur*'avec les arguments template fournis n’est pas l’instanciation explicite d’une fonction membre de'*type*'|
|Erreur du compilateur C3191|Obsolète.|
|[Erreur du compilateur C3192](compiler-error-c3192.md)|Erreur de syntaxe : ' ^' n’est pas un opérateur préfixé (voulez-vous utiliser ' *'?)|
|C3193 d’erreur du compilateur|'*construire*' : requiert ' / clr' ou ' / ZW' option de ligne de commande|
|[Erreur du compilateur C3194](compiler-error-c3194.md)|'*type*' : un type valeur ne peut pas avoir un opérateur d’assignation|
|[Erreur du compilateur C3195](compiler-error-c3195.md)|'*mot clé*' : est réservé et ne peut pas être utilisé en tant que membre d’un type de classe ou une valeur ref. Les opérateurs CLR/WinRT doivent être définis à l’aide du mot clé 'operator'|
|[Erreur du compilateur C3196](compiler-error-c3196.md)|'*identificateur*' : utilisé plusieurs fois|
|[Erreur du compilateur C3197](compiler-error-c3197.md)|'*mot clé*' : peut uniquement être utilisé dans les définitions|
|[Erreur du compilateur C3198](compiler-error-c3198.md)|utilisation non valide des pragmas à virgule flottante : le pragma fenv_access ne fonctionne qu’en mode précision|
|[Erreur du compilateur C3199](compiler-error-c3199.md)|utilisation non valide des pragmas à virgule flottante : les exceptions ne sont pas pris en charge en mode sans précision|
