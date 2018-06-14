---
title: Assistant Ajout d’événement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.event.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f92f871f22fb01f3f0f37677c393fcd481c08120
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325193"
---
# <a name="add-event-wizard"></a>Assistant Ajout d'événement
Cet Assistant ajoute un événement à un projet de contrôle ActiveX MFC. Vous pouvez spécifier votre propre événement, personnaliser un événement stock standard ou sélectionner un événement stock dans une liste.  
  
 **Nom de l’événement**  
 Définit le nom utilisé par les clients Automation pour demander un événement de la classe. Entrez un nom ou sélectionnez-en un dans la liste.  
  
 **Type de l’événement**  
 Indique le type d’événement à ajouter. Disponible uniquement si la sélection est effectuée dans la liste **Nom de l’événement**.  
  
|Option|Description|  
|------------|-----------------|  
|**Stock**|Spécifie qu’un événement stock, tel qu’un clic sur un bouton, est implémenté pour cette classe. Les événements stock sont définis dans la bibliothèque MFC (Microsoft Foundation Class).|  
|**Personnalisé**|Spécifie que vous définissez votre propre implémentation de l’événement.|  
  
 **Nom interne**  
 Définit le nom de la fonction membre qui envoie l’événement. Disponible uniquement pour les événements personnalisés. Le nom est basé sur le **Nom de l’événement**. Vous pouvez changer le nom interne si vous souhaitez attribuer un nom différent du **Nom de l’événement**.  
  
 **Type de paramètre**  
 Définit le type du **Nom du paramètre**. Sélectionnez le type dans la liste.  
  
 **Nom du paramètre**  
 Définit le nom d’un paramètre à passer par l’intermédiaire de votre événement. Après avoir tapé le nom, vous devez cliquer sur **Ajouter** pour l’ajouter à la liste de paramètres.  
  
 Une fois que vous cliquez sur **Ajouter**, le nom du paramètre s’affiche dans **Liste de paramètres**.  
  
> [!NOTE]
>  Si vous fournissez un nom de paramètre puis cliquez sur **Terminer** avant de cliquer sur **Ajouter**, le paramètre n’est pas ajouté à l’événement. Vous devez rechercher la méthode et insérer le paramètre manuellement. **Liste de paramètres**  
  
 **Ajouter**  
 Ajoute le paramètre que vous spécifiez dans **Nom du paramètre** et son type à **Liste de paramètres**. Vous devez cliquer sur **Ajouter** pour ajouter un paramètre à la liste.  
  
 **Supprimer**  
 Supprime le paramètre que vous sélectionnez dans **Liste de paramètres** de la liste.  
  
 **Liste de paramètres**  
 Affiche tous les paramètres et leurs types actuellement ajoutés pour la méthode. Quand vous ajoutez des paramètres, l’Assistant met à jour la **Liste de paramètres** pour afficher chaque paramètre avec son type.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un événement](../ide/adding-an-event-visual-cpp.md)