---
title: Assistant Implémentation d’interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.impl.interface.overview
dev_langs:
- C++
helpviewer_keywords:
- Implement Interface Wizard [C++]
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5d48688d271330c1cbcbac69f2e0b0c60ccbe8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713750"
---
# <a name="implement-interface-wizard"></a>Assistant Implémentation d'interface
Cet Assistant implémente une interface pour un objet COM. Les implémentations de nombreuses interfaces sont incluses dans les bibliothèques COM disponibles avec Visual Studio et Windows. Une implémentation d’interface est associée à un objet quand une instance de cet objet est créée, et elle fournit les services qu’offre l’objet.  
  
Pour en savoir plus sur les interfaces et les implémentations, consultez [Interfaces et implémentations d’interface](/windows/desktop/com/interfaces-and-interface-implementations) dans le SDK Windows.  
  
- **Implémenter une interface à partir de**

   Spécifie l’emplacement de la bibliothèque de types à partir de laquelle est créée l’interface.  
  
   |Option|Description|  
   |------------|-----------------|  
   |**Projet**|La bibliothèque de types fait partie du projet.|  
   |**Registry**|La bibliothèque de types est inscrite dans le système. Les bibliothèques de types inscrites sont répertoriées dans **Bibliothèques de types disponibles**.|  
   |**Fichier**|La bibliothèque de types n’est pas nécessairement inscrite dans le système, mais est contenue dans un fichier. Vous devez fournir l’emplacement du fichier dans **Emplacement**.|  
  
- **Bibliothèques de types disponibles**

   Affiche les bibliothèques de types disponibles contenant les définitions d’interface que vous pouvez implémenter. Quand vous cliquez sur **Fichier** sous **Implémenter une interface à partir de**, cette zone n’est pas modifiable.  
  
- **Emplacement**

   Affiche l’emplacement de la bibliothèque de types actuellement sélectionnée dans la liste **Bibliothèques de types disponibles**. Si vous avez sélectionné **Fichier** sous **Implémenter une interface à partir de**, cliquez sur le bouton de sélection pour rechercher un fichier contenant la bibliothèque de types à utiliser.  
  
- **Interfaces**

   Affiche les interfaces dont les définitions sont contenues dans la bibliothèque de types actuellement sélectionnée dans la zone **Bibliothèques de types disponibles**.  
  
   > [!NOTE]
   > Les interfaces qui ont le même nom que celles déjà implémentées par l’objet sélectionné ne sont pas affichées dans la zone **Interfaces**.  
  
   |Bouton de transfert|Description|  
   |---------------------|-----------------|  
   |**>**|Ajoute à la liste **Implémenter les interfaces** le nom d’interface actuellement sélectionné dans la liste **Interfaces**.|  
   |**>>**|Ajoute à la liste **Implémenter les interfaces** tous les noms d’interface disponibles dans la liste **Interfaces**.|  
   |**\<**|Supprime le nom d’interface actuellement sélectionné dans la liste **Implémenter les interfaces**.|  
   |**\<\<**|Supprime tous les noms d’interface actuellement répertoriés dans la liste **Implémenter les interfaces**.|  
  
- **Implémenter les interfaces**

   Affiche le nom des interfaces que vous avez choisi d’implémenter dans votre objet.  
  
   > [!NOTE]
   > Si vous incluez plusieurs interfaces qui dérivent de `IDispatch` ou si vous essayez d’implémenter une interface dérivée d’une autre interface déjà présente dans votre classe, vous devez clarifier les entrées COM_MAP. Consultez [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’une interface](../ide/implementing-an-interface-visual-cpp.md)