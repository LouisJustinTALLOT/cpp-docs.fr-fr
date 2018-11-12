---
title: Attributs du compilateur C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: 8fef953a520572b42e69a48ea391282c7b70ba44
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667361"
---
# <a name="compiler-attributes"></a>Attributs de compilateur

Attributs de compilateur fournissent de nombreuses fonctionnalités.

|Attribut|Description|
|---------------|-----------------|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivantes seront traitées et placés dans le fichier .idl généré.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[export](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[implements](implements-cpp.md)|Spécifie les interfaces de dispatch obligés d’être membres de la coclasse IDL.|
|[importidl](importidl.md)|Insère le fichier .idl spécifié dans le fichier .idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[includelib](includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|
|[satype](satype.md)|Spécifie le type de données de la `SAFEARRAY`.|
|[version](version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une interface ou une classe.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)