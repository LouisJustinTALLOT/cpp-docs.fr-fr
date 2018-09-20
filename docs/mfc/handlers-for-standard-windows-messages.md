---
title: Gestionnaires pour les Messages Windows Standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- afx_msg
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c74e97d8b89a72fc49f41b8c7e1bf90da2ba06c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417811"
---
# <a name="handlers-for-standard-windows-messages"></a>Gestionnaires pour les messages Windows standard

Par défaut des gestionnaires pour les messages Windows standards (**WM_**) sont prédéfinis dans la classe `CWnd`. La bibliothèque de classes base les noms de ces gestionnaires sur le nom du message. Par exemple, le gestionnaire pour le **WM_PAINT** message est déclaré dans `CWnd` en tant que :

`afx_msg void OnPaint();`

Le **afx_msg** mot clé suggère l’effet du C++ **virtuels** mot clé en caractérisant les gestionnaires des autres `CWnd` fonctions membres. Notez, toutefois, que ces fonctions ne sont pas réellement virtuelles ; elles sont plutôt implémentées dans les tables des messages. Les tables des messages dépendent uniquement des macros de préprocesseur standard, et non des extensions au langage C++. Le **afx_msg** mot clé correspond à un espace blanc après prétraitement.

Pour remplacer un gestionnaire défini dans une classe de base, il vous suffit de définir une fonction avec le même prototype dans votre classe dérivée et de créer une entrée dans la table des messages du gestionnaire. Le gestionnaire "substitue" tout gestionnaire du même nom dans n'importe laquelle des classes de base de vos classes.

Dans certains cas, le gestionnaire doit appeler le gestionnaire de remplacement dans la classe de base pour que la classe de base et Windows puissent traiter le message. L'emplacement où vous appelez le gestionnaire de classe de base dans votre substitution dépend des circonstances. Parfois vous devez appeler le gestionnaire de classe de base en premier et parfois en dernier. Parfois vous appelez le gestionnaire de classe de base de manière conditionnelle, si vous choisissez de ne pas traiter le message vous-même. Parfois vous devez appeler le gestionnaire de classe de base, puis exécuter de manière conditionnelle votre propre code gestionnaire, selon la valeur et l'état retourné par le gestionnaire de la classe de base.

> [!CAUTION]
>  Il n’est pas sécurisé de modifier les arguments passés dans un gestionnaire si vous envisagez de les transmettre à un gestionnaire de la classe de base. Par exemple, vous pouvez être tenté de modifier le *nChar* argument de la `OnChar` gestionnaire (à convertir en majuscules, par exemple). Ce comportement est suffisamment obscur, mais si vous devez obtenir cet effet, utilisez le `CWnd` fonction membre `SendMessage` à la place.

Comment déterminez-vous la méthode appropriée pour remplacer un message donné lors de la fenêtre Propriétés écrit le squelette de la fonction de gestionnaire pour un message donné, un `OnCreate` gestionnaire pour **WM_CREATE**, par exemple, il indique la forme de la fonction membre substituée recommandée. L’exemple suivant recommande le gestionnaire tout d’abord appeler le Gestionnaire de classe de base et continuer qu’à condition qu’elle ne retourne pas -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Par convention, les noms de ces gestionnaires commencent par le préfixe "On". Certains de ces gestionnaires n’occupent aucun argument, tandis que d’autres en ont plusieurs. Certains ont également un type de retour autre que **void**. Les gestionnaires par défaut pour tous les **WM_** messages sont documentées dans le *référence MFC* en tant que fonctions membres de classe `CWnd` dont les noms commencent par « On ». Les déclarations de fonction membre dans `CWnd` sont précédés de **afx_msg**.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
