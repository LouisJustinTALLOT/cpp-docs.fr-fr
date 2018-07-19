---
title: Implémentation d’une Interface double (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb28b1ce6d98ffd030bbeeca746847b57ed59bc9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957595"
---
# <a name="implementing-a-dual-interface"></a>Implémentation d’une Interface double
Vous pouvez implémenter une interface double à l’aide de la [IDispatchImpl](../atl/reference/idispatchimpl-class.md) (classe), qui fournit une implémentation par défaut de la `IDispatch` méthodes dans une interface double. Pour plus d’informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).  
  
 Pour utiliser cette classe :  
  
-   Définissez votre interface double dans une bibliothèque de types.  
  
-   Dérivez votre classe à partir d’une spécialisation de `IDispatchImpl` (passer des informations sur la bibliothèque d’interface et le type en tant que les arguments template).  
  
-   Ajouter une entrée (ou des entrées) au mappage COM pour exposer l’interface double via `QueryInterface`.  
  
-   Implémentez la partie vtable de l’interface dans votre classe.  
  
-   Assurez-vous que la bibliothèque de types contenant la définition d’interface est disponible pour vos objets en cours d’exécution.  
  
## <a name="atl-simple-object-wizard"></a>Assistant Objet simple ATL  
 Si vous souhaitez créer une nouvelle interface et une nouvelle classe pour l’implémenter, vous pouvez utiliser la [boîte de dialogue Ajouter une classe ATL](../ide/add-class-dialog-box.md), puis le [Assistant objet Simple ATL](../atl/reference/atl-simple-object-wizard.md).  
  
## <a name="implement-interface-wizard"></a>Assistant Implémentation d'interface  
 Si vous avez une interface existante, vous pouvez utiliser la [Assistant Implémentation d’Interface](../atl/reference/adding-a-new-interface-in-an-atl-project.md) pour ajouter la classe de base nécessaires, les entrées de mappage COM et structure des implémentations à une classe existante.  
  
> [!NOTE]
>  Vous devrez peut-être ajuster la classe de base générée afin que les numéros de version majeure et mineure de la bibliothèque de types sont passés comme arguments de modèle à votre `IDispatchImpl` classe de base. Assistant Implémentation d’Interface ne vérifie pas le numéro de version de bibliothèque de types pour vous.  
  
## <a name="implementing-idispatch"></a>Implémentation de IDispatch  
 Vous pouvez utiliser un `IDispatchImpl` classe de base pour fournir une implémentation d’une dispinterface en spécifiant l’entrée appropriée dans le mappage COM simplement (à l’aide de la [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) macro), que vous avez une bibliothèque de types décrivant une interface double correspondante. Il est assez courant d’implémenter le `IDispatch` de l’interface de cette façon, par exemple. L’Assistant objet Simple ATL et l’Assistant Implémentation d’Interface à la fois supposent que vous avez l’intention de mettre en œuvre `IDispatch` de cette façon, donc ils ajoutera l’entrée appropriée à la carte.  
  
> [!NOTE]
>  ATL offre la [IDispEventImpl](../atl/reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) classes pour vous aider à implémenter des dispinterfaces sans nécessiter une bibliothèque de types contenant la définition d’une interface double compatible.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)

