---
description: 'En savoir plus sur : attributs d’interface'
title: Attributs d’interface (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 4a2584f6d0ad73427c9460cd5ddafb92d11db9b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118327"
---
# <a name="interface-attributes"></a>Attributs d'interface

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

[Attributs par utilisation](attributes-by-usage.md)
