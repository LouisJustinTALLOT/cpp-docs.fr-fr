---
title: Options, Assistant Page de propriétés ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: 74cf72feedd8dc8e1186d54a8abe840195964620
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923656"
---
# <a name="options-atl-property-page-wizard"></a>Options, Assistant Page de propriétés ATL

::: moniker range="msvc-160"

L’Assistant Page de propriétés ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=msvc-150"

Utilisez cette page de l’Assistant pour définir le modèle de thread et le niveau d’agrégation de la page de propriétés que vous créez.

- **Modèle de thread**

   Spécifie le modèle de thread utilisé par la page de propriétés.

   Consultez [Spécification du modèle de thread du projet](../../atl/specifying-the-threading-model-for-a-project-atl.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Unique**|La page de propriétés s’exécute uniquement dans le thread COM principal.|
   |**STA**|La page de propriétés peut être créée dans n’importe quel thread unique cloisonné. Valeur par défaut.|

- **Agrégation**

   Ajoute la prise en charge de l’agrégation pour la page de propriétés que vous créez. Consultez [Agrégation](../../atl/aggregation.md) pour plus d’informations.

   |Option|Description|
   |------------|-----------------|
   |**Oui**|Créez une page de propriétés qui peut être agrégée.|
   |**Non**|Créez une page de propriétés qui ne peut pas être agrégée.|
   |**Ne**|Créez une page de propriétés qui peut être uniquement instanciée via l’agrégation.|

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md)<br/>
[Chaînes, Assistant Page de propriétés ATL](../../atl/reference/strings-atl-property-page-wizard.md)
