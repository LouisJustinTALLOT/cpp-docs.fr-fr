---
description: 'En savoir plus sur : attributs de classe'
title: Attributs de classe (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: ea929ed7f5fac949393e6d3cf2b24195babfeea7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247382"
---
# <a name="class-attributes"></a>Attributs de classe

Les attributs suivants s’appliquent au mot clé C++ de [classe](../../cpp/class-cpp.md) .

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique que la classe prend en charge l’agrégation.|
|[agrégats](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](appobject.md)|Identifie la coclasse sous la forme d’un objet d’application, qui est associé à une application. exe complète, et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[case](case-cpp.md)|Utilisé avec l’attribut [switch_type](switch-type.md) dans une Union.|
|[coclasse](coclass.md)|Crée un contrôle ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Ajoute une entrée d’interface à une table COM.|
|[control](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[propre](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifiée à un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[default](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](defaultvtable.md)|Définit une interface comme interface vtable par défaut pour un contrôle.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier **d’aide** .|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide d’une bibliothèque de types.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier. hlp ou. chm.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[masquer](hidden.md)|Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[implémente](implements-cpp.md)|Spécifie les interfaces de dispatch qui sont forcées à être membres de la coclasse IDL.|
|[implements_category](implements-category.md)|Spécifie les catégories de composant implémentées pour la classe.|
|[modules](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[noncreatable](noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|
|[ProgID](progid.md)|Définit le ProgID pour un contrôle.|
|[registration_script](registration-script.md)|Exécute le script d’inscription spécifié.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la notification `OnRequestEdit`.|
|[source](source-cpp.md)|Spécifie les interfaces sources du contrôle pour les points de connexion sur une classe. Sur une propriété ou une méthode, l' `source` attribut indique que le membre retourne un objet ou `VARIANT` qui est une source d’événements.|
|[support_error_info](support-error-info.md)|Prend en charge la création de rapports d’erreurs pour l’objet cible.|
|[Threading](threading-cpp.md)|Spécifie le modèle de thread pour un contrôle.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique d’une classe ou d’une interface.|
|[version](version-cpp.md)|Identifie une version particulière parmi plusieurs versions d’une classe.|
|[vi_progid](vi-progid.md)|Spécifie une forme indépendante de la version du ProgID.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)
