---
description: 'En savoir plus sur : options, Assistant contrôle ATL'
title: Options, Assistant contrôle ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 428f6ba1a4bee9cec60ca05b57d66d176c3f0deb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157891"
---
# <a name="options-atl-control-wizard"></a>Options, Assistant contrôle ATL

Utilisez cette page de l’Assistant pour définir le type de contrôle que vous créez et le niveau de prise en charge de l’interface qu’il contient.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

### <a name="control-type"></a>Type de contrôle

Type de contrôle que vous souhaitez créer.

- **Contrôle standard**: contrôle ActiveX.

- **Contrôle composite**: contrôle ActiveX qui peut contenir (semblable à une boîte de dialogue) d’autres contrôles ActiveX ou contrôles Windows. Un contrôle composite comprend les éléments suivants :

  - Modèle pour la boîte de dialogue qui implémente le contrôle composite.

  - Ressource personnalisée, registre, qui inscrit automatiquement le contrôle composite lorsqu’il est appelé.

  - Classe C++ qui implémente le contrôle composite.

  - Interface COM, exposée par le contrôle composite.

  - Page de test HTML contenant le contrôle composite.

    Par défaut, ce contrôle définit [CComControlBase :: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) sur true pour indiquer qu’il s’agit d’un contrôle avec fenêtres. Il implémente une table réceptrice. Pour plus d’informations, consultez [prise en charge du contrôle DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Contrôle DHTML**: un contrôle ATL DHTML spécifie l’interface utilisateur, à l’aide de html. La classe d’interface utilisateur DHTML contient une carte COM. Par défaut, ce contrôle définit [CComControlBase :: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) sur true pour indiquer qu’il s’agit d’un contrôle avec fenêtres.

   Pour plus d’informations, consultez [identification des éléments du projet de contrôle DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Contrôle minimal

Prend en charge uniquement les interfaces qui sont absolument nécessaires à la plupart des conteneurs. Vous pouvez définir un **contrôle minimal** pour tous les types de contrôle : vous pouvez créer un contrôle standard minimal, un contrôle composite minimal ou un contrôle DHTML minimal.

### <a name="aggregation"></a>Agrégation

Ajoute la prise en charge de l’agrégation pour le contrôle que vous créez. Pour plus d’informations, consultez [agrégation](../../atl/aggregation.md).

- **Oui**: créer un contrôle qui peut être agrégé.

- **Non**: créer un contrôle qui ne peut pas être agrégé.

- **Uniquement**: créer un contrôle qui peut uniquement être instancié par le biais de l’agrégation.

### <a name="threading-model"></a>Modèle de thread

Spécifie que le modèle de thread utilisé par le contrôle.

- **Unique**: le contrôle s’exécutera uniquement dans le thread com principal.

- **Apartment**: le contrôle peut être créé dans n’importe quel cloisonnement de threads unique. Valeur par défaut.

### <a name="interface"></a>Interface

Type d’interface que ce contrôle expose au conteneur.

- **Dual**: crée une interface qui expose des propriétés et des méthodes par `IDispatch` le biais de et directement par le biais du VTBL.

- **Custom**: crée une interface qui expose des méthodes directement par le biais d’un VTBL.

   Si vous sélectionnez **personnalisé**, vous pouvez spécifier que le contrôle est **compatible avec Automation**. Si vous sélectionnez **compatible Automation**, l’Assistant ajoute l’attribut [oleautomation](../../windows/attributes/oleautomation.md) à l’interface dans le IDL, et l’interface peut être marshalée par le marshaleur universel dans oleaut32.dll. Pour plus d’informations, consultez [Détails du marshaling](/windows/win32/com/marshaling-details) dans le SDK Windows.

   En outre, si vous sélectionnez **compatible Automation**, tous les paramètres de toutes les méthodes dans le contrôle doivent être compatibles variant.

### <a name="support"></a>Support

Définit une prise en charge supplémentaire pour le contrôle.

- **Points de connexion**: active les points de connexion pour votre objet en rendant la classe de votre objet dérivée de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) et en l’autorisant à exposer une interface source.

- **Sous licence**: ajoute la prise en charge du contrôle pour la gestion des [licences](/windows/win32/com/licensing). Les contrôles sous licence ne peuvent être hébergés que si la licence de l’ordinateur client est correcte.

## <a name="see-also"></a>Voir aussi

[Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md)
