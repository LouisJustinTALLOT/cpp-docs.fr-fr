---
title: Implémentation d’une Interface double (ATL) | Documents Microsoft
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
ms.openlocfilehash: 34cc55e4466dba094bf70e734340b40237207f3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356730"
---
# <a name="implementing-a-dual-interface"></a>Implémentation d’une Interface double
Vous pouvez implémenter une interface double à l’aide de la [IDispatchImpl](../atl/reference/idispatchimpl-class.md) (classe), qui fournit une implémentation par défaut de la `IDispatch` méthodes dans une interface double. Pour plus d'informations, consultez [Implementing the IDispatch Interface](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
 Pour utiliser cette classe :  
  
-   Définissez votre interface double dans une bibliothèque de types.  
  
-   Dérivez votre classe d’une spécialisation de `IDispatchImpl` (passer des informations sur la bibliothèque d’interface et le type en tant que les arguments template).  
  
-   Ajouter une entrée (ou entrées) au mappage COM pour exposer l’interface double via `QueryInterface`.  
  
-   Implémentez la partie vtable de l’interface dans votre classe.  
  
-   Assurez-vous que la bibliothèque de types contenant la définition d’interface est disponible pour vos objets en cours d’exécution.  
  
## <a name="atl-simple-object-wizard"></a>Assistant Objet simple ATL  
 Si vous souhaitez créer une nouvelle interface et une nouvelle classe pour l’implémenter, vous pouvez utiliser la [boîte de dialogue Ajouter une classe ATL](../ide/add-class-dialog-box.md), puis le [Assistant objet Simple ATL](../atl/reference/atl-simple-object-wizard.md).  
  
## <a name="implement-interface-wizard"></a>Assistant Implémentation d'interface  
 Si vous avez une interface existante, vous pouvez utiliser la [Assistant Implémentation d’Interface](../atl/reference/adding-a-new-interface-in-an-atl-project.md) pour ajouter la classe de base nécessaire, les entrées de mappage COM et implémentations de méthode squelette à une classe existante.  
  
> [!NOTE]
>  Vous devrez peut-être ajuster la classe de base générée afin que les numéros de version principale et secondaire de la bibliothèque de types sont passés comme arguments de modèle à votre `IDispatchImpl` classe de base. Assistant Implémentation d’Interface ne vérifie pas le numéro de version de bibliothèque de types pour vous.  
  
## <a name="implementing-idispatch"></a>Implémentation de IDispatch  
 Vous pouvez utiliser un `IDispatchImpl` classe de base pour fournir une implémentation d’une dispinterface simplement en spécifiant l’entrée appropriée dans le mappage COM (à l’aide de la [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) ou [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) macro) tant que vous disposez d’une bibliothèque de types décrivant une interface double correspondante. Il est assez courant pour implémenter le `IDispatch` de l’interface de cette manière, par exemple. L’Assistant objet Simple ATL et l’Assistant Implémentation d’Interface à la fois supposent que vous avez l’intention d’implémenter `IDispatch` de cette manière, par conséquent, ils ajouterez l’entrée appropriée à la carte.  
  
> [!NOTE]
>  ATL offre la [IDispEventImpl](../atl/reference/idispeventimpl-class.md) et [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) classes pour vous aider à implémenter des dispinterfaces sans nécessiter une bibliothèque de types contenant la définition d’une interface double compatible.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)

