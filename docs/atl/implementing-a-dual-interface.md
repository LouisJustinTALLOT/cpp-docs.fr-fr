---
title: Mise en œuvre d’une interface double (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: a85597adad045bee3edb5cc3ed63c72a22fa08fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319468"
---
# <a name="implementing-a-dual-interface"></a>Mise en œuvre d’une interface double

Vous pouvez implémenter une double interface à l’aide de `IDispatch` la classe [IDispatchImpl,](../atl/reference/idispatchimpl-class.md) qui fournit une implémentation par défaut des méthodes dans une double interface. Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Pour utiliser cette classe :

- Définissez votre interface double dans une bibliothèque de type.

- Dérivez votre classe d’une spécialisation de `IDispatchImpl` (pass informations sur l’interface et la bibliothèque de type comme arguments de modèle).

- Ajoutez une entrée (ou des entrées) à la `QueryInterface`carte COM pour exposer la double interface par .

- Implémentez la partie vtable de l’interface de votre classe.

- Assurez-vous que la bibliothèque de type contenant la définition d’interface est disponible pour vos objets au moment de l’exécution.

## <a name="atl-simple-object-wizard"></a>Assistant Objet simple ATL

Si vous souhaitez créer une nouvelle interface et une nouvelle classe pour l’implémenter, vous pouvez utiliser la [boîte de dialogue ATL Add Class](../ide/add-class-dialog-box.md), puis le assistant [d’objet simple ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Assistant Implémentation d'interface

Si vous avez une interface existante, vous pouvez utiliser le [Implémentation de l’interface pour](../atl/reference/adding-a-new-interface-in-an-atl-project.md) ajouter la classe de base nécessaire, les entrées de carte COM et les implémentations de méthodes de squelette à une classe existante.

> [!NOTE]
> Vous devrez peut-être ajuster la classe de base générée afin que les numéros `IDispatchImpl` de version majeur et mineur de la bibliothèque de type soient transmis comme arguments de modèle à votre classe de base. Le Implémentez l’interface Wizard ne vérifie pas pour vous le numéro de version de la bibliothèque de type.

## <a name="implementing-idispatch"></a>Mise en œuvre de l’IDispatch

Vous pouvez `IDispatchImpl` utiliser une classe de base pour fournir une implémentation d’un dispinterface simplement en spécifiant l’entrée appropriée dans la carte COM (en utilisant le [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) macro) tant que vous avez une bibliothèque de type décrivant une double interface correspondante. Il est assez courant `IDispatch` d’implémenter l’interface de cette façon, par exemple. L’ATL Simple Object Wizard et Implement Interface `IDispatch` Wizard supposent tous deux que vous avez l’intention d’implémenter de cette façon, de sorte qu’ils ajouteront l’entrée appropriée à la carte.

> [!NOTE]
> ATL propose les classes [IDispEventImpl](../atl/reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pour vous aider à mettre en œuvre des dispinterfaces sans avoir besoin d’une bibliothèque de type contenant la définition d’une interface double compatible.

## <a name="see-also"></a>Voir aussi

[Double interfaces et ATL](../atl/dual-interfaces-and-atl.md)
