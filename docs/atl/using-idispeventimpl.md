---
description: 'En savoir plus sur : utilisation de IDispEventImpl'
title: Utilisation de IDispEventImpl (ATL)
ms.date: 08/19/2019
helpviewer_keywords:
- IDispEventImpl class, using
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
ms.openlocfilehash: 4ddab52eeac3c409b32393e8b8b07a85019143c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157176"
---
# <a name="using-idispeventimpl"></a>Utilisation d’IDispEventImpl

Lorsque `IDispEventImpl` vous utilisez pour gérer des événements, vous devez :

- Dérivez votre classe de [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

- Ajoutez un mappage de récepteur d’événements à votre classe.

- Ajoutez des entrées à la table de récepteurs d’événements à l’aide de la macro [SINK_ENTRY](reference/composite-control-macros.md#sink_entry) ou [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex) .

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

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventimpl_1.h)]

Le code suivant apparaît dans NotSoSimple. h. Le code approprié est indiqué par des commentaires :

[!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/cpp/using-idispeventimpl_2.h)]

## <a name="see-also"></a>Voir aussi

[Gestion des événements](../atl/event-handling-and-atl.md)<br/>
[Exemple de ATLEventHandling](../overview/visual-cpp-samples.md)
