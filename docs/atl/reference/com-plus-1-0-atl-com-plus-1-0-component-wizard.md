---
title: COM+ 1.0, Assistant Composant COM+ 1.0 ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.mts.options
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
ms.openlocfilehash: 83b7beafe537f6b271b254d16505b515a41acf27
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496691"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, Assistant Composant COM+ 1.0 ATL

::: moniker range="vs-2019"

Cet Assistant n’est pas disponible dans Visual Studio 2019 et ultérieur.

::: moniker-end

::: moniker range="<=vs-2017"

Utilisez cette page de l’Assistant Composant ATL COM+ 1.0 pour spécifier le type d’interface et les interfaces supplémentaires à prendre en charge.

Pour plus d’informations sur les projets ATL et les classes ATL COM, consultez [Composants ATL COM Desktop](../../atl/atl-com-desktop-components.md).

- **Interface**

   Indique le type d’interface pris en charge par l’objet. Par défaut, l’objet prend en charge une interface double.

   |Option|Description|
   |------------|-----------------|
   |**Double**|Spécifie que l’objet prend en charge une interface double (sa vtable comprend des fonctions d’interface personnalisées et des méthodes `IDispatch` à liaison tardive). Permet aux clients COM et aux contrôleurs Automation d’accéder à l’objet.|
   |**Personnalisée**|Spécifie que l’objet prend en charge une interface personnalisée (sa vtable comprend des fonctions d’interface personnalisées). Une interface personnalisée peut être plus rapide qu’une interface double, en particulier entre les frontières de processus.<br /><br /> - **Compatible Automation** ajoute la prise en charge de l’automation à l’interface personnalisée. Pour les projets avec attributs, définit l’attribut **oleautomation** dans la coclasse.|

- **Queueable**

   Indique que les clients peuvent appeler ce composant de manière asynchrone à l’aide de files d’attente. Ajoute l’attribut de composant macro personnalisé (TLBATTR_QUEUEABLE,0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).

- **Support**

   Indique une prise en charge supplémentaire pour la gestion des erreurs et le contrôle des objets.

   |Option|Description|
   |------------|-----------------|
   |**ISupportErrorInfo**|Crée une prise en charge pour l’interface [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) afin que l’objet puisse retourner les informations d’erreur au client.|
   |**IObjectControl**|Fournit à votre objet l’accès aux trois méthodes [IObjectControl](/windows/win32/api/comsvcs/nn-comsvcs-iobjectcontrol) : [Activate](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-activate), [CanBePooled](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-canbepooled) et [Deactivate](/windows/win32/api/comsvcs/nf-comsvcs-iobjectcontrol-deactivate).|
   |**IObjectConstruct**|Crée une prise en charge pour l’interface [IObjectConstruct](/windows/win32/api/comsvcs/nn-comsvcs-iobjectconstruct) afin de gérer le passage des paramètres à partir d’autres méthodes ou objets.|

- **Transaction**

   Indique que l’objet prend en charge les transactions. Inclut le fichier mtxattr.h dans le fichier .idl (projets sans attributs).

   |Option|Description|
   |------------|-----------------|
   |**Prise en charge**|Spécifie que l’objet n’est jamais la racine d’un flux de transactions, par l’ajout de l’attribut de composant macro personnalisé (TLBATTR_TRANS_SUPPORTED,0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|
   |**Obligatoire**|Spécifie que l’objet peut ou non être la racine d’un flux de transactions, par l’ajout de l’attribut de composant macro personnalisé (TLBATTR_TRANS_REQUIRED,0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|
   |**Non pris en charge**|Spécifie que l’objet exclut les transactions. Ajoute l’attribut de composant macro personnalisé (TLBATTR_TRANS_NOTSUPP,0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|
   |**Nouvelle transaction requise**|Spécifie que l’objet est toujours la racine d’un flux de transactions, par l’ajout de l’attribut de composant macro personnalisé (TLBATTR_TRANS_REQNEW,0) au fichier .h (projets attribués) ou au fichier .idl (projets sans attributs).|

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Assistant Composant COM+ 1.0 ATL](../../atl/reference/atl-com-plus-1-0-component-wizard.md)<br/>
[Composant ATL COM+ 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
