---
title: Options, Assistant contrôle ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 932661227daa216934c061a8b6807b05ca8270ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443756"
---
# <a name="options-atl-control-wizard"></a>Options, Assistant contrôle ATL

Insérer « Résultats de la recherche « résumé ici.

Utilisez cette page de l’Assistant pour définir le type de contrôle que vous créez et le niveau de prise en charge de l’interface qu’il contient.

## <a name="uielement-list"></a>Liste des éléments d’interface

### <a name="control-type"></a>Type de contrôle

Le type de contrôle que vous souhaitez créer.

- **Contrôle standard**: contrôle ActiveX.

- **Contrôle composite**: contrôle ActiveX qui peut contenir (semblable à une boîte de dialogue) autres contrôles ActiveX ou Windows. Un contrôle composite inclut les éléments suivants :

   - Un modèle pour la boîte de dialogue qui implémente le contrôle composite.

   - Une ressource personnalisée, REGISTRY, qui inscrit automatiquement le contrôle composite lorsqu’elle est appelée.

   - Une classe C++ qui implémente le contrôle composite.

   - Une interface COM exposée par le contrôle composite.

   - Une page de test HTML contenant le contrôle composite.

   Par défaut, ce contrôle définit [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) à true pour indiquer qu’il s’agit d’un contrôle avec fenêtres. Il implémente une table de récepteur. Pour plus d’informations, consultez [prise en charge pour le contrôle DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Contrôle DHTML**: contrôle ATL DHTML spécifie l’interface utilisateur, à l’aide de HTML. La classe UI DHTML contient un mappage COM. Par défaut, ce contrôle définit [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) à true pour indiquer qu’il s’agit d’un contrôle avec fenêtres.

   Pour plus d’informations, consultez [identification des éléments du projet de contrôle DHTML Edit](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Contrôle minimal

Prend en charge uniquement les interfaces qui sont absolument nécessaires par la plupart des conteneurs. Vous pouvez définir **contrôle Minimal** pour tous les types de contrôles : vous pouvez créer un contrôle standard minimal, un contrôle composite minimal ou un contrôle DHTML minimal.

### <a name="aggregation"></a>Agrégation

Ajoute la prise en charge de l’agrégation pour le contrôle que vous créez. Pour plus d’informations, consultez [agrégation](../../atl/aggregation.md).

- **Oui**: créer un contrôle qui peut être agrégé.

- **Ne**: créer un contrôle qui ne peut pas être agrégé.

- **Uniquement**: créer un contrôle qui ne peut être instancié par le biais d’agrégation.

### <a name="threading-model"></a>Modèle de thread

Spécifie que le modèle de thread utilisé par le contrôle.

- **Seul**: le contrôle s’exécute uniquement dans le thread COM principal.

- **Cloisonnement**: le contrôle peut être créé dans n’importe quel thread unique cloisonné. Valeur par défaut.

### <a name="interface"></a>Interface

Le type d’interface de ce contrôle expose au conteneur.

- **Double**: crée une interface qui expose les propriétés et méthodes via `IDispatch` et directement par le biais de la VTBL.

- **Custom**: crée une interface qui expose des méthodes directement par le biais d’un VTBL.

   Si vous sélectionnez **personnalisé**, vous pouvez spécifier que le contrôle est **Automation compatible**. Si vous sélectionnez **Automation compatible**, l’Assistant ajoute les [oleautomation](../../windows/oleautomation.md) attribut à l’interface dans le fichier IDL, et l’interface peut être marshalée par le marshaleur universel dans oleaut32.dll. Consultez [détails Marshaling](/windows/desktop/com/marshaling-details) dans le SDK Windows pour plus d’informations.

   En outre, si vous sélectionnez **Automation compatible**, puis tous les paramètres pour toutes les méthodes dans le contrôle doivent être de type VARIANT compatible.

### <a name="support"></a>Assistance

Définit la prise en charge de divers supplémentaire pour le contrôle.

- **Points de connexion**: Active les points de connexion pour votre objet en faisant dériver la classe de l’objet [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) et ce qui lui permet d’exposer une interface source.

- **Une licence**: ajoute la prise en charge pour le contrôle pour [licences](/windows/desktop/com/licensing). Contrôles sous licence ne peuvent être hébergés que si l’ordinateur client possède la licence appropriée.

## <a name="see-also"></a>Voir aussi

[Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md)

