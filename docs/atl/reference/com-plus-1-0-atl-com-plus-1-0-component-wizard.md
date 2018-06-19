---
title: COM + 1.0, Assistant composant ATL COM + 1.0 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a23f148fbdc611c8a11d8116b2e7dff34fc9d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358203"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Assistant Composant COM+ 1.0 ATL
Utilisez cette page de l’Assistant composant ATL COM + 1.0 pour spécifier le type d’interface et les interfaces supplémentaires à prendre en charge.  
  
 Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [composants de bureau ATL COM](../../atl/atl-com-desktop-components.md).  
  
 **Interface**  
 Indique le type d’interface que prend en charge de l’objet. Par défaut, l’objet prend en charge une interface double.  
  
|Option|Description|  
|------------|-----------------|  
|**Double**|Spécifie que l’objet prend en charge une interface double (sa table vtable a des fonctions d’interface personnalisées et liaison tardive `IDispatch` méthodes). Permet à la fois les clients COM et les contrôleurs Automation d’accéder à l’objet.|  
|**Personnalisé**|Spécifie que l’objet prend en charge une interface personnalisée (sa table vtable a des fonctions d’interface personnalisées). Une interface personnalisée peut être plus rapide qu’une interface double, en particulier les limites du processus.<br /><br /> -   **Compatible Automation** ajoute la prise en charge de l’automation à l’interface personnalisée. Pour les projets avec attributs, définit le **oleautomation** attribut dans la coclasse.|  
  
 **Pouvant**  
 Indique que les clients peuvent appeler ce composant de manière asynchrone à l’aide de files d’attente. Ajoute la macro personnalisée avec composants (TLBATTR_QUEUEABLE, 0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).  
  
 **Prise en charge**  
 Indique la prise en charge supplémentaire pour le contrôle de la gestion et l’objet d’erreur.  
  
|Option|Description|  
|------------|-----------------|  
|**ISupportErrorInfo**|Crée la prise en charge pour le [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) afin que l’objet puisse retourner des informations d’erreur au client de l’interface.|  
|**IObjectControl**|Fournit l’accès de l’objet à trois [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474) méthodes : [activer](http://msdn.microsoft.com/library/windows/desktop/ms681303), [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322), et [Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms687094).|  
|**IObjectConstruct**|Crée la prise en charge pour le [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) interface permettant de gérer le passage de paramètres à partir d’autres méthodes ou objets.|  
  
 **Transaction**  
 Indique que l’objet prend en charge les transactions. Inclut le fichier mtxattr.h dans le fichier .idl (projets sans attributs).  
  
|Option|Description|  
|------------|-----------------|  
|**Prise en charge**|Spécifie que l’objet n’est jamais la racine d’un flux de transactions en ajoutant la custom(TLBATTR_TRANS_SUPPORTED,0) de macro attribut composant dans le fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|  
|**Obligatoire**|Spécifie que l’objet peut peut-être pas la racine d’un flux de transactions en ajoutant la custom(TLBATTR_TRANS_REQUIRED,0) de macro attribut composant dans le fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|  
|**Non pris en charge**|Spécifie que l’objet exclut les transactions. Ajoute le custom(TLBATTR_TRANS_NOTSUPP,0) de macro attribut composant dans le fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|  
|**Requiert une nouvelle**|Spécifie que l’objet est toujours la racine d’un flux de transactions en ajoutant la custom(TLBATTR_TRANS_REQNEW,0) de macro attribut composant dans le fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant composant ATL COM + 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [Composant ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

