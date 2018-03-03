---
title: Attributs IDL | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- IDL attributes
- .idl files, attributes
- IDL files, attributes
- .idl files
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 447c4369d7a80348dfb6c5eee54c49d76c1e8a4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes"></a>Attributs IDL
En règle générale, la gestion d’un fichier .idl signifiait que vous deviez :  
  
-   Être familiarisé avec la structure et la syntaxe d’un fichier .idl pour pouvoir le modifier.  
  
-   S’appuient sur un Assistant qui vous permet de modifier certains aspects du fichier .idl.  
  
 Maintenant, vous pouvez modifier le fichier .idl dans un fichier de code source à l’aide d’attributs Visual C++ IDL. Dans de nombreux cas, les attributs Visual C++ IDL ont le même nom que les attributs MIDL. Lorsque le nom d’un attribut Visual C++ IDL et un attribut MIDL sont identiques, cela signifie que le placement de l’attribut de Visual C++ dans votre fichier de code source entraîne un fichier .idl qui contient sa méthode ADO éponyme savoir un attribut MIDL. Toutefois, un attribut Visual C++ IDL peut ne pas fournit toutes les fonctionnalités d’un attribut MIDL.  
  
 Ne pas utilisé avec [attributs COM](../windows/com-attributes.md), attributs IDL vous permettent de définir les interfaces. Lorsque le code source est compilé, les attributs sont utilisés pour définir le fichier .idl généré. Lorsqu’il est utilisé avec les attributs de COM dans un projet ATL, certains attributs IDL, tel que **coclasse**, générer le code injectées dans le projet.  
  
 Notez que [idl_quote](../windows/idl-quote.md) vous permet d’utiliser des constructions MIDL qui ne sont pas pris en charge dans la version actuelle de Visual C++. Cela et autres attributs tels que [importlib](../windows/importlib.md) et [includelib](../windows/includelib-cpp.md) vous aider à utiliser les fichiers .idl existants dans votre projet Visual C++ actuel.  
  
