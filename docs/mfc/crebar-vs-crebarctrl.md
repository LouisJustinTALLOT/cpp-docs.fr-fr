---
title: CReBar et CReBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CReBar
- CReBarCtrl
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: a1b5cda729e760246449bf197fdc9b32752b96e8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279209"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar et CReBarCtrl

MFC fournit deux classes pour créer des rebars : [CReBar](../mfc/reference/crebar-class.md) et [CReBarCtrl](../mfc/reference/crebarctrl-class.md) (qui encapsule l’API de contrôle commun de Windows). `CReBar` fournit toutes les fonctionnalités du contrôle commun rebar, et il gère la plupart des paramètres de contrôle communs requis et des structures pour vous.

`CReBarCtrl` est une classe wrapper pour le contrôle rebar Win32 et par conséquent, peut être plus facile à implémenter si vous ne souhaitez pas intégrer le rebar dans l’architecture MFC. Si vous envisagez d’utiliser `CReBarCtrl` et intégrer le rebar dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations du contrôle rebar à MFC. Cette communication n’est pas difficile ; Toutefois, il est un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CReBar`.

Visual C++ propose deux façons de tirer parti du contrôle commun rebar.

- Créez le rebar à l’aide `CReBar`, puis appelez [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) pour accéder à la `CReBarCtrl` fonctions membres.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` est une fonction membre inline qui effectue un cast de la **cela** pointeur de l’objet rebar. Cela signifie que, au moment de l’exécution, l’appel de fonction n’a aucune surcharge.

- Créez le rebar [CReBarCtrl](../mfc/reference/crebarctrl-class.md)du constructeur.

Les deux méthodes vous donnera accès aux fonctions membres du contrôle rebar. Lorsque vous appelez `CReBar::GetReBarCtrl`, elle retourne une référence à un `CReBarCtrl` afin de pouvoir utiliser un ensemble de fonctions membres de l’objet. Consultez [CReBar](../mfc/reference/crebar-class.md) pour plus d’informations sur la construction et la création d’un contrôle rebar avec `CReBar`.

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
