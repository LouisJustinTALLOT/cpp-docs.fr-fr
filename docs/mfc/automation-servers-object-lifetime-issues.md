---
title: 'Serveurs Automation : problèmes liés à la durée de vie des objets'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 6e8c4189e8c895cf41323528c70d9277645d8f9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619071"
---
# <a name="automation-servers-object-lifetime-issues"></a>Serveurs Automation : problèmes liés à la durée de vie des objets

Lorsqu'un client Automation crée ou active un élément OLE, le serveur passe au client un pointeur vers cet objet. Le client établit une référence à l’objet via un appel à la fonction OLE [IUnknown :: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). Cette référence est appliquée jusqu’à ce que le client appelle [IUnknown :: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). (Les applications clientes écrites avec les classes OLE de bibliothèque MFC (Microsoft Foundation Class) n’ont pas besoin d’effectuer ces appels ; le Framework le fait.) Le système OLE et le serveur lui-même peuvent établir des références à l’objet. Un serveur ne doit pas détruire un objet tant que les références externes à l’objet restent actives.

L’infrastructure conserve un décompte interne du nombre de références à tout objet serveur dérivé de [CCmdTarget](reference/ccmdtarget-class.md). Ce nombre est mis à jour lorsqu’un client Automation ou une autre entité ajoute ou libère une référence à l’objet.

Lorsque le nombre de références devient 0, l’infrastructure appelle la fonction virtuelle [CCmdTarget :: OnFinalRelease](reference/ccmdtarget-class.md#onfinalrelease). L’implémentation par défaut de cette fonction appelle l’opérateur **Delete** pour supprimer cet objet.

La bibliothèque MFC fournit des fonctionnalités supplémentaires pour contrôler le comportement de l'application lorsque les clients externes contiennent des références aux objets de l'application. En plus de tenir le décompte des références à chaque objet, les serveurs contiennent un compte global des objets actifs. Les fonctions globales [AfxOleLockApp](reference/application-control.md#afxolelockapp) et [AfxOleUnlockApp](reference/application-control.md#afxoleunlockapp) mettent à jour le nombre d’objets actifs de l’application. Si ce nombre est différent de zéro, l'application ne se termine pas lorsque l'utilisateur sélectionne Fermer dans le menu système ou Quitter dans le menu Fichier. En revanche, la fenêtre principale de l'application est masquée (mais pas détruite) jusqu'à ce que toutes les demandes clientes en attente soient traitées. En général, `AfxOleLockApp` et `AfxOleUnlockApp` sont appelés respectivement dans les constructeurs et les destructeurs des classes qui prennent en charge Automation.

Parfois, des circonstances obligent le serveur à s'arrêter lorsqu'un client a toujours une référence à un objet. Par exemple, une ressource dont le serveur dépend, peut ne pas être disponible, ce qui cause une erreur du serveur. L'utilisateur peut également fermer un document serveur qui contient les objets auxquels d'autres applications ont des références.

Dans le SDK Windows, consultez `IUnknown::AddRef` et `IUnknown::Release` .

## <a name="see-also"></a>Voir aussi

[Serveurs Automation](automation-servers.md)<br/>
[AfxOleCanExitApp](reference/application-control.md#afxolecanexitapp)
