---
title: Options, Assistant contrôle ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 25db3995687011de5e9cc0a98506cd26f2f1af0b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495453"
---
# <a name="options-atl-control-wizard"></a>Options, Assistant contrôle ATL

Utilisez cette page de l’Assistant pour définir le type de contrôle que vous créez et le niveau de prise en charge de l’interface qu’il contient.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

### <a name="control-type"></a>Type de contrôle

Type de contrôle que vous souhaitez créer.

- **Contrôle standard**: Contrôle ActiveX.

- **Contrôle composite**: Contrôle ActiveX qui peut contenir (semblable à une boîte de dialogue) d’autres contrôles ActiveX ou contrôles Windows. Un contrôle composite comprend les éléments suivants:

  - Modèle pour la boîte de dialogue qui implémente le contrôle composite.

  - Ressource personnalisée, registre, qui inscrit automatiquement le contrôle composite lorsqu’il est appelé.

  - C++ Classe qui implémente le contrôle composite.

  - Interface COM, exposée par le contrôle composite.

  - Page de test HTML contenant le contrôle composite.

    Par défaut, ce contrôle définit [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) sur true pour indiquer qu’il s’agit d’un contrôle avec fenêtres. Il implémente une table réceptrice. Pour plus d’informations, consultez [prise en charge du contrôle DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Contrôle DHTML**: Un contrôle ATL DHTML spécifie l’interface utilisateur, à l’aide de HTML. La classe d’interface utilisateur DHTML contient une carte COM. Par défaut, ce contrôle définit [CComControlBase:: m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) sur true pour indiquer qu’il s’agit d’un contrôle avec fenêtres.

   Pour plus d’informations, consultez [identification des éléments du projet de contrôle DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Contrôle minimal

Prend en charge uniquement les interfaces qui sont absolument nécessaires à la plupart des conteneurs. Vous pouvez définir un **contrôle minimal** pour tous les types de contrôle: vous pouvez créer un contrôle standard minimal, un contrôle composite minimal ou un contrôle DHTML minimal.

### <a name="aggregation"></a>Agrégation

Ajoute la prise en charge de l’agrégation pour le contrôle que vous créez. Pour plus d’informations, consultez [agrégation](../../atl/aggregation.md).

- **Oui**: Créez un contrôle qui peut être agrégé.

- **Non**: Créez un contrôle qui ne peut pas être agrégé.

- **Uniquement**: Créez un contrôle qui peut uniquement être instancié par le biais de l’agrégation.

### <a name="threading-model"></a>Modèle de thread

Spécifie que le modèle de thread utilisé par le contrôle.

- **Unique**: Le contrôle s’exécutera uniquement dans le thread COM principal.

- **Cloisonnement**: Le contrôle peut être créé dans n’importe quel cloisonnement de thread unique. Valeur par défaut.

### <a name="interface"></a>Interface

Type d’interface que ce contrôle expose au conteneur.

- **Double**: Crée une interface qui expose des propriétés et des `IDispatch` méthodes par le biais de et directement par le biais du VTBL.

- **Personnalisé** : Crée une interface qui expose des méthodes directement par le biais d’un VTBL.

   Si vous sélectionnez **personnalisé**, vous pouvez spécifier que le contrôle est **compatible avec Automation**. Si vous sélectionnez **compatible Automation**, l’Assistant ajoute l’attribut [oleautomation](../../windows/oleautomation.md) à l’interface dans le fichier IDL, et l’interface peut être marshalée par le marshaleur universel dans Oleaut32. dll. Pour plus d’informations, consultez [Détails](/windows/win32/com/marshaling-details) du marshaling dans le SDK Windows.

   En outre, si vous sélectionnez **compatible Automation**, tous les paramètres de toutes les méthodes dans le contrôle doivent être compatibles variant.

### <a name="support"></a>Assistance

Définit une prise en charge supplémentaire pour le contrôle.

- **Points de connexion**: Active les points de connexion pour votre objet en faisant en sorte que la classe de votre objet dérive de [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) et en l’autorisant à exposer une interface source.

- **Sous licence**: Ajoute la prise en charge du contrôle pour la gestion des [licences](/windows/win32/com/licensing). Les contrôles sous licence ne peuvent être hébergés que si la licence de l’ordinateur client est correcte.

## <a name="see-also"></a>Voir aussi

[Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md)
