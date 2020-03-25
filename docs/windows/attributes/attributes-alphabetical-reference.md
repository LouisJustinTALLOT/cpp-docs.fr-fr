---
title: Référence alphabétique des attributs
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: dbbb406765c0664f2cd332524a61713f9c67cf9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167509"
---
# <a name="attributes-alphabetical-reference"></a>Référence alphabétique des attributs

Les attributs suivants sont disponibles dans le compilateur C++ Microsoft :

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|
|[aggregates](aggregates.md)|Indique qu’un contrôle agrège la classe cible.|
|[appobject](appobject.md)|Identifie la coclasse sous la forme d’un objet d’application, qui est associé à une application EXE complète, et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[async_uuid](async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL de définir à la fois les versions synchrones et asynchrones d’une interface COM.|
|[attribute](attribute.md)|Vous permet de créer un attribut personnalisé.|
|[bindable](bindable.md)|Indique que la propriété prend en charge la liaison de données.|
|[call_as](call-as.md)|Permet à une fonction non accessible à distance d’être mappée à une fonction distante.|
|[case](case-cpp.md)|Utilisé avec l’attribut [switch_type](switch-type.md) dans une Union.|
|[coclasse](coclass.md)|Crée un objet COM, qui peut implémenter une interface COM.|
|[com_interface_entry](com-interface-entry-cpp.md)|Ajoute une entrée d’interface à une table COM.|
|[control](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[cpp_quote](cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemets, dans le fichier d’en-tête généré.|
|[custom](custom-cpp.md)|Vous permet de définir vos propres attributs.|
|[db_accessor](db-accessor.md)|Lie les colonnes d’un ensemble de lignes et les lie aux mappages d’accesseur correspondants.|
|[db_column](db-column.md)|Lie une colonne spécifiée à l’ensemble de lignes.|
|[db_command](db-command.md)|Exécute une commande OLE DB.|
|[db_param](db-param.md)|Associe la variable membre spécifiée à un paramètre d’entrée ou de sortie.|
|[db_source](db-source.md)|Crée et encapsule une connexion, via un fournisseur, à une source de données.|
|[db_table](db-table.md)|Ouvre une table OLE DB.|
|[default](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultbind](defaultbind.md)|Indique la propriété unique pouvant être liée qui représente le mieux l’objet.|
|[defaultcollelem](defaultcollelem.md)|Utilisé pour Visual Basic optimisation du code.|
|[defaultvalue](defaultvalue.md)|Autorise la spécification d’une valeur par défaut pour un paramètre facultatif typé.|
|[defaultvtable](defaultvtable.md)|Définit une interface comme interface vtable par défaut pour un contrôle.|
|[dispinterface](dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|
|[displaybind](displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[dual](dual.md)|Place une interface dans le fichier. idl en tant qu’interface double.|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivants seront traités et placés dans le fichier. idl généré.|
|[entry](entry.md)|Spécifie une fonction ou une constante exportée dans un module en identifiant le point d’entrée dans la DLL.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[export](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau à transmettre.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide d’une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier. hlp ou. chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer une recherche de chaîne de document (localisation).|
|[hidden](hidden.md)|Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[id](id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou une dispinterface).|
|[idl_module](idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](idl-quote.md)|Vous permet d’utiliser des attributs ou des constructions IDL qui ne sont pas prises en charge dans la C++version actuelle de Visual.|
|[iid_is](iid-is.md)|Spécifie l’IID de l’interface COM vers laquelle pointe un pointeur d’interface.|
|[immediatebind](immediatebind.md)|Indique que la base de données sera immédiatement notifiée de toutes les modifications apportées à la propriété d’un objet lié aux données.|
|[implements](implements-cpp.md)|Spécifie les interfaces de dispatch qui sont forcées à être membres de la coclasse IDL.|
|[implements_category](implements-category.md)|Spécifie les catégories de composant implémentées pour la classe.|
|[import](import.md)|Spécifie un autre fichier. idl,. ODL ou d’en-tête contenant les définitions que vous souhaitez référencer à partir de votre fichier main. idl.|
|[importidl](importidl.md)|Insère le fichier. idl spécifié dans le fichier. idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[in](in-cpp.md)|Indique qu’un paramètre doit être passé de la procédure appelante à la procédure appelée.|
|[include](include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier. idl généré.|
|[includelib](includelib-cpp.md)|Entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau à transmettre.|
|[lcid](lcid.md)|Vous permet de passer un identificateur de paramètres régionaux à une fonction.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau à transmettre.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[licensed](licensed.md)|Indique que la coclasse à laquelle elle s’applique est concédée sous licence et doit être instanciée à l’aide de `IClassFactory2`.|
|[local](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme générateur d’en-tête lorsqu’il est utilisé dans l’en-tête d’interface. En cas d’utilisation dans une fonction individuelle, désigne une procédure locale pour laquelle aucun stub n’est généré.|
|[max_is](max-is.md)|Désigne la valeur maximale d’un index de tableau valide.|
|[module](module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|
|[ms_union](ms-union.md)|Contrôle l’alignement de la représentation des données réseau des unions qui ne sont pas encapsulées.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.|
|[nonbrowsable](nonbrowsable.md)|Indique qu’un membre d’interface ne doit pas être affiché dans un Explorateur de propriétés.|
|[noncreatable](noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|
|[nonextensible](nonextensible.md)|Spécifie que l’implémentation de `IDispatch` comprend uniquement les propriétés et les méthodes listées dans la description de l’interface et ne peut pas être étendue avec des membres supplémentaires au moment de l’exécution.|
|[object](object-cpp.md)|Identifie une interface personnalisée ; synonyme d’attribut personnalisé.|
|[odl](odl.md)|Identifie une interface en tant qu’interface ODL (Object Description Language).|
|[oleautomation](oleautomation.md)|Indique qu’une interface est compatible avec Automation.|
|[facultatif](optional-cpp.md)|Spécifie un paramètre facultatif pour une fonction membre.|
|[out](out-cpp.md)|Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).|
|[pointer_default](pointer-default.md)|Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.|
|[pragma](pragma.md)|Émet la chaîne spécifiée, sans les guillemets, dans le fichier. idl généré.|
|[progid](progid.md)|Spécifie le ProgID d’un objet COM.|
|[propget](propget.md)|Spécifie une fonction d’accesseur de propriété (Get).|
|[propput](propput.md)|Spécifie une fonction de définition de propriété.|
|[propputref](propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence au lieu d’une valeur.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[public](public-cpp-attributes.md)|Garantit qu’un typedef sera placé dans la bibliothèque de types, même s’il n’est pas référencé dans le fichier. idl.|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[rdx](rdx.md)|Crée ou modifie une clé de registre.|
|[readonly](readonly-cpp.md)|Interdit l’assignation à une variable.|
|[ref](ref-cpp.md)|Identifie un pointeur de référence.|
|[registration_script](registration-script.md)|Exécute le script d’inscription spécifié.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la notification `OnRequestEdit`.|
|[requires_category](requires-category.md)|Spécifie les catégories de composants nécessaires pour la classe.|
|[restricted](restricted.md)|Spécifie qu’une bibliothèque, ou un membre d’un module, d’une interface ou d’une dispinterface ne peut pas être appelé arbitrairement.|
|[retval](retval.md)|Désigne le paramètre qui reçoit la valeur de retour du membre.|
|[satype](satype.md)|Spécifie le type de données du `SAFEARRAY`.|
|[size_is](size-is.md)|Spécifie la taille de la mémoire allouée aux pointeurs dimensionnés, aux pointeurs dimensionnés aux pointeurs dimensionnés et aux tableaux à une ou plusieurs dimensions.|
|[source](source-cpp.md)|Indique qu’un membre d’une classe, d’une propriété ou d’une méthode est une source d’événements.|
|[string](string-cpp.md)|Indique que le **caractère**unidimensionnel, **wchar_t**, `byte`ou un tableau équivalent, ou le pointeur vers ce tableau, doit être traité comme une chaîne.|
|[support_error_info](support-error-info.md)|Prend en charge la création de rapports d’erreurs pour l’objet cible.|
|[switch_is](switch-is.md)|Spécifie l’expression ou l’identificateur agissant comme le discriminante d’Union qui sélectionne le membre Union.|
|[switch_type](switch-type.md)|Identifie le type de la variable utilisée en tant qu’Union discriminante.|
|[synchronize](synchronize.md)|Synchronise l’accès à une méthode.|
|[threading](threading-cpp.md)|Spécifie le modèle de thread pour un objet COM.|
|[transmit_as](transmit-as.md)|Indique au compilateur d’associer un type présenté, que les applications client et serveur manipulent, avec un type transmis.|
|[uidefault](uidefault.md)|Indique que le membre des informations de type est le membre par défaut à afficher dans l’interface utilisateur.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[usesgetlasterror](usesgetlasterror.md)|Indique à l’appelant qu’en cas d’erreur lors de l’appel de cette fonction, l’appelant peut alors appeler `GetLastError` pour récupérer le code d’erreur.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique d’une classe ou d’une interface.|
|[v1_enum](v1-enum.md)|Indique que le type énuméré spécifié doit être transmis en tant qu’entité 32 bits, au lieu de la valeur par défaut 16 bits.|
|[vararg](vararg.md)|Spécifie que la fonction prend un nombre variable d’arguments.|
|[version](version-cpp.md)|Identifie une version particulière parmi plusieurs versions d’une interface ou d’une classe.|
|[vi_progid](vi-progid.md)|Spécifie une forme indépendante de la version du ProgID.|
|[wire_marshal](wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifique à l’application.|

## <a name="see-also"></a>Voir aussi

[Attributs C++ pour COM et .NET](cpp-attributes-com-net.md)<br/>
[Attributs par groupe](attributes-by-group.md)<br/>
[Attributs par utilisation](attributes-by-usage.md)
