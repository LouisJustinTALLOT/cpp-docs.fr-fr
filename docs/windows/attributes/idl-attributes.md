---
title: Attributs IDL (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: a699e327eec056bbb36747840990bb9c7ccc259b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409549"
---
# <a name="idl-attributes"></a>Attributs IDL

En règle générale, la gestion d’un fichier .idl signifiait que vous deviez :

- Vous familiariser avec la structure et la syntaxe d’un fichier .idl à être en mesure de le modifier.

- S’appuient sur un Assistant qui vous permet de modifier certains aspects du fichier .idl.

Maintenant, vous pouvez modifier le fichier .idl dans un fichier de code source à l’aide d’attributs Visual C++ IDL. Dans de nombreux cas, les attributs Visual C++ IDL ont le même nom en tant qu’attributs MIDL. Lorsque le nom d’un attribut Visual C++ IDL et un attribut MIDL sont identiques, cela signifie que le placement de l’attribut de Visual C++ dans votre fichier de code source entraîne dans un fichier .idl contenant son attribut MIDL de méthode ADO éponyme savoir. Toutefois, un attribut Visual C++ IDL ne peut pas fournir toutes les fonctionnalités d’un attribut MIDL.

Ne pas utilisé avec [attributs COM](com-attributes.md), attributs IDL vous permettent de définir des interfaces. Lorsque le code source est compilé, les attributs sont utilisés pour définir le fichier .idl généré. Lorsqu’il est utilisé avec les attributs COM dans un projet ATL, certains attributs IDL, tel que `coclass`, du code à injecter dans le projet.

Notez que [idl_quote](idl-quote.md) vous permet d’utiliser des constructions MIDL qui ne sont pas pris en charge dans la version actuelle de Visual C++. Cela et autres attributs, tels que [importlib](importlib.md) et [includelib](includelib-cpp.md) vous aider à utiliser les fichiers .idl existants dans votre projet Visual C++ actuel.

|Attribut|Description|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|
|[appobject](appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application EXE complète et indique que les fonctions et les propriétés de la coclasse sont globalement disponibles dans cette bibliothèque de types.|
|[async_uuid](async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL pour définir des versions synchrones et asynchrones d’une interface COM.|
|[bindable](bindable.md)|Indique que la propriété prend en charge la liaison de données.|
|[call_as](call-as.md)|Permet à une fonction non accessibles à distance à mapper à une fonction à distance.|
|[case](case-cpp.md)|Utilisé avec le [switch_type](switch-type.md) attribut dans une union.|
|[coclasse](coclass.md)|Définition dans un fichier .idl que coclasse de classe de lieux.|
|[control](control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|
|[cpp_quote](cpp-quote.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier d’en-tête généré.|
|[defaultbind](defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|
|[defaultcollelem](defaultcollelem.md)|Utilisé pour l’optimisation du code Visual Basic.|
|[defaultvalue](defaultvalue.md)|Permet de spécifier une valeur par défaut pour un paramètre facultatif typé.|
|[default](default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|
|[defaultvtable](defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|
|[dispinterface](dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|
|[displaybind](displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|
|[dual](dual.md)|Place une interface dans le fichier .idl comme une interface double.|
|[entry](entry.md)|Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.|
|[first_is](first-is.md)|Spécifie l’index du premier élément de tableau doit être transmis.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[hidden](hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[idl_module](idl-module.md)|Spécifie un point d’entrée dans une DLL.|
|[idl_quote](idl-quote.md)|Vous permet d’utiliser des attributs ou IDL construit qui ne sont pas pris en charge dans la version actuelle de Visual C++.|
|[ID](id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou la dispinterface).|
|[iid_is](iid-is.md)|Spécifie l’IID de l’interface COM vers laquelle pointé un pointeur d’interface.|
|[immediatebind](immediatebind.md)|Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[import](import.md)|Spécifie un autre fichier .idl, .odl ou en-tête contenant les définitions que vous souhaitez référencer à partir de votre fichier .idl principal.|
|[include](include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.|
|[includelib](includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|
|[in](in-cpp.md)|Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.|
|[last_is](last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|
|[lcid](lcid.md)|Vous permet de passer un identificateur de paramètres régionaux à une fonction.|
|[length_is](length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|
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
|[optional](optional-cpp.md)|Spécifie un paramètre facultatif pour une fonction membre.|
|[out](out-cpp.md)|Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).|
|[pointer_default](pointer-default.md)|Spécifie l’attribut de pointeur par défaut pour tous les pointeurs à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.|
|[pragma](pragma.md)|Émet la chaîne spécifiée, sans les caractères guillemet, dans le fichier .idl généré.|
|[progid](progid.md)|Spécifie le ProgID pour un objet COM.|
|[propget](propget.md)|Spécifie une fonction d’accesseur (get) de propriété.|
|[propputref](propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence plutôt qu’une valeur.|
|[propput](propput.md)|Spécifie une fonction de définition de propriété.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[public](public-cpp-attributes.md)|Garantit qu’un typedef passera à la bibliothèque de types même s’il n’est pas référencé à partir du fichier .idl.|
|[range](range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|
|[readonly](readonly-cpp.md)|Interdit l’assignation à une variable.|
|[ref](ref-cpp.md)|Identifie un pointeur de référence.|
|[requestedit](requestedit.md)|Indique que la propriété prend en charge la notification `OnRequestEdit`.|
|[restricted](restricted.md)|Spécifie qu’une bibliothèque ou un membre d’un module, une interface ou une dispinterface ne peut pas être appelée arbitrairement.|
|[retval](retval.md)|Désigne le paramètre qui reçoit la valeur de retour du membre.|
|[size_is](size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de taille, taille des pointeurs vers des pointeurs de taille et seul ou les tableaux multidimensionnels.|
|[source](source-cpp.md)|Indique qu’un membre d’une classe, une propriété ou une méthode est une source d’événements.|
|[string](string-cpp.md)|Indique qu’unidimensionnel **char**, **wchar_t**, `byte`, ou tableau équivalent ou le pointeur vers ce type de tableau doit être traité comme une chaîne.|
|[switch_is](switch-is.md)|Spécifie l’expression ou l’identificateur agissant comme l’union discriminante qui sélectionne le membre d’union.|
|[switch_type](switch-type.md)|Identifie le type de la variable utilisée en tant que l’union discriminante.|
|[transmit_as](transmit-as.md)|Indique au compilateur d’associer un type présenté, les applications clientes et serveur manipulent, à un type transmis.|
|[uidefault](uidefault.md)|Indique que le membre d’informations de type est le membre par défaut pour l’affichage dans l’interface utilisateur.|
|[unique](unique-cpp.md)|Spécifie un pointeur unique.|
|[usesgetlasterror](usesgetlasterror.md)|Indique à l’appelant que s’il existe une erreur lors de l’appel de cette fonction, l’appelant peut ensuite appeler `GetLastError` pour récupérer le code d’erreur.|
|[uuid](uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|
|[v1_enum](v1-enum.md)|Indique que le type énuméré spécifié être transmises comme une entité de 32 bits, plutôt que la valeur par défaut de 16 bits.|
|[vararg](vararg.md)|Spécifie que la fonction accepte un nombre variable d’arguments.|
|[vi_progid](vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|
|[wire_marshal](wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifiques à l’application.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)
