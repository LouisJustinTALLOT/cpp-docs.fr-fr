---
description: 'En savoir plus sur : CReBar et CReBarCtrl'
title: CReBar comparé à CReBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 5a8dfe7594448319b4eb872abfb7022841d4e5dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309431"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar comparé à CReBarCtrl

MFC fournit deux classes pour créer des rebarres : [CReBar](reference/crebar-class.md) et [CReBarCtrl](reference/crebarctrl-class.md) (qui encapsulent l’API de contrôle commun Windows). `CReBar` fournit toutes les fonctionnalités du contrôle commun rebar, et gère un grand nombre des paramètres et structures de contrôle communs requis pour vous.

`CReBarCtrl` est une classe wrapper pour le contrôle rebar Win32 et, par conséquent, peut être plus facile à implémenter si vous n’envisagez pas d’intégrer le rebar dans l’architecture MFC. Si vous envisagez d’utiliser `CReBarCtrl` et d’intégrer le rebar dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations de contrôle rebar aux MFC. Cette communication n’est pas difficile. Toutefois, il s’agit d’un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CReBar` .

Visual C++ offre deux façons de tirer parti du contrôle commun Rebar.

- Créez le rebar à l’aide de `CReBar` , puis appelez [CReBar :: GetReBarCtrl](reference/crebar-class.md#getrebarctrl) pour accéder aux `CReBarCtrl` fonctions membres.

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` est une fonction membre incluse qui effectue un cast du **`this`** pointeur de l’objet Rebar. Cela signifie qu’au moment de l’exécution, l’appel de fonction n’a pas de surcharge.

- Créez le rebar à l’aide du constructeur de [CReBarCtrl](reference/crebarctrl-class.md).

L’une ou l’autre des méthodes vous donne accès aux fonctions membres du contrôle rebar. Quand vous appelez `CReBar::GetReBarCtrl` , elle retourne une référence à un `CReBarCtrl` objet afin que vous puissiez utiliser l’un ou l’autre ensemble de fonctions membres. Consultez [CReBar](reference/crebar-class.md) pour plus d’informations sur la construction et la création d’un rebar à l’aide de `CReBar` .

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](using-crebarctrl.md)<br/>
[Contrôles](controls-mfc.md)
