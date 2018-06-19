---
title: Attributs d’interface | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6f57cdce20a54b8bc56b804e12f59f92855c7f69
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880203"
---
# <a name="interface-attributes"></a>Attributs d'interface
Les attributs suivants s’appliquent à la [interface (ou __interface)](../cpp/interface.md) mot clé C++.  
  
|Attribut|Description|  
|---------------|-----------------|  
|[async_uuid](../windows/async-uuid.md)|Spécifie l’UUID qui indique au compilateur MIDL pour définir des versions synchrones et asynchrones d’une interface COM.|  
|[custom](../windows/custom-cpp.md)|Permet de définir vos propres attributs.|  
|[dispinterface](../windows/dispinterface.md)|Place une interface dans le fichier .idl comme interface de dispatch.|  
|[dual](../windows/dual.md)|Place une interface dans le fichier .idl comme une interface double.|  
|[export](../windows/export.md)|Provoque une structure de données doit être placé dans le fichier .idl.|  
|[helpcontext](../windows/helpcontext.md)|Spécifie un ID de contexte qui permet à l’utilisateur afficher des informations sur cet élément dans le fichier d’aide.|  
|[helpfile](../windows/helpfile.md)|Définit le nom du fichier d’aide pour une bibliothèque de types.|  
|[helpstring](../windows/helpstring.md)|Spécifie une chaîne de caractères qui est utilisée pour décrire l’élément auquel elle s’applique.|  
|[helpstringcontext](../windows/helpstringcontext.md)|Spécifie l’ID d’une rubrique d’aide dans un fichier .hlp ou .chm.|  
|[helpstringdll](../windows/helpstringdll.md)|Spécifie le nom de la DLL à utiliser pour effectuer la recherche de chaîne de document (localisation).|  
|[hidden](../windows/hidden.md)|Indique que l’élément existe, mais ne doit pas être affiché dans un navigateur orienté utilisateur.|  
|[library_block](../windows/library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|  
|[Local](../windows/local-cpp.md)|Vous permet d’utiliser le compilateur MIDL comme un générateur d’en-tête lorsqu’il est utilisé dans l’en-tête de l’interface. Lorsqu’il est utilisé dans une fonction individuelle, désigne une procédure locale pour lequel aucun stub n’est générés.|  
|[nonextensible](../windows/nonextensible.md)|Spécifie que le `IDispatch` implémentation inclut uniquement les propriétés et méthodes répertoriées dans la description de l’interface et ne peuvent pas être étendus avec des membres supplémentaires au moment de l’exécution. Cet attribut est valide uniquement sur un [double](../windows/dual.md) interface.|  
|[odl](../windows/odl.md)|Identifie l’interface comme une interface de l’objet Description Language (ODL).|  
|[object](../windows/object-cpp.md)|Identifie une interface personnalisée.|  
|[oleautomation](../windows/oleautomation.md)|Indique qu’une interface est compatible avec l’Automation.|  
|[pointer_default](../windows/pointer-default.md)|Spécifie l’attribut du pointeur par défaut pour tous les pointeurs à l’exception des pointeurs de niveau supérieur qui s’affichent dans les listes de paramètres.|  
|[ptr](../windows/ptr.md)|Désigne un pointeur en tant que pointeur complet.|  
|[restricted](../windows/restricted.md)|Désigne les membres de la bibliothèque ne peut pas être appelées arbitrairement.|  
|[uuid](../windows/uuid-cpp-attributes.md)|Fournit l’ID unique de la bibliothèque|  
  
 Vous devez observer les règles suivantes pour la définition d’une interface :  
  
-   Valeur par défaut de la convention d’appel est [__stdcall](../cpp/stdcall.md).  
  
-   Un GUID est fourni pour vous si vous ne fournissez pas un.  
  
-   Aucuns méthodes surchargées ne sont autorisées.  
  
 Lorsque vous ne spécifiez ne pas le [uuid](../windows/uuid-cpp-attributes.md) d’attribut et à l’aide du même nom d’interface dans les projets de l’attribut différent, le même GUID est généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs par utilisation](../windows/attributes-by-usage.md)