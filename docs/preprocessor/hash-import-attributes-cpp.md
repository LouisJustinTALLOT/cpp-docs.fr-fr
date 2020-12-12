---
description: 'En savoir plus sur les attributs suivants : #import (C++)'
title: '#import, attributs (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 87719ba549efab4e0acf13d7e957c6841900d5fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300449"
---
# <a name="import-attributes-c"></a>attributs #import (C++)

Fournit des liens vers des attributs utilisés avec la `#import` directive.

**Spécifique à Microsoft**

Les attributs suivants sont disponibles pour la `#import` directive.

|Attribut|Description|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|Renomme des mots réservés C++ en ajoutant deux traits de soulignement (__) au nom de variable pour résoudre les conflits potentiels entre les noms.|
|[auto_search](../preprocessor/auto-search.md)|Spécifie que, lorsqu'une bibliothèque de types est référencée avec #import et fait elle-même référence à une autre bibliothèque de types, le compilateur peut effectuer une opération #import implicite pour l'autre bibliothèque de types.|
|[embedded_idl](../preprocessor/embedded-idl.md)|Indique que la bibliothèque de types est écrite dans le fichier .tlh et que le code généré par attributs est conservé.|
|[exclus](../preprocessor/exclude-hash-import.md)|Exclut des éléments des fichiers d'en-tête de bibliothèque de types en cours de création.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|Spécifie un préfixe à utiliser pour nommer les propriétés et les méthodes de haut niveau.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|Spécifie d'autres préfixes pour trois méthodes de propriété.|
|[implementation_only](../preprocessor/implementation-only.md)|Supprime la génération du fichier d'en-tête .tlh (fichier d'en-tête principal).|
|[include ()](../preprocessor/include-parens.md)|Désactive l'exclusion automatique.|
|[inject_statement](../preprocessor/inject-statement.md)|Insère son argument en tant que texte source dans l’en-tête de bibliothèque de types.|
|[named_guids](../preprocessor/named-guids.md)|Indique au compilateur de définir et d’initialiser les variables GUID dans l’ancien style, sous la forme `LIBID_MyLib` ,, `CLSID_MyCoClass` `IID_MyInterface` et `DIID_MyDispInterface` .|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|Désactive l'exclusion automatique.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|Modifie la façon dont le compilateur génère des fonctions wrapper pour les méthodes d'interface double.|
|[no_implementation](../preprocessor/no-implementation.md)|Supprime la génération de l'en-tête .tli, qui contient les implémentations des fonctions membres de wrapper.|
|[no_namespace](../preprocessor/no-namespace.md)|Indique que le nom de l'espace de noms n'est pas généré par le compilateur.|
|[no_registry](../preprocessor/no-registry.md)|Indique au compilateur de ne pas rechercher de bibliothèques de types dans le Registre.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|A les mêmes fonctionnalités que l’attribut [no_namespace](../preprocessor/no-namespace.md) , mais est utilisé sur les bibliothèques de types que vous utilisez la directive #import avec l’attribut [auto_search](../preprocessor/auto-search.md) .|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|Supprime la création des pointeurs intelligents pour toutes les interfaces dans la bibliothèque de types.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|Indique au compilateur de générer des fonctions wrapper de bas niveau pour les méthodes et les propriétés dispinterface qui appellent `IDispatch::Invoke` et retournent le code d’erreur HRESULT.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|Supprime la génération des fonctions wrapper de gestion des erreurs et des déclarations de [propriété](../cpp/property-cpp.md) qui utilisent ces fonctions wrapper.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|Spécifie un préfixe différent pour éviter les collisions de noms.|
|[raw_native_types](../preprocessor/raw-native-types.md)|Désactive l'utilisation des classes de prise en charge COM dans les fonctions wrapper de haut niveau et force l'utilisation de types de données de bas niveau à la place.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|Spécifie d'autres préfixes pour trois méthodes de propriété.|
|[rename](../preprocessor/rename-hash-import.md)|Offre une solution de contournement pour les problèmes de collisions de noms.|
|[rename_namespace](../preprocessor/rename-namespace.md)|Renomme l'espace de noms qui contient le contenu de la bibliothèque de types.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|A les mêmes fonctionnalités que l’attribut [rename_namespace](../preprocessor/rename-namespace.md) , mais est utilisé sur les bibliothèques de types que vous utilisez la directive #import avec l’attribut [auto_search](../preprocessor/auto-search.md) .|
|[tlbid](../preprocessor/tlbid.md)|Permet de charger des bibliothèques autres que la bibliothèque de types principale.|

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[#import directive](../preprocessor/hash-import-directive-cpp.md)
