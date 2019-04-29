---
title: Options, Assistant Page de propriétés ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: c92c7a3f03c3ddedbea02647e2317d77a7655609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275397"
---
# <a name="options-atl-property-page-wizard"></a>Options, Assistant Page de propriétés ATL

Utilisez cette page de l’Assistant pour définir le niveau d’agrégation et le modèle de thread de page de propriétés que vous créez.

- **Modèle de thread**

   Spécifie le modèle de thread utilisé par la page de propriétés.

   Consultez [en spécifiant le modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Single**|La page de propriétés s’exécute uniquement dans le thread COM principal.|
   |**Apartment**|La page de propriétés peut être créée dans n’importe quel thread unique cloisonné. Valeur par défaut.|

- **Aggregation**

   Ajoute la prise en charge de l’agrégation de la page de propriétés que vous créez. Consultez [agrégation](../../atl/aggregation.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Oui**|Créer une page de propriétés qui peut être agrégée.|
   |**Non**|Créer une page de propriétés qui ne peut pas être agrégée.|
   |**Only**|Créer une page de propriétés qui ne peut être instanciée par le biais d’agrégation.|

## <a name="see-also"></a>Voir aussi

[Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Chaînes, Assistant Page de propriétés ATL](../../atl/reference/strings-atl-property-page-wizard.md)
