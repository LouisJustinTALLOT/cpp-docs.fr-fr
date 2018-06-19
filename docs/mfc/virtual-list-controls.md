---
title: Contrôles de liste virtuels | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b580e455aab7ff95beb85c02b8e3ca79dfa8a46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384190"
---
# <a name="virtual-list-controls"></a>Contrôles de liste virtuels
Un contrôle de liste virtuelle est un contrôle list view qui a le **est LVS_OWNERDATA** style. Ce style permet au contrôle prendre en charge d’un nombre d’éléments jusqu'à une `DWORD` (le nombre d’éléments par défaut s’étend uniquement à un `int`). Toutefois, le principal avantage de ce style est la possibilité d’avoir uniquement un sous-ensemble d’éléments de données en mémoire à tout moment. Ainsi, la liste virtuelle contrôle view lui-même pour une utilisation avec des bases de données de grande taille où les méthodes spécifiques de l’accès aux données sont déjà en place.  
  
> [!NOTE]
>  En plus de fournir la fonctionnalité de liste virtuelle `CListCtrl`, MFC fournit également les mêmes fonctionnalités dans le [CListView](../mfc/reference/clistview-class.md) classe.  
  
 Il existe certains problèmes de compatibilité que vous devez être conscient lors du développement de contrôles de liste virtuelle. Pour plus d’informations, consultez la section problèmes de compatibilité de la rubrique List-View Controls dans le Kit de développement logiciel Windows.  
  
## <a name="handling-the-lvngetdispinfo-notification"></a>Gestion de la Notification LVN_GETDISPINFO  
 Mettre à jour les contrôles de liste virtuels élément très peu d’informations. À l’exception de la sélection d’éléments et les informations de focus, toutes les informations de l’élément sont gérées par le propriétaire du contrôle. Informations sont demandées par l’infrastructure via un **LVN_GETDISPINFO** message de notification. Pour fournir les informations demandées, le propriétaire du contrôle de liste virtuelle (ou le contrôle lui-même) doit gérer cette notification. Cela peut être effectuée facilement à l’aide de la fenêtre Propriétés (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)). Le code résultant doit ressembler à l’exemple suivant (où `CMyDialog` propriétaire de l’objet de contrôle de liste virtuelle et que la boîte de dialogue gère la notification) :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]  
  
 Dans le gestionnaire pour le **LVN_GETDISPINFO** message de notification, vous devez vérifier pour voir quel type d’information est demandé. Les valeurs possibles sont :  
  
-   `LVIF_TEXT` Le `pszText` membre doit être renseigné.  
  
-   `LVIF_IMAGE` Le `iImage` membre doit être renseigné.  
  
-   **LVIF_INDENT** le *iIndent* membre doit être renseigné.  
  
-   `LVIF_PARAM` Le *lParam* membre doit être renseigné. (Ne présente pas de sous-éléments.)  
  
-   `LVIF_STATE` Le *état* membre doit être renseigné.  
  
 Vous devez ensuite fournir les informations demandées sur l’infrastructure.  
  
 L’exemple suivant (extrait du corps du Gestionnaire de notification pour l’objet contrôle list) illustre une méthode possible en fournissant des informations pour les mémoires tampons de texte et une image d’un élément :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]  
  
## <a name="caching-and-virtual-list-controls"></a>Contrôles de liste de mise en cache et virtuel  
 Étant donné que ce type de contrôle de liste est destiné aux jeux de données volumineux, il est recommandé de mettre en cache les données d’élément demandé pour améliorer les performances de récupération. Le framework fournit un mécanisme pour contribuer à optimiser le cache en envoyant un **LVN_ODCACHEHINT** message de notification.  
  
 L’exemple suivant met à jour le cache de la plage passée à la fonction gestionnaire.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]  
  
 Pour plus d’informations sur la préparation et la gestion d’un cache, consultez la section de gestion du Cache de la rubrique List-View Controls dans le Kit de développement logiciel Windows.  
  
## <a name="finding-specific-items"></a>Recherche d’éléments spécifiques  
 Le **LVN_ODFINDITEM** message de notification est envoyé par le contrôle de liste virtuels lorsqu’un élément de contrôle de liste particulier doit être trouvé. Le message de notification est envoyé lorsque le contrôle list view reçoit de touche d’accès rapide ou lorsqu’il reçoit un **LVM_FINDITEM** message. Les informations de recherche sont envoyées sous la forme d’un **LVFINDINFO** structure, qui est un membre de la **NMLVFINDITEM** structure. Gérer ce message en substituant la `OnChildNotify` fonction de votre liste d’objet de contrôle et dans le corps du gestionnaire, recherchez le **LVN_ODFINDITEM** message. Si trouvé, exécutez l’action appropriée.  
  
 Il se peut que vous devez être prêt à rechercher un élément qui correspond aux informations fournies par le contrôle list view. Vous devez retourner l’index de l’élément en cas de réussite, ou -1 si aucun élément correspondant n’est trouvé.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CListCtrl](../mfc/using-clistctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

