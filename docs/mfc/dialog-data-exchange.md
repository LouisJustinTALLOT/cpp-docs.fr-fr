---
description: 'En savoir plus sur : échange de données de boîtes de dialogue'
title: Échange de données de boîtes de dialogue
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: 7ed592e8e6a452d4c6958c3c5f7b573c1be7fe07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261474"
---
# <a name="dialog-data-exchange"></a>Échange de données de boîtes de dialogue

Si vous utilisez le mécanisme DDX, définissez les valeurs initiales des variables membres de l'objet de boîte de dialogue, en général dans votre gestionnaire `OnInitDialog` ou le constructeur de boîte de dialogue. Juste avant que la boîte de dialogue ne s’affiche, le mécanisme DDX de l’infrastructure transfère les valeurs des variables membres vers les contrôles de la boîte de dialogue, où ils apparaissent quand la boîte de dialogue elle-même s’affiche en réponse à `DoModal` ou `Create` . L'implémentation par défaut de `OnInitDialog` dans `CDialog` appelle la fonction membre `UpdateData` de la classe `CWnd` pour initialiser les contrôles dans la boîte de dialogue.

Le même mécanisme transfère les valeurs des contrôles vers les variables membres lorsque l’utilisateur clique sur le bouton OK (ou à chaque fois que vous appelez la `UpdateData` fonction membre avec l’argument **true**). Le mécanisme de validation des données de boîte de dialogue valide tous les éléments de données pour lesquels vous avez spécifiés les règles de validation.

L'illustration suivante montre l'échange de données de boîte de dialogue.

![Échange de données de la boîte de dialogue](../mfc/media/vc379d1.gif "Échange de données de la boîte de dialogue") <br/>
Échange de données de boîtes de dialogue

`UpdateData` fonctionne dans les deux sens, comme spécifié par le paramètre **bool** qui lui est passé. Pour effectuer l'échange, `UpdateData` génère un objet `CDataExchange` et appelle la fonction membre `CDialog` de la substitution de votre classe de boîte de dialogue `DoDataExchange`. `DoDataExchange` accepte un argument de type `CDataExchange`. L'objet `CDataExchange` passé à `UpdateData` représente le contexte de l'échange, et définit des informations telles que la direction de l'échange.

Lorsque vous (ou un Assistant Code) remplacez `DoDataExchange`, vous spécifiez un appel à une fonction DDX par données membres (contrôle). Chaque fonction DDX sait échanger des données dans les deux directions selon le contexte fourni par l’argument `CDataExchange` passé à votre `DoDataExchange` par `UpdateData`.

MFC fournit de nombreuses fonctions DDX pour différents types d'échange. L'exemple suivant illustre la substitution de `DoDataExchange` dans laquelle deux fonctions DDX et une fonction DDV sont appelées :

[!code-cpp[NVC_MFCControlLadenDialog#49](codesnippet/cpp/dialog-data-exchange_1.cpp)]

Les lignes `DDX_` et `DDV_` sont une table de données. Les exemples de fonctions DDX et DDV affichés concernent respectivement un contrôle de case à cocher et un contrôle de zone d'édition.

Si l’utilisateur annule une boîte de dialogue modale, la `OnCancel` fonction membre met fin à la boîte de dialogue et `DoModal` retourne la valeur **IDCANCEL**. Dans ce cas, aucune donnée n'est échangée entre la boîte de dialogue et l'objet dialogue.

## <a name="see-also"></a>Voir aussi

[Échange et validation des données de boîte de dialogue](dialog-data-exchange-and-validation.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)<br/>
[Validation des données de boîte de dialogue](dialog-data-validation.md)
