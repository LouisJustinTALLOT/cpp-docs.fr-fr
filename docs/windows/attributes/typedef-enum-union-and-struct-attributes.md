---
title: TypeDef, Enum, Union et Struct (attributs) (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 2b56ada13a0c597866d538991ed1e83078924ac9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029581"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Attributs Typedef, Enum, Union et Struct

Les attributs suivants s’appliquent à la [typedef](../../cpp/aliases-and-typedefs-cpp.md), [struct](../../cpp/struct-cpp.md), et [enum](../../cpp/enumerations-cpp.md) mots clés C++.

### <a name="typedef"></a>typedef

|Attribut|Description|
|---------------|-----------------|
|[casse](case-cpp.md)|Utilisé avec le [switch_type](switch-type.md) d’attribut dans un **union**.|
|[personnalisé](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[exporter](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[public](public-cpp-attributes.md)|Garantit qu’un typedef passera à la bibliothèque de types même s’il n’est pas référencé à partir du fichier .idl.|
|[ref](ref-cpp.md)|Identifie un pointeur de référence.|
|[switch_is](switch-is.md)|Spécifie l’expression ou l’identificateur agissant comme l’union discriminante qui sélectionne le membre d’union.|
|[switch_type](switch-type.md)|Identifie le type de la variable utilisée en tant que l’union discriminante.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[wire_marshal](wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifiques à l’application.|

### <a name="enum"></a>enum

|Attribut|Description|
|---------------|-----------------|
|[personnalisé](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[exporter](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[v1_enum](v1-enum.md)|Indique que le type énuméré spécifié être transmises comme une entité de 32 bits, plutôt que la valeur par défaut de 16 bits.|

### <a name="union"></a>union

|Attribut|Description|
|---------------|-----------------|
|[personnalisé](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[exporter](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
|[max_is](max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|
|[size_is](size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|

### <a name="nonencapsulated-union"></a>Union nonencapsulated

|Attribut|Description|
|---------------|-----------------|
|[ms_union](ms-union.md)|Contrôle l’alignement de représentation sous forme de données de réseau d’unions nonencapsulated.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|

### <a name="struct"></a>struct

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique que la classe prend en charge l’agrégation.|
|[agrégats](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application .exe complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[coclasse](coclass.md)|Crée un contrôle ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[contrôle](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[personnalisé](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[default](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[exporter](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[hidden](hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[implements_category](implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
|[max_is](max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|
|[requires_category](requires-category.md)|Spécifie les catégories de composant requis de la classe cible.|
|[size_is](size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[source](source-cpp.md)|Sur une classe, spécifie les interfaces de source de l’objet COM pour les points de connexion. Sur une propriété ou une méthode, indique que le membre retourne un objet ou un VARIANT et qui est une source d’événements.|
|[threads](threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[version](version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une classe.|
|[vi_progid](vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)