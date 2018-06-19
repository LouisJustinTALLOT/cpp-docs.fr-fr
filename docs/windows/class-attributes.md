---
title: Attributs de classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a932fdb1ef1d9e2af2acace901feaa95b6216d1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861439"
---
# <a name="class-attributes"></a>Attributs de classe
Les attributs suivants s’appliquent à la [classe](../cpp/class-cpp.md) mot clé C++.  
  
|Attribut|Description|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Indique que la classe prend en charge l’agrégation.|  
|[aggregates](../windows/aggregates.md)|Indique qu’un contrôle agrège la classe cible.|  
|[appobject](../windows/appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application .exe complet et indique que les fonctions et les propriétés de la coclasse sont disponibles dans cette bibliothèque de types.|  
|[case](../windows/case-cpp.md)|Utilisé avec le [switch_type](../windows/switch-type.md) attribut dans une union.|  
|[coclass](../windows/coclass.md)|Crée un contrôle ActiveX.|  
|[COM_INTERFACE_ENTRY](../windows/com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|  
|[control](../windows/control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|  
|[custom](../windows/custom-cpp.md)|Permet de définir votre propre attribut.|  
|[db_command](../windows/db-command.md)|Crée une commande OLE DB.|  
|[db_param](../windows/db-param.md)|Associe la variable membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|  
|[db_source](../windows/db-source.md)|Crée une connexion à une source de données.|  
|[db_table](../windows/db-table.md)|Ouvre une table OLE DB.|  
|[default](../windows/default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|  
|[defaultvtable](../windows/defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|  
|[event_receiver](../windows/event-receiver.md)|Crée un récepteur d’événements.|  
|[event_source](../windows/event-source.md)|Crée une source d'événement.|  
|[helpcontext](../windows/helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|  
|[helpfile](../windows/helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|  
|[helpstring](../windows/helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|  
|[hidden](../windows/hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|  
|[Implémente](../windows/implements-cpp.md)|Spécifie les interfaces de dispatch qui doivent être membres de la coclasse IDL.|  
|[implements_category](../windows/implements-category.md)|Spécifie les catégories de composants de mise en œuvre de la classe.|  
|[Module](../windows/module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|  
|[noncreatable](../windows/noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|  
|[progid](../windows/progid.md)|Définit le ProgID pour un contrôle.|  
|[registration_script](../windows/registration-script.md)|Exécute le script d’enregistrement spécifié.|  
|[requestedit](../windows/requestedit.md)|Indique que la propriété prend en charge la **OnRequestEdit** notification.|  
|[Source](../windows/source-cpp.md)|Spécifie les interfaces de source du contrôle des points de connexion sur une classe. Sur une propriété ou une méthode, le **source** attribut indique que le membre retourne un objet ou un VARIANT et qui est une source d’événements.|  
|[support_error_info](../windows/support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|  
|[Modèle de thread](../windows/threading-cpp.md)|Spécifie le modèle de thread pour un contrôle.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|  
|[version](../windows/version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une classe.|  
|[vi_progid](../windows/vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs par utilisation](../windows/attributes-by-usage.md)