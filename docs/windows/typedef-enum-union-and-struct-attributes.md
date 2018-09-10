---
title: TypeDef, Enum, Union et Struct (attributs) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74e9bbf3ad593f5ce1e6d1868d8e1a09b0bd885e
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314597"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Attributs Typedef, Enum, Union et Struct

Les attributs suivants s’appliquent à la [typedef](../cpp/aliases-and-typedefs-cpp.md), [struct](../cpp/struct-cpp.md), et [enum](../cpp/enumerations-cpp.md) mots clés C++.

### <a name="typedef"></a>typedef

|Attribut|Description|
|---------------|-----------------|
|[case](../windows/case-cpp.md)|Utilisé avec le [switch_type](../windows/switch-type.md) d’attribut dans un **union**.|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[export](../windows/export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](../windows/first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[helpcontext](../windows/helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](../windows/helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstring](../windows/helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[library_block](../windows/library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[ptr](../windows/ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[public](../windows/public-cpp-attributes.md)|Garantit qu’un typedef passera à la bibliothèque de types même s’il n’est pas référencé à partir du fichier .idl.|
|[ref](../windows/ref-cpp.md)|Identifie un pointeur de référence.|
|[switch_is](../windows/switch-is.md)|Spécifie l’expression ou l’identificateur agissant comme l’union discriminante qui sélectionne le membre d’union.|
|[switch_type](../windows/switch-type.md)|Identifie le type de la variable utilisée en tant que l’union discriminante.|
|[unique](../windows/unique-cpp.md)|Spécifie un pointeur unique.|
|[wire_marshal](../windows/wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifiques à l’application.|

### <a name="enum"></a>enum

|Attribut|Description|
|---------------|-----------------|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[export](../windows/export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[uuid](../windows/uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[v1_enum](../windows/v1-enum.md)|Indique que le type énuméré spécifié être transmises comme une entité de 32 bits, plutôt que la valeur par défaut de 16 bits.|

### <a name="union"></a>union

|Attribut|Description|
|---------------|-----------------|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[export](../windows/export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](../windows/first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[last_is](../windows/last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[length_is](../windows/length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
|[max_is](../windows/max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|
|[size_is](../windows/size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[unique](../windows/unique-cpp.md)|Spécifie un pointeur unique.|
|[uuid](../windows/uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|

### <a name="nonencapsulated-union"></a>Union nonencapsulated

|Attribut|Description|
|---------------|-----------------|
|[ms_union](../windows/ms-union.md)|Contrôle l’alignement de représentation sous forme de données de réseau d’unions nonencapsulated.|
|[no_injected_text](../windows/no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|

### <a name="struct"></a>struct

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Indique que la classe prend en charge l’agrégation.|
|[aggregates](../windows/aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](../windows/appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application .exe complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[coclass](../windows/coclass.md)|Crée un contrôle ActiveX.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[control](../windows/control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_column](../windows/db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](../windows/db-command.md)|Crée une commande OLE DB.|
|[db_param](../windows/db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](../windows/db-source.md)|Crée une connexion à une source de données.|
|[db_table](../windows/db-table.md)|Ouvre une table OLE DB.|
|[default](../windows/default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](../windows/defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|
|[event_receiver](../windows/event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](../windows/event-source.md)|Crée une source d'événement.|
|[export](../windows/export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](../windows/first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[hidden](../windows/hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[implements_category](../windows/implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[last_is](../windows/last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[length_is](../windows/length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
|[max_is](../windows/max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|
|[requires_category](../windows/requires-category.md)|Spécifie les catégories de composant requis de la classe cible.|
|[size_is](../windows/size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[source](../windows/source-cpp.md)|Sur une classe, spécifie les interfaces de source de l’objet COM pour les points de connexion. Sur une propriété ou une méthode, indique que le membre retourne un objet ou un VARIANT et qui est une source d’événements.|
|[Threading](../windows/threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[unique](../windows/unique-cpp.md)|Spécifie un pointeur unique.|
|[uuid](../windows/uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[version](../windows/version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une classe.|
|[vi_progid](../windows/vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](../windows/attributes-by-usage.md)