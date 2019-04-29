---
title: Contrôles de liste virtuels
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 7372aca9e24a554e01f7a61f43d6170e99fe34c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358245"
---
# <a name="virtual-list-controls"></a>Contrôles de liste virtuels

Un contrôle de liste virtuelle est un contrôle list view dont le style est LVS_OWNERDATA. Ce style permet au contrôle prendre en charge un nombre d’éléments jusqu'à une **DWORD** (le nombre d’éléments par défaut s’étend uniquement à un **int**). Toutefois, le principal avantage de ce style est la possibilité uniquement un sous-ensemble d’éléments de données en mémoire à tout moment. Ainsi, la liste virtuelle contrôle view lui-même pour une utilisation avec des bases de données de grande taille où les méthodes spécifiques de l’accès aux données sont déjà en place.

> [!NOTE]
>  En plus de fournir la fonctionnalité de liste virtuelle `CListCtrl`, MFC fournit également les mêmes fonctionnalités dans le [CListView](../mfc/reference/clistview-class.md) classe.

Il existe certains problèmes de compatibilité que vous devez être conscient lors du développement de contrôles de liste virtuelle. Pour plus d’informations, consultez la section problèmes de compatibilité de la rubrique contrôles d’affichage de liste dans le SDK Windows.

## <a name="handling-the-lvngetdispinfo-notification"></a>Gestion de la Notification LVN_GETDISPINFO

Contrôles de liste virtuelle gèrent élément très peu d’informations. À l’exception de la sélection d’éléments et les informations de focus, toutes les informations de l’élément sont gérées par le propriétaire du contrôle. Informations sont demandées par l’infrastructure via un message de notification LVN_GETDISPINFO. Pour fournir les informations demandées, le propriétaire du contrôle liste virtuelle (ou le contrôle lui-même) doit gérer cette notification. Cela peut être effectuée facilement à l’aide de la fenêtre Propriétés (consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)). Le code résultant doit ressembler à l’exemple suivant (où `CMyDialog` propriétaire de l’objet de contrôle de liste virtuelle et que la boîte de dialogue gère la notification) :

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

Dans le gestionnaire pour le message de notification LVN_GETDISPINFO, vous devez vérifier pour voir quel type d’information est demandé. Les valeurs possibles sont :

- `LVIF_TEXT` Le *pszText* membre doit être renseigné.

- `LVIF_IMAGE` Le *iImage* membre doit être renseigné.

- `LVIF_INDENT` Le *iIndent* membre doit être renseigné.

- `LVIF_PARAM` Le *lParam* membre doit être renseigné. (Non présents pour sous-éléments.)

- `LVIF_STATE` Le *état* membre doit être renseigné.

Vous devez ensuite fournir les informations demandées à l’infrastructure.

L’exemple suivant (extrait à partir du corps du Gestionnaire de notification de l’objet de contrôle de liste) illustre une méthode possible en fournissant des informations pour les mémoires tampons de texte et l’image d’un élément :

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Mise en cache et contrôles Virtual List

Étant donné que ce type de contrôle de liste est destiné aux grands jeux de données, il est recommandé de mettre en cache les données d’élément demandé pour améliorer les performances de récupération. Le framework fournit un mécanisme pour contribuer à optimiser le cache en envoyant un message de notification LVN_ODCACHEHINT.

L’exemple suivant met à jour le cache avec la plage transmise à la fonction gestionnaire.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Pour plus d’informations sur la préparation et la gestion d’un cache, consultez la section Gestion du Cache de la rubrique contrôles d’affichage de liste dans le SDK Windows.

## <a name="finding-specific-items"></a>Recherche d’éléments spécifiques

Le message de notification LVN_ODFINDITEM est envoyé par le contrôle de liste virtuelle lorsqu’un élément de contrôle de liste particulière doit être trouvé. Le message de notification est envoyé lorsque le contrôle list view reçoit la touche d’accès rapide ou lorsqu’il reçoit un message LVM_FINDITEM. Les informations de recherche sont envoyées sous la forme d’un **LVFINDINFO** structure, qui est un membre de la **NMLVFINDITEM** structure. Gérer ce message en substituant le `OnChildNotify` fonction de votre liste d’objet de contrôle et à l’intérieur du corps du gestionnaire, recherchez le message LVN_ODFINDITEM. Si trouvée, effectuer l’action appropriée.

Il se peut que vous devez être prêt à rechercher un élément qui correspond aux informations données par le contrôle list view. Vous devez retourner l’index de l’élément en cas de réussite, ou -1 si aucun élément correspondant est trouvé.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
