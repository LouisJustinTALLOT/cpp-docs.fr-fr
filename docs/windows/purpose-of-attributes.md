---
title: Objectif des attributs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b34ff9641df4d102c2902e5b8ea42a80db4db50
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607098"
---
# <a name="purpose-of-attributes"></a>Objectif des attributs

Attributs étendent C++ dans les directions n’est pas actuellement possibles sans casser la structure classique de la langue. Attributs permettent aux fournisseurs (DLL séparées) pour étendre les fonctionnalités de langage dynamique. Le principal objectif des attributs est de simplifier la création de composants COM, en plus d’augmenter la productivité des développeurs de composants. Attributs peuvent être appliqués à presque n’importe quelle construction C++, telles que des classes, des membres de données ou des fonctions membres. Voici une mise en surbrillance des avantages offerts par cette nouvelle technologie :

- Expose une convention d’appel familière et simple.

- Le code inséré, qui, contrairement aux macros, n’est reconnu par le débogueur.

- Permet la dérivation facile à partir de classes de base sans détails d’implémentation laborieux.

- Remplace la grande quantité de code IDL requis par un composant COM avec quelques attributs simples.

Par exemple, pour implémenter un récepteur d’événements simple pour une classe ATL générique, vous pouvez appliquer le [event_receiver](../windows/event-receiver.md) attribut sur une classe spécifique, tel que `CMyReceiver`. Le `event_receiver` attribut est ensuite compilé par le compilateur Visual C++, qui insère le code approprié dans le fichier objet.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Vous pouvez ensuite configurer le `CMyReceiver` méthodes `handler1` et `handler2` pour gérer les événements (à l’aide de la fonction intrinsèque [__hook](../cpp/hook.md)) à partir d’une source d’événement, vous pouvez créer à l’aide de [event_source](../windows/event-source.md).

## <a name="see-also"></a>Voir aussi

[Concepts](../windows/attributed-programming-concepts.md)