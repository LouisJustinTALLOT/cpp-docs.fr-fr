---
title: Utilisation d’IDispEventSimpleImpl (ATL)
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
ms.openlocfilehash: a0af775e8b6c6c5c7bad547971c08ab1b3175988
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259007"
---
# <a name="using-idispeventsimpleimpl"></a>Utilisation d’IDispEventSimpleImpl

Lorsque vous utilisez `IDispEventSimpleImpl` pour gérer les événements, vous devez :

- Dérivez votre classe de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Ajoutez une table de récepteur d’événements à votre classe.

- Définir [les structures _ATL_FUNC_INFO](../atl/reference/atl-func-info-structure.md) structures décrivant les événements.

- Ajouter des entrées à la carte de récepteur événement à l’aide du [macro SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) macro.

- Implémenter les méthodes qui vous intéresse dans la gestion des.

- Et désinformation la source d’événements.

## <a name="example"></a>Exemple

L’exemple ci-dessous vous montre comment gérer les `DocumentChange` événements déclenchement par de Word **Application** objet. Cet événement est défini en tant que méthode sur le `ApplicationEvents` dispinterface.

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

Les seules informations à partir de la bibliothèque de types réellement utilisée dans cet exemple sont le CLSID du mot `Application` objet et l’IID de le `ApplicationEvents` interface. Ces informations sont utilisées uniquement au moment de la compilation.

Le code suivant s’affiche dans Simple.h. Le code correspondant est indiqué par des commentaires :

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

Le code suivant provient de Simple.cpp :

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)<br/>
[ATLEventHandling, exemple](../visual-cpp-samples.md)
