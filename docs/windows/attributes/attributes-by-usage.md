---
title: Attributs par utilisation
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: dcbed019f8cd08ddbf4ab6b4756a59f7fcbabc4b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361337"
---
# <a name="attributes-by-usage"></a>Attributs par utilisation

Ce sujet énumère les attributs en fonction des éléments linguistiques CMD auxquels ils s’appliquent.

Si un attribut précède un élément qui n’est pas dans la portée de l’attribut, le bloc d’attribut est traité comme un commentaire.

|Attribut|Description|
|---------------|-----------------|
|[Attributs du module](module-attributes.md)|S’applique à l’attribut du [module.](module-cpp.md)|
|[Attributs d'interface](interface-attributes.md)|S’applique au mot clé [__interface](../../cpp/interface.md) CMD.|
|[Attributs de classe](class-attributes.md)|S’applique au mot-clé C.|
|[Attributs de méthode](method-attributes.md)|S’applique aux méthodes d’une classe, d’une coclasse ou d’une interface.|
|[Attributs de paramètre](parameter-attributes.md)|S’applique aux paramètres d’une méthode dans une classe ou une interface.|
|[Attributs de membre de données](data-member-attributes.md)|S’applique aux membres de données dans une classe, une coclasse ou une interface.|
|[Typesdef, Enum, Union et Struct Attributes](typedef-enum-union-and-struct-attributes.md)|S’applique aux mots-clés C.|
|[Attributs de tableau](array-attributes.md)|S’applique aux `SAFEARRAY`tableaux ou s.|
|[Attributs autonomes](stand-alone-attributes.md)|Fonctionne plus comme une ligne de code, mais ne fonctionne pas sur un mot clé C. Les énoncés d’attribut autonomes nécessitent un point-virgule à la fin de la ligne.|
|[Attributs personnalisés](custom-attributes-cpp.md)|Permet à l’utilisateur d’étendre les métadonnées.|

## <a name="module-attributes"></a>Attributs de module

L’attribut suivant ne peut être appliqué qu’à l’attribut du [module.](module-cpp.md)

|Attribut|Description|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Spécifie le nom du DLL à utiliser pour effectuer la recherche de chaînes de documents (localisation).|

## <a name="interface-attributes"></a>Attributs d'interface

Les attributs suivants s’appliquent au mot clé de [l’interface (ou __interface)](../../cpp/interface.md) CMD.

|Attribut|Description|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Spécifie l’UUID qui dirige le compilateur MIDL pour définir les versions synchrones et asynchrones d’une interface COM.|
|[Personnalisé](custom-cpp.md)|Vous permet de définir vos propres attributs.|
|[dispinterface](dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|
|[Double](dual.md)|Place une interface dans le fichier .idl comme une double interface.|
|[Exportation](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[helpcontext](helpcontext.md)|Spécifie un ID contextuelle qui permet à l’utilisateur de visualiser les informations sur cet élément dans le fichier d’aide.|
|[helpfile](helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de type.|
|[helpstring](helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|
|[helpstringcontext](helpstringcontext.md)|Spécifie l’ID d’un sujet d’aide dans un fichier .hlp ou .chm.|
|[helpstringdll](helpstringdll.md)|Spécifie le nom du DLL à utiliser pour effectuer la recherche de chaînes de documents (localisation).|
|[Cachés](hidden.md)|Indique que l’élément existe mais ne doit pas être affiché dans un navigateur orienté vers l’utilisateur.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[local](local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour laquelle aucun talon n’est généré.|
|[nonextensible](nonextensible.md)|Précise que la `IDispatch` mise en œuvre ne comprend que les propriétés et les méthodes énumérées dans la description de l’interface et ne peut pas être étendue avec des membres supplémentaires au moment de l’exécution. Cet attribut n’est valable que sur une [double](dual.md) interface.|
|[Odl](odl.md)|Identifie une interface comme une interface langage de description d’objet (ODL).|
|[Objet](object-cpp.md)|Identifie une interface personnalisée.|
|[oleautomation](oleautomation.md)|Indique qu’une interface est compatible avec Automation.|
|[pointer_default](pointer-default.md)|Spécifie l’attribut de pointeur par défaut pour tous les pointeurs, sauf les pointeurs de haut niveau qui apparaissent dans les listes de paramètres.|
|[Ptr](ptr.md)|Désigne un pointeur comme pointeur complet.|
|[Restreint](restricted.md)|Désigne quels membres de la bibliothèque ne peuvent pas être appelés arbitrairement.|
|[uuid](uuid-cpp-attributes.md)|Fournit l’ID unique pour la bibliothèque|

Vous devez observer ces règles pour définir une interface :

- La convention d’appel par défaut est [__stdcall](../../cpp/stdcall.md).

- Un GUID vous est fourni si vous n’en fournissez pas un.

- Aucune méthode surchargée n’est autorisée.

Lorsqu’il ne spécifie pas l’attribut [uuid](uuid-cpp-attributes.md) et que vous n’utilisez pas le même nom d’interface dans différents projets d’attributs, le même GUID est généré.

## <a name="see-also"></a>Voir aussi

[Attributs C++ pour COM et .NET](cpp-attributes-com-net.md)<br/>
[Attributs par Groupe](attributes-by-group.md)<br/>
[Attributs Référence alphabétique](attributes-alphabetical-reference.md)
