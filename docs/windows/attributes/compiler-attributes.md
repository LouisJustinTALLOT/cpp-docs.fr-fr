---
description: 'En savoir plus sur : attributs du compilateur'
title: Attributs du compilateur (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: 6d2cbb6bcffb5108ec98fe2786f9fb2216a79b9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306532"
---
# <a name="compiler-attributes"></a>Attributs de compilateur

Les attributs du compilateur offrent un large éventail de fonctionnalités.

|Attribut|Description|
|---------------|-----------------|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivants seront traités et placés dans le fichier. idl généré.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[exporter](export.md)|Entraîne le placement d’une structure de données dans le fichier. idl.|
|[implémente](implements-cpp.md)|Spécifie les interfaces de dispatch qui sont forcées à être membres de la coclasse IDL.|
|[importidl](importidl.md)|Insère le fichier. idl spécifié dans le fichier. idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[includelib (](includelib-cpp.md)|Entraîne l’inclusion d’un fichier. idl ou. h dans le fichier. idl généré.|
|[library_block](library-block.md)|Place une construction dans le bloc de bibliothèque du fichier. idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code en raison de l’utilisation d’un attribut.|
|[satype](satype.md)|Spécifie le type de données de `SAFEARRAY` .|
|[version](version-cpp.md)|Identifie une version particulière parmi plusieurs versions d’une interface ou d’une classe.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)
