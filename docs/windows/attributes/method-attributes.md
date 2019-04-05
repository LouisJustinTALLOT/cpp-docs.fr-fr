---
title: Attributs de méthode (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: aa67d45dfc0fadd300caeaaeb8a7c25bb1c38bcb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023566"
---
# <a name="method-attributes"></a>Attributs de méthode

Les attributs suivants s’appliquent aux méthodes dans une classe, une coclasse ou une interface.

|Attribut|Description|
|---------------|-----------------|
|[bindable](bindable.md)|Indique que la propriété prend en charge la liaison de données.|
|[call_as](call-as.md)|Permet à une fonction non accessibles à distance à mapper à une fonction à distance.|
|[personnalisé](custom-cpp.md)|Vous permet de définir votre propre attribut.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Crée une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie et délimite la variable.|
|[db_source](db-source.md)|Crée une connexion à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[defaultbind](defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|
|[defaultcollelem](defaultcollelem.md)|Utilisé pour l’optimisation du code Visual Basic.|
|[displaybind](displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le **aide** fichier.|
|[helpfile](helpfile.md)|Définit le nom de la **aide** fichier pour une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|
|[hidden](hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[ID](id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).|
|[immediatebind](immediatebind.md)|Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.|
|[dans](in-cpp.md)|Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.|
|[locaux](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.|
|[nonbrowsable](nonbrowsable.md)|Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.|
|[propget](propget.md)|Spécifie une fonction d’accesseur de propriété.|
|[propput](propput.md)|Spécifie une fonction de définition de propriété.|
|[propputref](propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence plutôt qu’une valeur.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la notification `OnRequestEdit`.|
|[restricted](restricted.md)|Spécifie qu’un membre d’un module, une interface ou une dispinterface ne peut pas être appelé arbitrairement.|
|[satype](satype.md)|Spécifie le type de données de la `SAFEARRAY` structure.|
|[source](source-cpp.md)|Spécifie les interfaces de source du contrôle des points de connexion sur une classe. Sur une propriété ou méthode, le `source` attribut indique que le membre retourne un objet ou un VARIANT et qui est une source d’événements.|
|[synchronize](synchronize.md)|Synchronise l’accès à la méthode cible.|
|[vararg](vararg.md)|Spécifie que la fonction accepte un nombre variable d’arguments.|

## <a name="see-also"></a>Voir aussi

[Attributs par utilisation](attributes-by-usage.md)