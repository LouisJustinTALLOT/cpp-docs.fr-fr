---
title: Contrôles de liste virtuels
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375508"
---
# <a name="virtual-list-controls"></a>Contrôles de liste virtuels

Un contrôle de liste virtuel est un contrôle de vue de liste qui a le style LVS_OWNERDATA. Ce style permet au contrôle de prendre en charge un nombre d’éléments jusqu’à un **DWORD** (le nombre d’éléments par défaut ne s’étend qu’à un **int**). Cependant, le plus grand avantage fourni par ce style est la capacité d’avoir seulement un sous-ensemble d’éléments de données en mémoire à tout moment. Cela permet au contrôle de vue de liste virtuelle de se prêter pour une utilisation avec de grandes bases de données d’informations, où des méthodes spécifiques d’accès aux données sont déjà en place.

> [!NOTE]
> En plus de fournir des `CListCtrl`fonctionnalités de liste virtuelle dans , MFC fournit également les mêmes fonctionnalités dans la classe [CListView.](../mfc/reference/clistview-class.md)

Il ya quelques problèmes de compatibilité que vous devez être au courant lors du développement de contrôles de liste virtuelle. Pour plus d’informations, consultez la section Questions de Compatibilité du sujet contrôle de la liste dans le SDK Windows.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Traitement de la notification LVN_GETDISPINFO

Les contrôles de liste virtuelle conservent très peu d’informations sur les éléments. À l’exception de la sélection de l’élément et de l’information de mise au point, toutes les informations sur l’élément sont gérées par le propriétaire du contrôle. L’information est demandée par le cadre via un message de notification LVN_GETDISPINFO. Pour fournir les informations demandées, le propriétaire du contrôle de liste virtuelle (ou le contrôle lui-même) doit gérer cette notification. Cela peut facilement être fait à l’aide de [l’assistant de classe](reference/mfc-class-wizard.md) (voir [Messages de cartographie aux fonctions](../mfc/reference/mapping-messages-to-functions.md)). Le code résultant doit ressembler à l’exemple suivant (où `CMyDialog` possède l’objet de contrôle de liste virtuelle et le dialogue est le traitement de la notification):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

Dans le gestionnaire du message de notification LVN_GETDISPINFO, vous devez vérifier quel type d’information est demandé. Les valeurs possibles sont les suivantes :

- `LVIF_TEXT`Le membre *pszText* doit être rempli.

- `LVIF_IMAGE`Le membre *iImage* doit être rempli.

- `LVIF_INDENT`Le membre *iIndent* doit être rempli.

- `LVIF_PARAM`Le membre *lParam* doit être rempli. (Non présent pour les sous-éléments.)

- `LVIF_STATE`Le membre *de l’État* doit être comblé.

Vous devez ensuite fournir toutes les informations demandées dans le cadre.

L’exemple suivant (tiré du corps du gestionnaire de notification pour l’objet de commande de liste) démontre une méthode possible en fournissant des informations pour les tampons de texte et l’image d’un élément :

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Contrôles de la liste de cachage et de liste virtuelle

Étant donné que ce type de contrôle de liste est destiné aux grands ensembles de données, il est recommandé de mettre en cache les données de l’élément demandé pour améliorer les performances de récupération. Le cadre fournit un mécanisme de cache-indice pour aider à optimiser le cache en envoyant un message de notification LVN_ODCACHEHINT.

L’exemple suivant met à jour le cache avec la plage passée à la fonction de gestionnaire.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Pour plus d’informations sur la préparation et la maintenance d’un cache, consultez la section Gestion cache du sujet Contrôle List-View dans le SDK Windows.

## <a name="finding-specific-items"></a>Trouver des éléments spécifiques

Le message de notification LVN_ODFINDITEM est envoyé par le contrôle de liste virtuel lorsqu’un élément de contrôle de liste particulier doit être trouvé. Le message de notification est envoyé lorsque le contrôle de vue de liste reçoit un accès rapide aux clés ou lorsqu’il reçoit un message LVM_FINDITEM. Les informations de recherche sont envoyées sous la forme d’une structure **LVFINDINFO,** qui est membre de la structure **NMLVFINDITEM.** Manipulez ce message `OnChildNotify` en remplaçant la fonction de votre objet de contrôle de liste et à l’intérieur du corps du gestionnaire, vérifiez le message LVN_ODFINDITEM. Si vous êtes trouvé, effectuez les mesures appropriées.

Vous devez être prêt à rechercher un élément qui correspond aux informations données par le contrôle de vue de liste. Vous devez retourner l’index de l’article en cas de succès, ou -1 si aucun élément correspondant n’est trouvé.

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
