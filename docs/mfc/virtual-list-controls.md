---
title: Contrôles de liste virtuels
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 12200697af90a3c83fea3df676bd4d2488598d45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215918"
---
# <a name="virtual-list-controls"></a>Contrôles de liste virtuels

Un contrôle de liste virtuelle est un contrôle d’affichage de liste qui a le style LVS_OWNERDATA. Ce style permet au contrôle de prendre en charge un nombre d’éléments allant jusqu’à une **valeur DWORD** (le nombre d’éléments par défaut s’étend uniquement à un **`int`** ). Toutefois, le plus grand avantage fourni par ce style est la possibilité de disposer d’un sous-ensemble d’éléments de données en mémoire à un moment donné. Cela permet au contrôle de vue de liste virtuelle de se prêter à une utilisation avec de grandes bases de données d’informations, où des méthodes spécifiques d’accès aux données sont déjà en place.

> [!NOTE]
> En plus de fournir des fonctionnalités de liste virtuelle dans `CListCtrl` , MFC fournit également la même fonctionnalité dans la classe [CListView](../mfc/reference/clistview-class.md) .

Il existe certains problèmes de compatibilité que vous devez connaître lors du développement de contrôles de liste virtuels. Pour plus d’informations, consultez la section problèmes de compatibilité de la rubrique contrôles de liste dans le SDK Windows.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Gestion de la notification de LVN_GETDISPINFO

Les contrôles de liste virtuelle maintiennent très peu d’informations sur les éléments. À l’exception des informations de sélection d’élément et de focus, toutes les informations sur les éléments sont gérées par le propriétaire du contrôle. Les informations sont demandées par l’infrastructure par le biais d’un message de notification LVN_GETDISPINFO. Pour fournir les informations demandées, le propriétaire du contrôle de liste virtuelle (ou le contrôle lui-même) doit gérer cette notification. Cela peut être fait facilement à l’aide de l' [Assistant classe](reference/mfc-class-wizard.md) (consultez [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)). Le code obtenu doit ressembler à l’exemple suivant (où `CMyDialog` est le propriétaire de l’objet de contrôle de liste virtuel et la boîte de dialogue gère la notification) :

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

Dans le gestionnaire du message de notification LVN_GETDISPINFO, vous devez vérifier le type d’informations demandées. Les valeurs possibles sont les suivantes :

- `LVIF_TEXT`Le membre *pszText* doit être renseigné.

- `LVIF_IMAGE`Le membre *IImage* doit être renseigné.

- `LVIF_INDENT`Le membre *iIndent* doit être renseigné.

- `LVIF_PARAM`Le membre *lParam* doit être rempli. (Non présent pour les sous-éléments.)

- `LVIF_STATE`Le membre d' *État* doit être rempli.

Vous devez ensuite fournir toutes les informations demandées à l’infrastructure.

L’exemple suivant (extrait du corps du gestionnaire de notification pour l’objet de contrôle de liste) illustre une méthode possible en fournissant des informations pour les mémoires tampons de texte et l’image d’un élément :

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Mise en cache et contrôles de liste virtuels

Étant donné que ce type de contrôle de liste est destiné aux jeux de données volumineux, il est recommandé de mettre en cache les données d’élément demandées pour améliorer les performances de récupération. Le Framework fournit un mécanisme d’affinage du cache pour faciliter l’optimisation du cache en envoyant un message de notification LVN_ODCACHEHINT.

L’exemple suivant met à jour le cache avec la plage passée à la fonction de gestionnaire.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Pour plus d’informations sur la préparation et la maintenance d’un cache, consultez la section gestion du cache de la rubrique contrôles de liste dans le SDK Windows.

## <a name="finding-specific-items"></a>Recherche d’éléments spécifiques

Le message de notification LVN_ODFINDITEM est envoyé par le contrôle de liste virtuel lorsqu’un élément de contrôle de liste particulier doit être trouvé. Le message de notification est envoyé lorsque le contrôle List View reçoit un accès à la clé rapide ou lorsqu’il reçoit un message de LVM_FINDITEM. Les informations de recherche sont envoyées sous la forme d’une structure **LVFINDINFO** , qui est membre de la structure **NMLVFINDITEM** . Gérez ce message en remplaçant la `OnChildNotify` fonction de votre objet de contrôle de liste et dans le corps du gestionnaire, recherchez le message de LVN_ODFINDITEM. S’il est trouvé, effectuez l’action appropriée.

Vous devez être prêt à rechercher un élément qui correspond aux informations fournies par le contrôle List View. Vous devez retourner l’index de l’élément en cas de réussite, ou-1 si aucun élément correspondant n’est trouvé.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
