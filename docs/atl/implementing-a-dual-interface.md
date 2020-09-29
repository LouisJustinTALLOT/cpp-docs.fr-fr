---
title: Implémentation d’une interface double (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: 97d8cd912c85a74f3550a9ca6c7b87a9717d4075
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499551"
---
# <a name="implementing-a-dual-interface"></a>Implémentation d’une interface double

Vous pouvez implémenter une interface double à l’aide de la classe [IDispatchImpl](../atl/reference/idispatchimpl-class.md) , qui fournit une implémentation par défaut des `IDispatch` méthodes dans une interface double. Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Pour utiliser cette classe :

- Définissez votre interface double dans une bibliothèque de types.

- Dérivez votre classe d’une spécialisation de `IDispatchImpl` (transmettez des informations sur l’interface et la bibliothèque de types comme arguments template).

- Ajoutez une ou des entrées au mappage COM pour exposer l’interface double via `QueryInterface` .

- Implémentez la partie vtable de l’interface dans votre classe.

- Assurez-vous que la bibliothèque de types contenant la définition d’interface est disponible pour vos objets au moment de l’exécution.

## <a name="atl-simple-object-wizard"></a>Assistant Objet simple ATL

Si vous souhaitez créer une nouvelle interface et une classe pour l’implémenter, vous pouvez utiliser la [boîte de dialogue Ajouter une classe ATL](../ide/adding-a-class-visual-cpp.md#add-class-dialog-box), puis l' [Assistant objet simple ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Assistant Implémentation d'interface

Si vous disposez d’une interface existante, vous pouvez utiliser l' [Assistant Implémentation](../atl/reference/adding-a-new-interface-in-an-atl-project.md) de l’interface pour ajouter la classe de base, les entrées de mappage com et les implémentations de méthode squelette nécessaires à une classe existante.

> [!NOTE]
> Vous devrez peut-être ajuster la classe de base générée afin que les numéros de version principale et secondaire de la bibliothèque de types soient passés comme arguments template à votre `IDispatchImpl` classe de base. L’Assistant implémentation de l’interface ne vérifie pas le numéro de version de la bibliothèque de types pour vous.

## <a name="implementing-idispatch"></a>Implémentation de IDispatch

Vous pouvez utiliser une `IDispatchImpl` classe de base pour fournir une implémentation d’une dispinterface en spécifiant simplement l’entrée appropriée dans le mappage COM (à l’aide de la [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) macro) tant que vous disposez d’une bibliothèque de types décrivant une interface double correspondante. Il est assez courant d’implémenter l' `IDispatch` interface de cette manière, par exemple. L’Assistant objet simple ATL et l’Assistant Implémentation d’interface supposent que vous avez l’intention de l’implémenter `IDispatch` de cette manière, afin qu’ils ajoutent l’entrée appropriée à la carte.

> [!NOTE]
> ATL offre les classes [IDispEventImpl](../atl/reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pour vous aider à implémenter des dispinterfaces sans avoir besoin d’une bibliothèque de types contenant la définition d’une interface double compatible.

## <a name="see-also"></a>Voir aussi

[Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)
