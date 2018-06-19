---
title: Ajout d’une entrée à une Table d’accélérateurs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 22f3e00c8ba6523f6cc615e4a766ad9206560b5e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855368"
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>Ajout d'une entrée dans une table d'accélérateurs
### <a name="to-add-an-entry-to-an-accelerator-table"></a>Pour ajouter une entrée à une table d'accélérateurs  
  
1.  Ouvrez la table d’accélérateurs en double-cliquant sur son icône dans [affichage des ressources](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Avec le bouton droit dans la table d’accélérateurs et choisissez **nouvel accélérateur** à partir du menu contextuel, ou cliquez sur l’entrée de la ligne vide en bas de la table.  
  
3.  Sélectionnez un [ID](id-property.md) dans la liste déroulante dans l’ID de zone ou tapez un nouvel ID dans la **ID** boîte.  
  
4.  Type de la [clé](../windows/accelerator-key-property.md) vous souhaitez utiliser comme accélérateur ou avec le bouton droit et choisissez **enfoncée suivante** dans le menu contextuel pour définir une combinaison de touches (la **enfoncée suivante** commande est également disponible à partir de la **modifier** menu).  
  
5.  Modifier la [modificateur](../windows/accelerator-modifier-property.md) et [Type](../windows/accelerator-type-property.md), si nécessaire.  
  
6.  Appuyez sur **Entrée**.  
  
    > [!NOTE]
    >  Assurez-vous que tous les accélérateurs définis sont uniques. Plusieurs combinaisons de touches peuvent être assignées au même ID sans problème. Par exemple, Ctrl + P et F8 peuvent être assignées à ID_PRINT. Toutefois, l'assignation d'une combinaison de touches à plusieurs ID ne fonctionne pas correctement. C'est le cas, par exemple, si la combinaison Ctrl + Z est assignée à ID_SPELL_CHECK et ID_THESAURUS.  
  

  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des Tables d’accélérateurs](../windows/editing-accelerator-tables.md)   
 [Éditeur d’accélérateurs](../windows/accelerator-editor.md)