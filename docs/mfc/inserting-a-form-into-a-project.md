---
title: Insertion d’un formulaire dans un projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e62618301e09ad4c44fb91608976ecab972a59da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344131"
---
# <a name="inserting-a-form-into-a-project"></a>Insertion d'un formulaire dans un projet
Formulaires fournissent un conteneur pratique pour les contrôles. Vous pouvez aisément insérer un formulaire MFC dans votre application, que l’application prend en charge les bibliothèques MFC.  
  
### <a name="to-insert-a-form-into-your-project"></a>Pour insérer un formulaire dans votre projet  
  
1.  À partir de l’affichage de classes, sélectionnez le projet auquel vous souhaitez ajouter le formulaire et cliquez sur le bouton droit de la souris.  
  
2.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une classe**.  
  
     Si le **nouveau formulaire** commande n’est pas disponible, votre projet peut être basé sur la bibliothèque ATL (Active Template). Pour ajouter un formulaire à un projet ATL, vous devez [spécifier certains paramètres](../atl/reference/application-settings-atl-project-wizard.md) lors de la création du projet.  
  
3.  À partir de la **MFC** dossier, cliquez sur **classe MFC**.  
  
4.  À l’aide de l’Assistant classe MFC, vérifiez la nouvelle classe à dériver de [CFormView](../mfc/reference/cformview-class.md).  
  
 Visual C++ ajoute le formulaire à votre application, puis l’ouvre dans l’éditeur de boîte de dialogue afin que vous puissiez commencer Ajout de contrôles et l’utilisation de sa conception globale.  
  
 Voulez-vous effectuer les étapes supplémentaires suivantes (non applicables pour les applications basées sur la boîte de dialogue) :  
  
1.  Remplacer la `OnUpdate` fonction membre.  
  
2.  Implémenter une fonction membre pour déplacer des données à partir de votre vue à votre document.  
  
3.  Créer un `OnPrint` fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode formulaire](../mfc/form-views-mfc.md)

