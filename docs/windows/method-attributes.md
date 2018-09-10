---
title: Attributs de méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 27540db2da7aecbe7a4b70b786bbf05bf608e889
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317431"
---
# <a name="method-attributes"></a>Attributs de méthode

Les attributs suivants s’appliquent aux méthodes dans une classe, une coclasse ou une interface.

|Attribut|Description|
|---------------|-----------------|
|[bindable](../windows/bindable.md)|Indique que la propriété prend en charge la liaison de données.|
|[call_as](../windows/call-as.md)|Permet à une fonction non accessibles à distance à mapper à une fonction à distance.|
|[custom](../windows/custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_column](../windows/db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](../windows/db-command.md)|Crée une commande OLE DB.|
|[db_param](../windows/db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](../windows/db-source.md)|Crée une connexion à une source de données.|
|[db_table](../windows/db-table.md)|Ouvre une table OLE DB.|
|[defaultbind](../windows/defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|
|[defaultcollelem](../windows/defaultcollelem.md)|Utilisé pour l’optimisation du code Visual Basic.|
|[displaybind](../windows/displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[helpcontext](../windows/helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le **aide** fichier.|
|[helpfile](../windows/helpfile.md)|Définit le nom de la **aide** fichier pour une bibliothèque de types.|
|[helpstring](../windows/helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[helpstringcontext](../windows/helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstringdll](../windows/helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|
|[hidden](../windows/hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[ID](../windows/id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).|
|[immediatebind](../windows/immediatebind.md)|Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.|
|[in](../windows/in-cpp.md)|Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.|
|[local](../windows/local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.|
|[nonbrowsable](../windows/nonbrowsable.md)|Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.|
|[propget](../windows/propget.md)|Spécifie une fonction d’accesseur de propriété.|
|[propput](../windows/propput.md)|Spécifie une fonction de définition de propriété.|
|[propputref](../windows/propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence plutôt qu’une valeur.|
|[ptr](../windows/ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[range](../windows/range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[requestedit](../windows/requestedit.md)|Indique que la propriété prend en charge la `OnRequestEdit` notification.|
|[restricted](../windows/restricted.md)|Spécifie qu’un membre d’un module, une interface ou une dispinterface ne peut pas être appelé arbitrairement.|
|[satype](../windows/satype.md)|Spécifie le type de données de la `SAFEARRAY` structure.|
|[source](../windows/source-cpp.md)|Spécifie les interfaces de source du contrôle des points de connexion sur une classe. Sur une propriété ou méthode, le `source` attribut indique que le membre retourne un objet ou un VARIANT et qui est une source d’événements.|
|[synchronize](../windows/synchronize.md)|Synchronise l’accès à la méthode cible.|
|[vararg](../windows/vararg.md)|Spécifie que la fonction accepte un nombre variable d’arguments.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](../windows/attributes-by-usage.md)