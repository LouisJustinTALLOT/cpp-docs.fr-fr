---
title: Options, Assistant Page de propriétés ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: a46a55cca221293e83a72bf0c2670e2343c744b0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076208"
---
# <a name="options-atl-property-page-wizard"></a>Options, Assistant Page de propriétés ATL

::: moniker range="vs-2019"

L’Assistant Page de propriétés ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=vs-2017"

Utilisez cette page de l’Assistant pour définir le modèle de thread et le niveau d’agrégation de la page de propriétés que vous créez.

- **Modèle de thread**

   Spécifie le modèle de thread utilisé par la page de propriétés.

   Consultez [Spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Unique**|La page de propriétés s’exécute uniquement dans le thread COM principal.|
   |**Apartment**|La page de propriétés peut être créée dans n’importe quel thread unique cloisonné. La valeur par défaut.|

- **Agrégation**

   Ajoute la prise en charge de l’agrégation pour la page de propriétés que vous créez. Consultez [Agrégation](../../atl/aggregation.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Oui**|Créez une page de propriétés qui peut être agrégée.|
   |**Non**|Créez une page de propriétés qui ne peut pas être agrégée.|
   |**Uniquement**|Créez une page de propriétés qui peut être uniquement instanciée via l’agrégation.|

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Chaînes, Assistant Page de propriétés ATL](../../atl/reference/strings-atl-property-page-wizard.md)
