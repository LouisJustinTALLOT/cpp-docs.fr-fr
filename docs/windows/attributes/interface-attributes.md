---
title: Attributs (C++ COM) de l’interface | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd12db4235d22245c3f31ce7dfe3fd2470133dfd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790669"
---
# <a name="interface-attributes"></a>Attributs d'interface

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

[Attributs par utilisation](attributes-by-usage.md)