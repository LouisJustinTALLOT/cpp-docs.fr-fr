---
title: Définition des propriétés d’un accélérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5198fc1958863d3b5ad560ffeb8c5576506e9e46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888843"
---
# <a name="setting-accelerator-properties"></a>Définition des propriétés d'un accélérateur
Vous pouvez définir les propriétés d’un accélérateur dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) à tout moment. Vous pouvez également utiliser l'Éditeur d'accélérateurs pour modifier les propriétés d'un accélérateur dans la table d'accélérateurs. Les modifications apportées à l'aide de la fenêtre Propriétés ou de l'Éditeur d'accélérateurs ont le même résultat : elles sont immédiatement répercutées dans la table d'accélérateurs.  
  
 Il existe trois propriétés pour chaque raccourci [ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   Le [propriété modificateur](../windows/accelerator-modifier-property.md) définit des combinaisons de touches pour l’accélérateur de contrôle.  
  
    > [!NOTE]
    >  Dans la fenêtre Propriétés, cette propriété s'affiche sous forme de trois propriétés booléennes distinctes, qui peuvent être contrôlées indépendamment : Alt, Ctrl ou Maj.  
  
-   Le [propriété de clé](../windows/accelerator-key-property.md) définit la clé réelle à utiliser comme accélérateur.  
  
-   Le [de la propriété Type](../windows/accelerator-type-property.md) détermine si la clé est interprétée comme virtuelle (VIRTKEY) ou ASCII/ANSI.  
  

  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Touches accélérateur prédéfinies](../windows/predefined-accelerator-keys.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)   
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)