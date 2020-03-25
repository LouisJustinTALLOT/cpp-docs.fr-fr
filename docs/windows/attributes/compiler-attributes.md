---
title: Attributs du compilateurC++ (com)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: f8eb15645049085acc047e41d0a4ea769d359871
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168277"
---
# <a name="compiler-attributes"></a>Attributs de compilateur

Les attributs du compilateur offrent un large éventail de fonctionnalités.

|Attribut|Description|
|---------------|-----------------|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivants seront traités et placés dans le fichier. idl généré.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[export](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[implements](implements-cpp.md)|Spécifie les interfaces de dispatch qui sont forcées à être membres de la coclasse IDL.|
|[importidl](importidl.md)|Insère le fichier. idl spécifié dans le fichier. idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[includelib](includelib-cpp.md)|Entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.|
|[satype](satype.md)|Spécifie le type de données du `SAFEARRAY`.|
|[version](version-cpp.md)|Identifie une version particulière parmi plusieurs versions d’une interface ou d’une classe.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)
