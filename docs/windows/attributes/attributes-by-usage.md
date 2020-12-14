---
description: 'En savoir plus sur : attributs par utilisation'
title: Attributs par utilisation
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: 7f199ec1ede4cbaeddd46518f29a4b73edb40547
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247538"
---
# <a name="attributes-by-usage"></a>Attributs par utilisation

Cette rubrique répertorie les attributs en fonction des éléments du langage C++ auxquels ils s’appliquent.

Si un attribut précède un élément qui n’est pas dans la portée de l’attribut, le bloc d’attributs est traité comme un commentaire.

|Attribut|Description|
|---------------|-----------------|
|[Attributs de module](module-attributes.md)|S’applique à l’attribut de [module](module-cpp.md) .|
|[Attributs d’interface](interface-attributes.md)|S’applique au mot clé C++ [__interface](../../cpp/interface.md) .|
|[Attributs de classe](class-attributes.md)|S’applique au mot clé C++.|
|[Attributs de méthode](method-attributes.md)|S’applique aux méthodes d’une classe, d’une coclasse ou d’une interface.|
|[Attributs de paramètre](parameter-attributes.md)|S’applique aux paramètres d’une méthode dans une classe ou une interface.|
|[Attributs de membre de données](data-member-attributes.md)|S’applique aux membres de données dans une classe, une coclasse ou une interface.|
|[Attributs typedef, enum, Union et struct](typedef-enum-union-and-struct-attributes.md)|S’applique aux mots clés C++.|
|[Attributs de tableau](array-attributes.md)|S’applique aux tableaux ou aux `SAFEARRAY` .|
|[Attributs autonomes](stand-alone-attributes.md)|Fonctionne plus comme une ligne de code, mais ne fonctionne pas sur un mot clé C++. Les instructions d’attribut autonome requièrent un point-virgule à la fin de la ligne.|
|[Attributs personnalisés](custom-attributes-cpp.md)|Permet à l’utilisateur d’étendre les métadonnées.|

## <a name="module-attributes"></a>Attributs de module

L’attribut suivant ne peut être appliqué qu’à l’attribut de [module](module-cpp.md) .

|Attribut|Description|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer une recherche de chaîne de document (localisation).|

## <a name="interface-attributes"></a>Attributs d'interface

Les attributs suivants s’appliquent au mot clé C++ de l' [interface (ou __interface)](../../cpp/interface.md) .

|Attribut|Description|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL de définir à la fois les versions synchrones et asynchrones d’une interface COM.|
|[propre](custom-cpp.md)|Vous permet de définir vos propres attributs.|
|[dispinterface](dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|
|[double](dual.md)|Place une interface dans le fichier. idl en tant qu’interface double.|
|[exporter](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[helpcontext](helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur d’afficher des informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide d’une bibliothèque de types.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier. hlp ou. chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer une recherche de chaîne de document (localisation).|
|[masquer](hidden.md)|Indique que l’élément existe mais qu’il ne doit pas être affiché dans un navigateur orienté utilisateur.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[localisé](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme générateur d’en-tête lorsqu’il est utilisé dans l’en-tête d’interface. En cas d’utilisation dans une fonction individuelle, désigne une procédure locale pour laquelle aucun stub n’est généré.|
|[nonextensible](nonextensible.md)|Spécifie que l' `IDispatch` implémentation de comprend uniquement les propriétés et les méthodes listées dans la description de l’interface et ne peut pas être étendue avec des membres supplémentaires au moment de l’exécution. Cet attribut n’est valide que sur une interface [double](dual.md) .|
|[ODL](odl.md)|Identifie une interface en tant qu’interface ODL (Object Description Language).|
|[object](object-cpp.md)|Identifie une interface personnalisée.|
|[oleautomation](oleautomation.md)|Indique qu’une interface est compatible avec Automation.|
|[pointer_default](pointer-default.md)|Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, à l’exception des pointeurs de niveau supérieur qui apparaissent dans les listes de paramètres.|
|[ptr](ptr.md)|Désigne un pointeur comme un pointeur complet.|
|[sensible](restricted.md)|Désigne les membres de la bibliothèque qui ne peuvent pas être appelés de façon arbitraire.|
|[uuid](uuid-cpp-attributes.md)|Fournit l’ID unique de la bibliothèque.|

Vous devez respecter les règles suivantes pour définir une interface :

- La Convention d’appel par défaut est [__stdcall](../../cpp/stdcall.md).

- Un GUID est fourni si vous n’en fournissez pas un.

- Aucune méthode surchargée n’est autorisée.

Lorsque vous ne spécifiez pas l’attribut [UUID](uuid-cpp-attributes.md) et que vous utilisez le même nom d’interface dans différents projets d’attributs, le même GUID est généré.

## <a name="see-also"></a>Voir aussi

[Attributs C++ pour COM et .NET](cpp-attributes-com-net.md)<br/>
[Attributs par groupe](attributes-by-group.md)<br/>
[Référence alphabétique des attributs](attributes-alphabetical-reference.md)
