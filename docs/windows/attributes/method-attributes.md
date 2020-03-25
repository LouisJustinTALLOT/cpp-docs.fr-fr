---
title: Attributs de méthodeC++ (com)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: c9823869be96f53a3c4fbc36c7b56e1bea0a1303
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166768"
---
# <a name="method-attributes"></a>Attributs de méthode

Les attributs suivants s’appliquent aux méthodes dans une classe, une coclasse ou une interface.

|Attribut|Description|
|---------------|-----------------|
|[bindable](bindable.md)|Indique que la propriété prend en charge la liaison de données.|
|[call_as](call-as.md)|Permet à une fonction non accessible à distance d’être mappée à une fonction distante.|
|[custom](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifiée à un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[defaultbind](defaultbind.md)|Indique la propriété unique pouvant être liée qui représente le mieux l’objet.|
|[defaultcollelem](defaultcollelem.md)|Utilisé pour Visual Basic optimisation du code.|
|[displaybind](displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier **d’aide** .|
|[helpfile](helpfile.md)|Définit le nom du fichier d' **aide** d’une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier. hlp ou. chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer une recherche de chaîne de document (localisation).|
|[hidden](hidden.md)|Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[id](id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou une dispinterface).|
|[immediatebind](immediatebind.md)|Indique que la base de données sera immédiatement notifiée de toutes les modifications apportées à la propriété d’un objet lié aux données.|
|[in](in-cpp.md)|Indique qu’un paramètre doit être passé de la procédure appelante à la procédure appelée.|
|[local](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme générateur d’en-tête lorsqu’il est utilisé dans l’en-tête d’interface. En cas d’utilisation dans une fonction individuelle, désigne une procédure locale pour laquelle aucun stub n’est généré.|
|[nonbrowsable](nonbrowsable.md)|Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.|
|[propget](propget.md)|Spécifie une fonction d’accesseur de propriété.|
|[propput](propput.md)|Spécifie une fonction de définition de propriété.|
|[propputref](propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence au lieu d’une valeur.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la notification `OnRequestEdit`.|
|[restricted](restricted.md)|Spécifie qu’un membre d’un module, d’une interface ou d’une dispinterface ne peut pas être appelé arbitrairement.|
|[satype](satype.md)|Spécifie le type de données de la structure `SAFEARRAY`.|
|[source](source-cpp.md)|Spécifie les interfaces sources du contrôle pour les points de connexion sur une classe. Sur une propriété ou une méthode, l’attribut `source` indique que le membre retourne un objet ou une variante qui est une source d’événements.|
|[synchronize](synchronize.md)|Synchronise l’accès à la méthode cible.|
|[vararg](vararg.md)|Spécifie que la fonction prend un nombre variable d’arguments.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)
