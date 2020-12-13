---
description: 'En savoir plus sur : utilisation de IDispEventSimpleImpl'
title: Utilisation de IDispEventSimpleImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: c0b3f6a0ecdcaae084d3f5d62c19745ee15ac6e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138162"
---
# <a name="using-idispeventsimpleimpl"></a>Utilisation d’IDispEventSimpleImpl

Lorsque `IDispEventSimpleImpl` vous utilisez pour gérer des événements, vous devez :

- Dérivez votre classe de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Ajoutez un mappage de récepteur d’événements à votre classe.

- Définir des structures de [_ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) décrivant les événements.

- Ajoutez des entrées à la table de récepteurs d’événements à l’aide de la macro [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) .

- Implémentez les méthodes que vous souhaitez gérer.

- Conseillez et Déconseillez la source de l’événement.

## <a name="example"></a>Exemple

L’exemple ci-dessous montre comment gérer l' `DocumentChange` événement déclenché par l’objet **application** de Word. Cet événement est défini comme une méthode sur la `ApplicationEvents` dispinterface.

L’exemple provient de l' [exemple ATLEventHandling](../overview/visual-cpp-samples.md).

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

L’exemple utilise `#import` pour générer les fichiers d’en-tête requis à partir de la bibliothèque de types Word. Si vous souhaitez utiliser cet exemple avec d’autres versions de Word, vous devez spécifier le fichier dll mso correct. Par exemple, Office 2000 fournit des mso9.dll et OfficeXP mso.dll. Ce code est simplifié de *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) :

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

Les seules informations de la bibliothèque de types réellement utilisées dans cet exemple sont le CLSID de l' `Application` objet Word et l’IID de l' `ApplicationEvents` interface. Ces informations sont utilisées uniquement au moment de la compilation.

Le code suivant apparaît dans simple. h. Le code approprié est indiqué par des commentaires :

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

Le code suivant provient de simple. cpp :

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)<br/>
[Exemple de ATLEventHandling](../overview/visual-cpp-samples.md)
