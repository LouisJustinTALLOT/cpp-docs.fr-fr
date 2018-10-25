---
title: Utilisation d’IDispEventImpl (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d28a9a8bad8ced772d5c698e76d3d08f09c8db2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066472"
---
# <a name="using-idispeventimpl"></a>Utilisation d’IDispEventImpl

Lorsque vous utilisez `IDispEventImpl` pour gérer les événements, vous devez :

- Dérivez votre classe de [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Ajoutez une table de récepteur d’événements à votre classe.

- Ajouter des entrées à la carte de récepteur événement à l’aide du [aide de SINK_ENTRY](reference/composite-control-macros.md#sink_entry) ou [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) (macro).

- Implémenter les méthodes qui vous intéresse dans la gestion des.

- Et désinformation la source d’événements.

## <a name="example"></a>Exemple

L’exemple ci-dessous montre comment gérer les `DocumentChange` événements déclenchement par de Word **Application** objet. Cet événement est défini en tant que méthode sur le `ApplicationEvents` dispinterface.

L’exemple est issu le [exemple ATLEventHandling](../visual-cpp-samples.md).

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

L’exemple utilise `#import` pour générer les fichiers d’en-tête requis à partir de la bibliothèque de types de Word. Si vous souhaitez utiliser cet exemple avec d’autres versions de Word, vous devez spécifier le fichier mso dll approprié. Par exemple, Office 2000 fournit mso9.dll et OfficeXP fournit mso.dll. Ce code est simplifié dans stdafx.h :

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

Le code suivant s’affiche dans NotSoSimple.h. Le code correspondant est indiqué par des commentaires :

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)<br/>
[ATLEventHandling, exemple](../visual-cpp-samples.md)

