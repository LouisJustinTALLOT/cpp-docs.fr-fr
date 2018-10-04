---
title: Référence alphabétique des attributs | Microsoft Docs
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.attributes
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0b305e928fec58833c4aac3f5625783aa2cb9ef
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791025"
---
# <a name="attributes-alphabetical-reference"></a>Référence alphabétique des attributs

Les attributs suivants sont disponibles dans Visual C++.

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|
|[aggregates](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application EXE complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[async_uuid](async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL pour définir des versions synchrones et asynchrones d’une interface COM.|
|[attribute](attribute.md)|Vous permet de créer un attribut personnalisé.|
|[bindable](bindable.md)|Indique que la propriété prend en charge la liaison de données.|
|[call_as](call-as.md)|Permet à une fonction non accessibles à distance à mapper à une fonction à distance.|
|[case](case-cpp.md)|Utilisé avec le [switch_type](switch-type.md) attribut dans une union.|
|[coclass](coclass.md)|Crée un objet COM, ce qui peut implémenter une interface COM.|
|[COM_INTERFACE_ENTRY](com-interface-entry-cpp.md)|Ajoute une entrée de l’interface à un mappage COM.|
|[control](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[cpp_quote](cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier d’en-tête généré.|
|[custom](custom-cpp.md)|Vous permet de définir vos propres attributs.|
|[db_accessor](db-accessor.md)|Lie les colonnes dans un ensemble de lignes et les lie aux mappages d’accesseur correspondant.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Exécute une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable de membre spécifié avec un paramètre d’entrée ou de sortie.|
|[db_source](db-source.md)|Crée et encapsule une connexion, via un fournisseur, à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[default](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultbind](defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|
|[defaultcollelem](defaultcollelem.md)|Utilisé pour l’optimisation du code Visual Basic.|
|[defaultvalue](defaultvalue.md)|Permet de spécifier une valeur par défaut pour un paramètre facultatif typé.|
|[defaultvtable](defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|
|[dispinterface](dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|
|[displaybind](displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[dual](dual.md)|Place une interface dans le fichier .idl comme une interface double.|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivantes seront traitées et placés dans le fichier .idl généré.|
|[entry](entry.md)|Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[export](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|
|[hidden](hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[ID](id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).|
|[idl_module](idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](idl-quote.md)|Vous permet d’utiliser des attributs ou IDL construit qui ne sont pas pris en charge dans la version actuelle de Visual C++.|
|[iid_is](iid-is.md)|Spécifie l’IID de l’interface COM vers laquelle pointé un pointeur d’interface.|
|[immediatebind](immediatebind.md)|Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.|
|[Implémente](implements-cpp.md)|Spécifie les interfaces de dispatch obligés d’être membres de la coclasse IDL.|
|[implements_category](implements-category.md)|Spécifie les catégories de composants implémentés pour la classe.|
|[import](import.md)|Spécifie un autre fichier .idl, .odl ou en-tête contenant les définitions que vous souhaitez référencer à partir de votre fichier .idl principal.|
|[importidl](importidl.md)|Insère le fichier .idl spécifié dans le fichier .idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[in](in-cpp.md)|Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.|
|[include](include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.|
|[includelib](includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[lcid](lcid.md)|Vous permet de passer un identificateur de paramètres régionaux à une fonction.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[licensed](licensed.md)|Indique que la coclasse auquel il s’applique est concédé sous licence et doit être instanciée à l’aide de `IClassFactory2`.|
|[local](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.|
|[max_is](max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|
|[module](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[ms_union](ms-union.md)|Contrôle l’alignement de représentation sous forme de données de réseau d’unions nonencapsulated.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|
|[nonbrowsable](nonbrowsable.md)|Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.|
|[noncreatable](noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|
|[nonextensible](nonextensible.md)|Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peut pas être étendus avec des membres supplémentaires en cours d’exécution.|
|[object](object-cpp.md)|Identifie une interface personnalisée ; synonyme d’attribut personnalisé.|
|[odl](odl.md)|Identifie une interface en tant qu’objet Description Language (ODL) interface.|
|[oleautomation](oleautomation.md)|Indique qu’une interface est compatible avec Automation.|
|[Facultatif](optional-cpp.md)|Spécifie un paramètre facultatif pour une fonction membre.|
|[out](out-cpp.md)|Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).|
|[pointer_default](pointer-default.md)|Spécifie l’attribut de pointeur par défaut pour tous les pointeurs à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.|
|[pragma](pragma.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier .idl généré.|
|[progid](progid.md)|Spécifie le ProgID pour un objet COM.|
|[propget](propget.md)|Spécifie une fonction d’accesseur (get) de propriété.|
|[propput](propput.md)|Spécifie une fonction de définition de propriété.|
|[propputref](propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence plutôt qu’une valeur.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[public](public-cpp-attributes.md)|Garantit qu’un typedef passera à la bibliothèque de types même s’il n’est pas référencé à partir du fichier .idl.|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[rdx](rdx.md)|Crée ou modifie une clé de Registre.|
|[readonly](readonly-cpp.md)|Interdit l’assignation à une variable.|
|[ref](ref-cpp.md)|Identifie un pointeur de référence.|
|[registration_script](registration-script.md)|Exécute le script d’inscription spécifiée.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la `OnRequestEdit` notification.|
|[requires_category](requires-category.md)|Spécifie les catégories de composants requis pour la classe.|
|[restricted](restricted.md)|Spécifie qu’une bibliothèque ou un membre d’un module, une interface ou une dispinterface ne peut pas être appelée arbitrairement.|
|[retval](retval.md)|Désigne le paramètre qui reçoit la valeur de retour du membre.|
|[satype](satype.md)|Spécifie le type de données de la `SAFEARRAY`.|
|[size_is](size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[source](source-cpp.md)|Indique qu’un membre d’une classe, une propriété ou une méthode est une source d’événements.|
|[string](string-cpp.md)|Indique qu’unidimensionnel **char**, **wchar_t**, `byte`, ou tableau équivalent ou le pointeur vers ce type de tableau doit être traité comme une chaîne.|
|[support_error_info](support-error-info.md)|Prend en charge les rapports d’erreurs pour l’objet cible.|
|[switch_is](switch-is.md)|Spécifie l’expression ou l’identificateur agissant comme l’union discriminante qui sélectionne le membre d’union.|
|[switch_type](switch-type.md)|Identifie le type de la variable utilisée en tant que l’union discriminante.|
|[synchronize](synchronize.md)|Synchronise l’accès à une méthode.|
|[Threading](threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[transmit_as](transmit-as.md)|Indique au compilateur d’associer un type présenté, les applications clientes et serveur manipulent, à un type transmis.|
|[uidefault](uidefault.md)|Indique que le membre d’informations de type est le membre par défaut pour l’affichage dans l’interface utilisateur.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[usesgetlasterror](usesgetlasterror.md)|Indique à l’appelant que s’il existe une erreur lors de l’appel de cette fonction, l’appelant peut ensuite appeler `GetLastError` pour récupérer le code d’erreur.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[v1_enum](v1-enum.md)|Indique que le type énuméré spécifié être transmises comme une entité de 32 bits, plutôt que la valeur par défaut de 16 bits.|
|[vararg](vararg.md)|Spécifie que la fonction accepte un nombre variable d’arguments.|
|[version](version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une interface ou une classe.|
|[vi_progid](vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|
|[wire_marshal](wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifiques à l’application.|

## <a name="see-also"></a>Voir aussi

[Attributs de C++ pour COM et .NET](cpp-attributes-com-net.md)<br/>
[Attributs par groupe](attributes-by-group.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)