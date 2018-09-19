---
title: COM + 1.0, Assistant composant ATL COM + 1.0 | Microsoft Docs
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
ms.openlocfilehash: 471d6a273bfb4a446dbf5aba1c3b1bb31d988b24
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116098"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Assistant Composant COM+ 1.0 ATL

Utilisez cette page de l’Assistant composant ATL COM + 1.0 pour spécifier le type d’interface et les interfaces supplémentaires à prendre en charge.

Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md).

- **Interface**

   Indique le type d’interface que prend en charge de l’objet. Par défaut, l’objet prend en charge une interface double.

   |Option|Description|
   |------------|-----------------|
   |**Double**|Spécifie que l’objet prend en charge une interface double (son vtable a des fonctions d’interface personnalisées et liaison tardive `IDispatch` méthodes). Permet aux clients COM et les contrôleurs Automation pour accéder à l’objet.|
   |**Personnalisé**|Spécifie que l’objet prend en charge une interface personnalisée (son vtable a des fonctions d’interface personnalisées). Une interface personnalisée peut être plus rapide qu’une interface double, en particulier les limites du processus.<br /><br /> -   **Compatible Automation** ajoute la prise en charge automation à l’interface personnalisée. Pour les projets avec attributs, définit le **oleautomation** attribut dans la coclasse.|

- **Pouvant**

   Indique que les clients peuvent appeler ce composant de manière asynchrone à l’aide de files d’attente. Ajoute la composant attribué macro personnalisée (TLBATTR_QUEUEABLE, 0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).

- **Prise en charge**

   Indique la prise en charge supplémentaire pour le contrôle d’objet et de gestion des erreurs.

   |Option|Description|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crée la prise en charge pour le [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) interface afin que l’objet puisse retourner les informations d’erreur au client.|
   |**IObjectControl**|Fournit l’accès de votre objet aux trois [IObjectControl](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectcontrol) méthodes : [activer](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled), et [désactiver](/windows/desktop/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Crée la prise en charge pour le [IObjectConstruct](/windows/desktop/api/comsvcs/nn-comsvcs-iobjectconstruct) interface pour gérer en passant dans les paramètres à partir d’autres méthodes ou objets.|

- **Transaction**

   Indique que l’objet prend en charge les transactions. Inclut le fichier mtxattr.h dans le fichier .idl (projets sans attributs).

   |Option|Description|
   |------------|-----------------|
   |**Prise en charge**|Spécifie que l’objet n’est jamais la racine d’un flux de transactions en ajoutant la custom(TLBATTR_TRANS_SUPPORTED,0) de macro d’attribut composant au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|
   |**Obligatoire**|Spécifie que l’objet peut être la racine d’un flux de transaction en ajoutant le custom(TLBATTR_TRANS_REQUIRED,0) de macro d’attribut composant au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|
   |**Non pris en charge**|Spécifie que l’objet exclut les transactions. Ajoute le custom(TLBATTR_TRANS_NOTSUPP,0) de macro d’attribut composant au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|
   |**Requiert une nouvelle**|Spécifie que l’objet est toujours la racine d’un flux de transactions en ajoutant la custom(TLBATTR_TRANS_REQNEW,0) de macro d’attribut composant au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|

## <a name="see-also"></a>Voir aussi

[Assistant Composant COM+ 1.0 ATL](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Composant ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