|Attribut|Description|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|Indique qu’un contrôle peut être agrégé par un autre contrôle.|  
|[appobject](../windows/appobject.md)|Identifie la coclasse comme un objet de l’application, qui est associé à une application EXE complète et indique que les fonctions et les propriétés de la coclasse sont disponibles dans cette bibliothèque de types.|  
|[async_uuid](../windows/async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL pour définir des versions synchrones et asynchrones d’une interface COM.|  
|[bindable](../windows/bindable.md)|Indique que la propriété prend en charge la liaison de données.|  
|[call_as](../windows/call-as.md)|Permet à une fonction non accessibles à distance à associer à une fonction distante.|  
|[case](../windows/case-cpp.md)|Utilisé avec le [switch_type](../windows/switch-type.md) attribut dans une union.|  
|[coclass](../windows/coclass.md)|Emplacements de classe Définition dans un fichier .idl que coclasse.|  
|[control](../windows/control.md)|Spécifie que le type défini par l’utilisateur est un contrôle.|  
|[cpp_quote](../windows/cpp-quote.md)|Émet la chaîne spécifiée, sans guillemets, dans le fichier d’en-tête généré.|  
|[defaultbind](../windows/defaultbind.md)|Indique la propriété unique, pouvant être liée qui correspond le mieux à l’objet.|  
|[defaultcollelem](../windows/defaultcollelem.md)|Utilisé pour l’optimisation du code Visual Basic.|  
|[defaultvalue](../windows/defaultvalue.md)|Autorise la spécification d’une valeur par défaut pour un paramètre optionnel typé.|  
|[default](../windows/default-cpp.md)|Indique que l’interface personnalisée ou dispinterface définie dans une coclasse représente l’interface de programmabilité par défaut.|  
|[defaultvtable](../windows/defaultvtable.md)|Définit une interface en tant que l’interface de vtable par défaut pour un contrôle.|  
|[dispinterface](../windows/dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|  
|[displaybind](../windows/displaybind.md)|Indique une propriété qui doit être affichée à l’utilisateur comme pouvant être liée.|  
|[dual](../windows/dual.md)|Place une interface dans le fichier .idl comme une interface double.|  
|[entry](../windows/entry.md)|Spécifie une fonction exportée ou une constante dans un module en identifiant le point d’entrée dans la DLL.|  
|[first_is](../windows/first-is.md)|Spécifie l’index du premier élément du tableau doit être transmis.|  
|[helpcontext](../windows/helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|  
|[helpfile](../windows/helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|  
|[helpstring](../windows/helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|  
|[hidden](../windows/hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|  
|[idl_module](../windows/idl-module.md)|Spécifie un point d’entrée dans une DLL.|  
|[idl_quote](../windows/idl-quote.md)|Vous pouvez utiliser des attributs ou IDL constructions qui ne sont pas pris en charge dans la version actuelle de Visual C++.|  
|[ID](../windows/id.md)|Spécifie un DISPID pour une fonction membre (une propriété ou une méthode, dans une interface ou une dispinterface).|  
|[iid_is](../windows/iid-is.md)|Spécifie l’IID de l’interface COM vers laquelle pointé un pointeur d’interface.|  
|[immediatebind](../windows/immediatebind.md)|Indique que la base de données est immédiatement avertie de toutes les modifications apportées à une propriété d’un objet lié aux données.|  
|[importlib](../windows/importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|  
|[import](../windows/import.md)|Spécifie un autre fichier .idl, .odl ou en-tête contenant des définitions à référencer à partir de votre fichier .idl principal.|  
|[include](../windows/include-cpp.md)|Spécifie un ou plusieurs fichiers d’en-tête à inclure dans le fichier .idl généré.|  
|[includelib](../windows/includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|  
|[in](../windows/in-cpp.md)|Indique qu’un paramètre est à passer à la procédure appelée à partir de la procédure appelante.|  
|[last_is](../windows/last-is.md)|Spécifie l’index du dernier élément de tableau doit être transmis.|  
|[lcid](../windows/lcid.md)|Vous permet de passer un identificateur de paramètres régionaux à une fonction.|  
|[length_is](../windows/length-is.md)|Spécifie le nombre d’éléments de tableau doit être transmis.|  
|[licensed](../windows/licensed.md)|Indique que la coclasse auquel elle s’applique est concédé sous licence et doit être instanciée à l’aide de **IClassFactory2**.|  
|[local](../windows/local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.|  
|[max_is](../windows/max-is.md)|Désigne la valeur maximale pour un index de tableau valide.|  
|[module](../windows/module-cpp.md)|Définit le bloc de bibliothèque dans le fichier .idl.|  
|[ms_union](../windows/ms-union.md)|Contrôle l’alignement de représentation sous forme de données de réseau d’unions nonencapsulated.|  
|[no_injected_text](../windows/no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|  
|[nonbrowsable](../windows/nonbrowsable.md)|Indique qu’un membre d’interface ne doit pas être affiché dans la fenêtre Propriétés.|  
|[noncreatable](../windows/noncreatable.md)|Définit un objet qui ne peut pas être instancié par lui-même.|  
|[nonextensible](../windows/nonextensible.md)|Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peuvent pas être étendus avec des membres supplémentaires au moment de l’exécution.|  
|[object](../windows/object-cpp.md)|Identifie une interface personnalisée ; synonyme d’attribut personnalisé.|  
|[odl](../windows/odl.md)|Identifie l’interface comme une interface de l’objet Description Language (ODL).|  
|[oleautomation](../windows/oleautomation.md)|Indique qu’une interface est compatible avec l’Automation.|  
|[facultatif](../windows/optional-cpp.md)|Spécifie un paramètre facultatif pour une fonction membre.|  
|[out](../windows/out-cpp.md)|Identifie des paramètres pointeurs qui sont retournés de la procédure appelée à la procédure appelante (du serveur au client).|  
|[pointer_default](../windows/pointer-default.md)|Spécifie l’attribut du pointeur par défaut pour tous les pointeurs à l’exception des pointeurs de niveau supérieur qui s’affichent dans les listes de paramètres.|  
|[pragma](../windows/pragma.md)|Émet la chaîne spécifiée, sans guillemets, dans le fichier .idl généré.|  
|[progid](../windows/progid.md)|Spécifie le ProgID d’un objet COM.|  
|[propget](../windows/propget.md)|Spécifie une fonction d’accesseur (get) de propriété.|  
|[propputref](../windows/propputref.md)|Spécifie une fonction de définition de propriété qui utilise une référence au lieu d’une valeur.|  
|[propput](../windows/propput.md)|Spécifie une fonction de définition de propriété.|  
|[ptr](../windows/ptr.md)|Désigne un pointeur en tant que pointeur complet.|  
|[public](../windows/public-cpp-attributes.md)|Garantit qu’un typedef passera à la bibliothèque de types même s’il n’est pas référencé à partir du fichier .idl.|  
|[plage](../windows/range-cpp.md)|Spécifie une plage de valeurs autorisées pour les arguments ou les champs dont les valeurs sont définies au moment de l’exécution.|  
|[readonly](../windows/readonly-cpp.md)|Interdit l’assignation à une variable.|  
|[ref](../windows/ref-cpp.md)|Identifie un pointeur de référence.|  
|[requestedit](../windows/requestedit.md)|Indique que la propriété prend en charge la **OnRequestEdit** notification.|  
|[restricted](../windows/restricted.md)|Spécifie qu’une bibliothèque ou un membre d’un module, une interface ou une dispinterface ne peut pas être appelée arbitrairement.|  
|[retval](../windows/retval.md)|Désigne le paramètre qui reçoit la valeur de retour du membre.|  
|[size_is](../windows/size-is.md)|Spécifie la taille de mémoire allouée pour les pointeurs de tailles, taille des pointeurs vers des pointeurs de tailles et un ou des tableaux multidimensionnels.|  
|[source](../windows/source-cpp.md)|Indique qu’un membre d’une classe, une propriété ou une méthode est une source d’événements.|  
|[string](../windows/string-cpp.md)|Indique que la dimension `char`, `wchar_t`, **octets**, ou équivalent tableau ou pointeur vers ce type de tableau doit être traité en tant que chaîne.|  
|[switch_is](../windows/switch-is.md)|Spécifie l’expression ou identificateur agissant comme l’union discriminante qui sélectionne le membre d’union.|  
|[switch_type](../windows/switch-type.md)|Identifie le type de la variable utilisée en tant que l’union discriminante.|  
|[transmit_as](../windows/transmit-as.md)|Indique au compilateur pour associer un type présenté, les applications clientes et serveur manipulent, avec un type transmis.|  
|[uidefault](../windows/uidefault.md)|Indique que le membre du type d’informations est le membre par défaut pour l’affichage dans l’interface utilisateur.|  
|[unique](../windows/unique-cpp.md)|Spécifie un pointeur unique.|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|Indique à l’appelant que s’il existe une erreur lors de l’appel de cette fonction, l’appelant peut ensuite appeler `GetLastError` pour récupérer le code d’erreur.|  
|[UUID](../windows/uuid-cpp-attributes.md)|Spécifie l’ID unique pour une classe ou interface.|  
|[v1_enum](../windows/v1-enum.md)|Indique que le type énuméré spécifié être transmis en tant qu’une entité de 32 bits, plutôt que la valeur par défaut de 16 bits.|  
|[vararg](../windows/vararg.md)|Spécifie que la fonction accepte un nombre variable d’arguments.|  
|[vi_progid](../windows/vi-progid.md)|Spécifie un formulaire indépendant de la version du ProgID.|  
|[wire_marshal](../windows/wire-marshal.md)|Spécifie un type de données qui sera utilisé pour la transmission au lieu d’un type de données spécifiques à l’application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs par groupe](../windows/attributes-by-group.md)   
 [Limitations des attributs](http://msdn.microsoft.com/en-us/6e6c4329-f667-4869-b991-cbe9cb7a8f61)