---
title: CReBar et CReBarCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6133e298cd0bc5b497fbbba47982a755afeefb2e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442849"
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

