---
title: Attributs de classe C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: bdc689107eb973b9701e3f1fbe37a10aa6ae8d85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448865"
---
# <a name="class-attributes"></a>Attributs de classe

Les attributs suivants s’appliquent à la [classe](../../cpp/class-cpp.md) mot clé C++.

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique que la classe prend en charge l’agrégation.|
|[aggregates](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application .exe complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[case](case-cpp.md)|Utilisé avec le [switch_type](switch-type.md) attribut dans une union.|
|[coclasse](coclass.md)|Crée un contrôle ActiveX.|
|[com_interface_entry](com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[control](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[custom](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[default](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le **aide** fichier.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[hidden](hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[implements](implements-cpp.md)|Spécifie les interfaces de dispatch obligés d’être membres de la coclasse IDL.|
|[implements_category](implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[module](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[noncreatable](noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|
|[progid](progid.md)|Définit le ProgID pour un contrôle.|
|[registration_script](registration-script.md)|Exécute le script d’inscription spécifiée.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la `OnRequestEdit` notification.|
|[source](source-cpp.md)|Spécifie les interfaces de source du contrôle des points de connexion sur une classe. Sur une propriété ou méthode, le `source` attribut indique que le membre retourne un objet ou `VARIANT` qui est une source d’événements.|
|[support_error_info](support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|
|[threading](threading-cpp.md)|Spécifie le modèle de thread pour un contrôle.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[version](version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une classe.|
|[vi_progid](vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)