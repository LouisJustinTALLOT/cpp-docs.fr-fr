---
title: Propriété de Type d’un accélérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb1ba8f117fadab7cccb835ba8889d57bcc9f184
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856499"
---
# <a name="accelerator-type-property"></a>Type, propriété d'un accélérateur
L’accélérateur **Type** propriété détermine si la combinaison de touches de raccourci associée à l’ID de l’accélérateur est une combinaison de touches virtuelle ou une valeur de clé ASCII/ANSI :  
  
-   Si le **Type** propriété est **ASCII**, le [modificateur](../windows/accelerator-modifier-property.md) peut être qu’aucun ou Alt, ou elle peut avoir un accélérateur qui utilise la touche CTRL (spécifié en faisant précéder la clé avec un ^).  
  
-   Si le **Type** propriété **VIRTKEY**, n’importe quelle combinaison de valeurs de clé et modificateur n’est valide.  
  
    > [!NOTE]
    >  Si vous souhaitez entrer une valeur dans la table d’accélérateurs et ont la valeur soient traitées comme ASCII/ANSI, cliquez simplement sur le Type de l’écriture dans la table et sélectionnez ASCII dans la liste déroulante. Toutefois, si vous utilisez la **enfoncée suivante** commande (**modifier** menu) pour spécifier la clé, vous devez modifier le **Type** propriété de VIRTKEY en ASCII *avant* entrer le code de la clé.  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des propriétés d’un accélérateur](../windows/setting-accelerator-properties.md)   
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)