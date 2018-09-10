---
title: Classe d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60243373ea6b34ebceffd6f1ae21723e71e11bbb
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313596"
---
# <a name="class-attributes"></a>Attributs de classe

Les attributs suivants s’appliquent à la [classe](../cpp/class-cpp.md) mot clé C++.

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|Indique que la classe prend en charge l’agrégation.|
|[aggregates](../windows/aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](../windows/appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application .exe complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[case](../windows/case-cpp.md)|Utilisé avec le [switch_type](../windows/switch-type.md) attribut dans une union.|
|[coclass](../windows/coclass.md)|Crée un contrôle ActiveX.|
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[control](../windows/control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_command](../windows/db-command.md)|Crée une commande OLE DB.|
|[db_param](../windows/db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](../windows/db-source.md)|Crée une connexion à une source de données.|
|[db_table](../windows/db-table.md)|Ouvre une table OLE DB.|
|[default](../windows/default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](../windows/defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|
|[event_receiver](../windows/event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](../windows/event-source.md)|Crée une source d'événement.|
|[helpcontext](../windows/helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le **aide** fichier.|
|[helpfile](../windows/helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstringcontext](../windows/helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstring](../windows/helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[hidden](../windows/hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[Implémente](../windows/implements-cpp.md)|Spécifie les interfaces de dispatch obligés d’être membres de la coclasse IDL.|
|[implements_category](../windows/implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[module](../windows/module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[noncreatable](../windows/noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|
|[progid](../windows/progid.md)|Définit le ProgID pour un contrôle.|
|[registration_script](../windows/registration-script.md)|Exécute le script d’inscription spécifiée.|
|[requestedit](../windows/requestedit.md)|Indique que la propriété prend en charge la `OnRequestEdit` notification.|
|[source](../windows/source-cpp.md)|Spécifie les interfaces de source du contrôle des points de connexion sur une classe. Sur une propriété ou méthode, le `source` attribut indique que le membre retourne un objet ou `VARIANT` qui est une source d’événements.|
|[support_error_info](../windows/support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|
|[Threading](../windows/threading-cpp.md)|Spécifie le modèle de thread pour un contrôle.|
|[uuid](../windows/uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[version](../windows/version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une classe.|
|[vi_progid](../windows/vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](../windows/attributes-by-usage.md)