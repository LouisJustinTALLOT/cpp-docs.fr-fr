---
title: Attributs du compilateur (C++ COM) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f0483676fd0dd60d893f8931511083d369539dd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790636"
---
# <a name="compiler-attributes"></a>Attributs de compilateur

Attributs de compilateur fournissent de nombreuses fonctionnalités.

|Attribut|Description|
|---------------|-----------------|
|[emitidl](emitidl.md)|Détermine si tous les attributs IDL suivantes seront traitées et placés dans le fichier .idl généré.|
|[event_receiver](event-receiver.md)|Crée un récepteur d’événements.|
|[event_source](event-source.md)|Crée une source d'événement.|
|[export](export.md)|Provoque une structure de données à placer dans le fichier .idl.|
|[Implémente](implements-cpp.md)|Spécifie les interfaces de dispatch obligés d’être membres de la coclasse IDL.|
|[importidl](importidl.md)|Insère le fichier .idl spécifié dans le fichier .idl généré.|
|[importlib](importlib.md)|Rend disponibles les types qui ont déjà été compilés dans une autre bibliothèque de types pour la bibliothèque de types en cours de création.|
|[includelib](includelib-cpp.md)|Génère un fichier .idl ou .h à inclure dans le fichier .idl généré.|
|[library_block](library-block.md)|Place une construction à l’intérieur du bloc de bibliothèque du fichier .idl.|
|[no_injected_text](no-injected-text.md)|Empêche le compilateur d’injecter du code à la suite d’utilisation de l’attribut.|
|[satype](satype.md)|Spécifie le type de données de la `SAFEARRAY`.|
|[version](version-cpp.md)|Identifie une version particulière entre plusieurs versions d’une interface ou une classe.|

## <a name="see-also"></a>Voir aussi

[Attributs par groupe](attributes-by-group.md)