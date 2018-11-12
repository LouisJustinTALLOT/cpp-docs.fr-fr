---
title: Attributs par utilisation
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: 2536309025506ca66d9c4b7cdfbaabf5787945e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449362"
---
# <a name="attributes-by-usage"></a>Attributs par utilisation

Cette rubrique répertorie les attributs selon les éléments de langage C++ auquel elles s’appliquent.

Si un attribut précède un élément qui n’est pas dans la portée de l’attribut, le bloc d’attributs est traité comme un commentaire.

|Attribut|Description|
|---------------|-----------------|
|[Attributs de module](module-attributes.md)|S’applique à la [module](module-cpp.md) attribut.|
|[Attributs d’interface](interface-attributes.md)|S’applique à la [__interface](../../cpp/interface.md) mot clé C++.|
|[Attributs de classe](class-attributes.md)|S’applique au mot clé C++.|
|[Attributs de méthode](method-attributes.md)|S’applique aux méthodes dans une classe, une coclasse ou une interface.|
|[Attributs de paramètres](parameter-attributes.md)|S’applique aux paramètres d’une méthode dans une classe ou interface.|
|[Attributs de membre de données](data-member-attributes.md)|S’applique aux membres de données dans une classe, une coclasse ou une interface.|
|[Attributs Typedef, Enum, Union et Struct](typedef-enum-union-and-struct-attributes.md)|S’applique aux mots clés C++.|
|[Attributs de tableau](array-attributes.md)|S’applique aux tableaux ou `SAFEARRAY`s.|
|[Attributs autonomes](stand-alone-attributes.md)|Fonctionne plus comme une ligne de code, mais ne fonctionne pas sur un mot clé C++. Les instructions d’attribut autonome nécessitent un point-virgule à la fin de la ligne.|
|[Attributs personnalisés](custom-attributes-cpp.md)|Permet à l’utilisateur d’étendre les métadonnées.|

## <a name="module-attributes"></a>Attributs de module
L’attribut suivant peut uniquement être appliqué à la [module](module-cpp.md) attribut.

|Attribut|Description|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|

## <a name="interface-attributes"></a>Attributs d'interface

Les attributs suivants s’appliquent à la [interface (ou __interface)](../../cpp/interface.md) mot clé C++.

|Attribut|Description|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL pour définir des versions synchrones et asynchrones d’une interface COM.|
|[custom](custom-cpp.md)|Vous permet de définir vos propres attributs.|
|[dispinterface](dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|
|[dual](dual.md)|Place une interface dans le fichier .idl comme une interface double.|
|[export](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui vous permet de l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|
|[hidden](hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[local](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.|
|[nonextensible](nonextensible.md)|Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peut pas être étendus avec des membres supplémentaires en cours d’exécution. Cet attribut est valide uniquement sur un [double](dual.md) interface.|
|[odl](odl.md)|Identifie une interface en tant qu’objet Description Language (ODL) interface.|
|[object](object-cpp.md)|Identifie une interface personnalisée.|
|[oleautomation](oleautomation.md)|Indique qu’une interface est compatible avec Automation.|
|[pointer_default](pointer-default.md)|Spécifie l’attribut de pointeur par défaut pour tous les pointeurs à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[restricted](restricted.md)|Désigne les membres de la bibliothèque ne peut pas être appelées arbitrairement.|
|[uuid](uuid-cpp-attributes.md)|Fournit l’ID unique de la bibliothèque|

Vous devez respecter ces règles pour définir une interface :

- Valeur par défaut de la convention d’appel est [__stdcall](../../cpp/stdcall.md).

- Un GUID est fourni pour vous si vous ne fournissez pas une.

- Aucune des méthodes surchargées ne sont autorisées.

Lorsque vous ne spécifiez ne pas le [uuid](uuid-cpp-attributes.md) d’attribut et à l’aide du même nom d’interface dans les projets de l’autre attribut, le même GUID est généré.

## <a name="see-also"></a>Voir aussi

[Attributs C++ pour COM et .NET](cpp-attributes-com-net.md)<br/>
[Attributs par groupe](attributes-by-group.md)<br/>
[Référence alphabétique des attributs](attributes-alphabetical-reference.md)