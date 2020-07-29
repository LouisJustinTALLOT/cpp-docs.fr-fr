---
title: Attributs typedef, enum, Union et struct (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 5e9eccd5e4464e92757d6dd78dd0f5187372ea3e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222106"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Attributs Typedef, Enum, Union et Struct

Les attributs suivants s’appliquent aux mots clés [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md)et [enum](../../cpp/enumerations-cpp.md) C++.

### <a name="typedef"></a>typedef

|Attribut|Description|
|---------------|-----------------|
|[études](case-cpp.md)|Utilisé avec l’attribut [switch_type](switch-type.md) dans un **`union`** .|
|[propre](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[exporter](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau à transmettre.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide d’une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[public](public-cpp-attributes.md)|Garantit qu’un typedef sera placé dans la bibliothèque de types, même s’il n’est pas référencé dans le fichier. idl.|
|[ref](ref-cpp.md)|Identifie un pointeur de référence.|
|[switch_is](switch-is.md)|Spécifie l’expression ou l’identificateur agissant comme le discriminante d’Union qui sélectionne le membre Union.|
|[switch_type](switch-type.md)|Identifie le type de la variable utilisée en tant qu’Union discriminante.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[wire_marshal](wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifique à l’application.|

### <a name="enum"></a>enum

|Attribut|Description|
|---------------|-----------------|
|[propre](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[exporter](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique d’une classe ou d’une interface.|
|[v1_enum](v1-enum.md)|Indique que le type énuméré spécifié doit être transmis en tant qu’entité 32 bits, au lieu de la valeur par défaut 16 bits.|

### <a name="union"></a>union

|Attribut|Description|
|---------------|-----------------|
|[propre](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[exporter](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau à transmettre.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau à transmettre.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau à transmettre.|
|[max_is](max-is.md)|Désigne la valeur maximale d’un index de tableau valide.|
|[size_is](size-is.md)|Spécifie la taille de la mémoire allouée aux pointeurs dimensionnés, aux pointeurs dimensionnés aux pointeurs dimensionnés et aux tableaux à une ou plusieurs dimensions.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique d’une classe ou d’une interface.|

### <a name="nonencapsulated-union"></a>Union qui n’est pas encapsulée

|Attribut|Description|
|---------------|-----------------|
|[ms_union](ms-union.md)|Contrôle l’alignement de la représentation des données réseau des unions qui ne sont pas encapsulées.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.|

### <a name="struct"></a>struct

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique que la classe prend en charge l’agrégation.|
|[agrégats](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](appobject.md)|Identifie la coclasse sous la forme d’un objet d’application, qui est associé à une application. exe complète, et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[coclasse](coclass.md)|Crée un contrôle ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Ajoute une entrée d’interface à une table COM.|
|[control](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[propre](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifiée à un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[valeurs](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](defaultvtable.md)|Définit une interface comme interface vtable par défaut pour un contrôle.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[exporter](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau à transmettre.|
|[masquer](hidden.md)|Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[implements_category](implements-category.md)|Spécifie les catégories de composant implémentées pour la classe.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau à transmettre.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau à transmettre.|
|[max_is](max-is.md)|Désigne la valeur maximale d’un index de tableau valide.|
|[requires_category](requires-category.md)|Spécifie les catégories de composants nécessaires de la classe cible.|
|[size_is](size-is.md)|Spécifie la taille de la mémoire allouée aux pointeurs dimensionnés, aux pointeurs dimensionnés aux pointeurs dimensionnés et aux tableaux à une ou plusieurs dimensions.|
|[source](source-cpp.md)|Sur une classe, spécifie les interfaces sources de l’objet COM pour les points de connexion. Sur une propriété ou une méthode, indique que le membre retourne un objet ou une variante qui est une source d’événements.|
|[Threading](threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique d’une classe ou d’une interface.|
|[version](version-cpp.md)|Identifie une version particulière parmi plusieurs versions d’une classe.|
|[vi_progid](vi-progid.md)|Spécifie une forme indépendante de la version du ProgID.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)
